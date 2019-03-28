
[Maximal-square - leetcode.com ](https://leetcode.com/problems/maximal-square/)

- Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

<details><summary>Java</summary>
    
- <details><summary>Solution</summary>

    ```java
    public class MaximalSquare {

        /**
         *  return number of 1s in array (a) starting at index (s)
         */
        public static int horizontal1s(char[] a, int s) {
            int count = 0;
            for (int i=s; i < a.length && a[i] != '0'; i++) {
                count += 1;
            }
            return count;
        }

        /**
         * count horizontal 1s
         *  -> return max h1s for a square starting at ir, ic
         *
         * - initial: count first row of 1s -> h1s
         * - termination: if h1s and row count equal or
         *      - array out of bounds or
         *      - starting char of current row '0'
         *      - return Min(h1s, rows checked)
         * - step: count next row of 1s
        **/
        public static int maxH1sForSquareStartingAt(char[][] m, int ir, int ic) {
            int h1s = horizontal1s(m[ir], ic), r = ir+1;

            for (; r < m.length && (r-ir) < h1s && m[r][ic] != '0'; r++) {
                h1s = Math.min(h1s, horizontal1s(m[r], ic));
            }
            return (h1s > (r-ir)) ? r-ir : h1s;
        }

        /**
         * return area of max square of 1s in matrix
         *
         * - initial: h1s = 0
         * - termination: if
         *      - array is out of bounds or
         *      - h1s < numCols - c  or
         *      - h1s < numRows -r
         *  - step:
         *      - h1s = max(h1s, maxH1sForSquareStartingAt(m, r, c)
         *      - increment column index (c) otherwise increment row index (r) and set c = 0
         *
         * @param {char[][]} matrix
         * @return {number}
         **/
        public static int maximalSquare(char[][] m) {
            if (m.length == 0) {
                return 0;
            }
            int h1s = 0, numCols = m[0].length, numRows = m.length;
            for (int r=0; r < numRows && h1s < numRows - r; r++) {
                for (int c=0; c < numCols && h1s < numCols - c; c++) {
                    h1s = Math.max(h1s, maxH1sForSquareStartingAt(m,r,c));
                }
            }
            return h1s*h1s;
        }
    }
    ```

    </details>

- <details><summary>Tests</summary>

    ```java
    import org.junit.Test;

    import static org.junit.Assert.*;

    public class MaximalSquareTest {

        @org.junit.Test
        public void horizontal1s() {
            char[] a = {'1'};
            assertEquals(MaximalSquare.horizontal1s(a, 0), 1);
            a = new char[]{'1','1'};
            assertEquals(MaximalSquare.horizontal1s(a, 0), 2);
            a = new char[]{'0','1','1'};
            assertEquals(MaximalSquare.horizontal1s(a, 0), 0);
            a = new char[]{'0','1','1'};
            assertEquals(MaximalSquare.horizontal1s(a, 1), 2);
            a = new char[]{'0','1','1','1','0'};
            assertEquals(MaximalSquare.horizontal1s(a, 1), 3);
        }

        @Test
        public void maxH1sForSquareStartingAt() {
            char[][] m = new char[][]{
                    {'1','1','1','1','1','1','1','1'},
                    {'1','1','1','1','1','1','1','0'},
                    {'1','1','1','1','1','1','1','0'},
                    {'1','1','1','1','1','0','0','0'},
                    {'0','1','1','1','1','0','0','0'}};
            assertEquals(4, MaximalSquare.maxH1sForSquareStartingAt(m,0,0));
            assertEquals(4, MaximalSquare.maxH1sForSquareStartingAt(m,0,1));
        }

        @org.junit.Test
        public void maximalSquare() {
            char[][] m;
            m = new char[][]{
                    {'1'}
            };
            assertEquals(MaximalSquare.maximalSquare(m), 1);
            m = new char[][]{
                    {'0'}
            };
            assertEquals(MaximalSquare.maximalSquare(m), 0);
            m = new char[][]{
                    {'0', '1'}
            };
            assertEquals(MaximalSquare.maximalSquare(m), 1);
            m = new char[][]{
                    {'0', '1', '1'},
                    {'0', '1', '1'}
            };
            assertEquals(MaximalSquare.maximalSquare(m), 4);
            m = new char[][]{
                    {'1','0','1','0','0'},
                    {'1','0','1','1','1'},
                    {'1','1','1','1','1'},
                    {'1','0','0','1','0'}};
            assertEquals(MaximalSquare.maximalSquare(m), 4);
            m = new char[][]{
                    {'1','1','1','1','1','1','1','1'},
                    {'1','1','1','1','1','1','1','0'},
                    {'1','1','1','1','1','1','1','0'},
                    {'1','1','1','1','1','0','0','0'},
                    {'0','1','1','1','1','0','0','0'}};
            assertEquals(16, MaximalSquare.maximalSquare(m));
            m = new char[][]{
            };
            assertEquals(MaximalSquare.maximalSquare(m), 0);
            m = new char[][]{
                    {'0','0','0','0','0'},
                    {'1','0','0','0','0'},
                    {'0','0','0','0','0'},
                    {'0','0','0','0','0'}
            };
            assertEquals(1, MaximalSquare.maximalSquare(m));
        }

    }
    ```
    </details>

</details>

<details><summary>Scala</summary>
    
- <details><summary>Solution</summary>

    ```scala
    class MaximalSquare {

        def horizontal1s(a: Array[Char], s: Int): Int = {
          if (s >= a.length || a(s) == '0') return 0
          horizontal1s(a, s+1) + 1
        }

        def maxH1sForSquareStartingAt (m: Array[Array[Char]], ir: Int, ic: Int):Int = {
          var h1s = horizontal1s(m(ir), ic)
          val r = ir + 1

          def maxH1sForSquareStartingAt (r: Int, c: Int):Int = {
            var rp = r - ir // rows processed
            if (r >= m.length || rp >= h1s || m(r)(ic) == '0') {
              if (h1s > rp) return rp else return h1s
            }
            h1s = Math.min(h1s, horizontal1s(m(r), ic))
            maxH1sForSquareStartingAt(r+1, ic)
          }

          maxH1sForSquareStartingAt(ir+1, ic)
        }

        def maximalSquare(m: Array[Array[Char]]): Int = {
          if (m.length == 0) return 0
          var h1s = 0
          val numCols = m(0).length
          val numRows = m.length

          def maximalSquare(r: Int, c: Int): Int = {
            if (r >= numRows || h1s >= numRows - r) return h1s*h1s
            if (c >= numCols || h1s >= numCols - c) return maximalSquare(r+1, 0)
            h1s = Math.max(h1s, maxH1sForSquareStartingAt(m, r, c))
            maximalSquare(r, c+1)
          }

          maximalSquare(0, 0)
        }

    }
    ```

    </details>

- <details><summary>Tests</summary>

    ```scala
    import org.scalatest.FunSuite

    class MaximalSquareTest extends FunSuite {

      test("horizontal1s") {
        assertResult(0)(new MaximalSquare().horizontal1s(Array(),0))
        assertResult(1)(new MaximalSquare().horizontal1s(Array('1'),0))
        assertResult(2)(new MaximalSquare().horizontal1s(Array('1', '1'),0))
        assertResult(0)(new MaximalSquare().horizontal1s(Array('0', '1', '1'),0))
        assertResult(2)(new MaximalSquare().horizontal1s(Array('0', '1', '1'),1))
        assertResult(3)(new MaximalSquare().horizontal1s(Array('0', '1', '1', '1', '0'),1))
      }

      test("maxH1sForSquareStartingAt") {
        val m = Array[Array[Char]](
          Array('1', '1', '1', '1', '1', '1', '1', '1'),
          Array('1', '1', '1', '1', '1', '1', '1', '0'),
          Array('1', '1', '1', '1', '1', '1', '1', '0'),
          Array('1', '1', '1', '1', '1', '0', '0', '0'),
          Array('0', '1', '1', '1', '1', '0', '0', '0'))
        assertResult(4)(new MaximalSquare().maxH1sForSquareStartingAt(m, 0, 0))
        assertResult(4)(new MaximalSquare().maxH1sForSquareStartingAt(m, 0, 1))
      }

      test("testMaximalSquare") {
        var m: Array[Array[Char]] = null
        m = Array[Array[Char]](
          Array('1'))
        assertResult(1)(new MaximalSquare().maximalSquare(m))
        m = Array[Array[Char]](
          Array('0'))
        assertResult(0)(new MaximalSquare().maximalSquare(m))
        m = Array[Array[Char]](
          Array('0', '1'))
        assertResult(1)(new MaximalSquare().maximalSquare(m))
        m = Array[Array[Char]](
          Array('0', '1', '1'),
          Array('0', '1', '1'))
        assertResult(4)(new MaximalSquare().maximalSquare(m))
        m = Array[Array[Char]](
          Array('1', '0', '1', '0', '0'),
          Array('1', '0', '1', '1', '1'),
          Array('1', '1', '1', '1', '1'),
          Array('1', '0', '0', '1', '0'))
        assertResult(4)(new MaximalSquare().maximalSquare(m))

        m = Array[Array[Char]](
          Array('1', '1', '1', '1', '1', '1', '1', '1'),
          Array('1', '1', '1', '1', '1', '1', '1', '0'),
          Array('1', '1', '1', '1', '1', '1', '1', '0'),
          Array('1', '1', '1', '1', '1', '0', '0', '0'),
          Array('0', '1', '1', '1', '1', '0', '0', '0'))
        assertResult(16)(new MaximalSquare().maximalSquare(m))

        m = Array[Array[Char]]()
        assertResult(0)(new MaximalSquare().maximalSquare(m))

        m = Array[Array[Char]](
          Array('0', '0', '0', '0', '0'),
          Array('1', '0', '0', '0', '0'),
          Array('0', '0', '0', '0', '0'),
          Array('0', '0', '0', '0', '0'))
        assertResult(1)(new MaximalSquare().maximalSquare(m))

      }

    }
    ```
    </details>

</details>

<details><summary>References</summary>

</details>

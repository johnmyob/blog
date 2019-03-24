## Scala HakerRank exercises

<details><sammary>Staircase - right aligned</summary>

- [Staircase - right aligned](https://www.hackerrank.com/challenges/staircase/problem?h_r=next-challenge&h_v=legacy)
- Consider a staircase of size :

```
   #
  ##
 ###
####
```

```scala
object Solution {
    
    def counts(a:Array[Int]): (Int, Int, Int) = {
        def counts(i:Int, pos:Int, neg:Int, zero:Int): (Int, Int, Int) =
            if (i >= a.length)
                (pos,neg,zero)
            else if (a(i) < 0)
                counts(i+1, pos, neg+1, zero)
            else if (a(i) > 0)
                counts(i+1, pos+1, neg, zero)
            else
                counts(i+1, pos, neg, zero+1)
                
        counts(0, 0, 0, 0)
    }
    
    def main(args: Array[String]) {
        val sc = new java.util.Scanner (System.in);
        var n = sc.nextInt();
        var arr = new Array[Int](n);
        for(arr_i <- 0 to n-1) {
           arr(arr_i) = sc.nextInt();
        }
        val (pos, neg, zero) = counts(arr)
        var dn : Double = n
        //println(pos/dn + "\n" + neg/dn + "\n" + zero/dn) 
        printf("%.6f\n%.6f\n%.6f\n", pos/dn, neg/dn, zero/dn)         
    }
}
```

</details>

[Reverse-words-in-a-string - leetcode.com ](https://leetcode.com/problems/reverse-words-in-a-string/)

- Given an input string, reverse the string word by word.

<details><summary>JavaScript</summary>

```javascript
const reverseWords = (s) =>
    s.trim().replace(/\s\s+/g, ' ').split(" ").reverse().join(" ");
```
</details>

<details><summary>Java</summary>

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

class Solution {
    public String reverseWords(String s) {
        String[] sArray = s.trim().replaceAll("\\s\\s+", " ").split(" ");

        List<String> list = Arrays.asList(sArray);
        Collections.reverse(list);
        
        return String.join(" ", (String[])list.toArray());
    }
}
```
</details>

<details><summary>Scala</summary>

```scala
object Solution {
    def reverseWords(s: String): String = {
      s.trim().split("\\s+").reverse.mkString(" ")  
    }
}
```
</details>

<details><summary>References</summary>

- [Regular expressions in Java - Tutorial](https://www.vogella.com/tutorials/JavaRegularExpressions/article.html)
- [java.lang.String trim()](http://javatutorialhq.com/java/lang/string-class-tutorial/trim-method-example/)
- [Split a String in Java](https://www.baeldung.com/java-split-string)
- [Java – How to convert Array to Stream](https://www.mkyong.com/java8/java-how-to-convert-array-to-stream/)
- [How to Invert an Array in Java](https://www.baeldung.com/java-invert-array)
- [Java String join() with examples](https://www.geeksforgeeks.org/java-string-join-examples/)

</details>

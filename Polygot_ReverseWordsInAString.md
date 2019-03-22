[Reverse-words-in-a-string - leetcode.com ](https://leetcode.com/problems/reverse-words-in-a-string/)

- Given an input string, reverse the string word by word.

<details><summary>JavaScript</summary>

```javascript
const reverseWords = (s) =>
    // s.trim().replace(/\s\s+/g, ' ').split(" ").reverse().join(" ");
    s.trim().split(/\s+/).reverse().join(" "); // more memory 34.8MB compared to 34.2MB
```
</details>

<details><summary>Java - collections</summary>

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

class Solution {
    public String reverseWords(String s) {
        String[] sArray = s.trim().split("\\s+"); // less code, but 8ms compared to 6ms for complete solution

        List<String> list = Arrays.asList(sArray);
        Collections.reverse(list);
        
        return String.join(" ", (String[])list.toArray());
    }
}
```
</details>

<details><summary>Java - streams</summary>

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

//T ime Submitted  Status  Runtime Memory  Language
// a few seconds ago	Accepted	47 ms	39.3 MB	java
class Solution {
    public String reverseWords(String s) {
        String[] arr = s.trim().split("\\s+");

        return IntStream.rangeClosed(1, arr.length).mapToObj(i -> arr[arr.length - i])
                .collect(Collectors.joining(" "));
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

<details><summary>Kotlin - refactored</summary>

```kotlin
class Solution {
    fun reverseWords(s: String) = s.trim().split("\\s+".toRegex())
        .asReversed().joinToString(separator = " ");
}
```
</details>

<details><summary>Kotlin - first Attempt</summary>

```kotlin
class Solution {
    fun reverseWords(s: String): String {
        return s.trim()
            .split("\\s+".toRegex()).asReversed()
            .joinToString(separator = " ");
    }
}
```
</details>

<details><summary>Java - first Attempt</summary>

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

<details><summary>References</summary>

- [Regular expressions in Java - Tutorial](https://www.vogella.com/tutorials/JavaRegularExpressions/article.html)
- [java.lang.String trim()](http://javatutorialhq.com/java/lang/string-class-tutorial/trim-method-example/)
- [Split a String in Java](https://www.baeldung.com/java-split-string)
- [Java – How to convert Array to Stream](https://www.mkyong.com/java8/java-how-to-convert-array-to-stream/)
- [How to Invert an Array in Java](https://www.baeldung.com/java-invert-array)
- [Java String join() with examples](https://www.geeksforgeeks.org/java-string-join-examples/)
- [Scala: How to extract parts of a string that match a regex](https://alvinalexander.com/scala/how-to-extract-parts-strings-match-regular-expression-regex-scala)

</details>

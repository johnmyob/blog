[Two-Sum - leetcode.com ](https://leetcode.com/problems/two-sum/)

- Given an array of integers, return indices of the two numbers such that they add up to a specific target.

- You may assume that each input would have exactly one solution, and you may not use the same element twice.

<details><summary>Scala</summary>

```scala
object Solution { // comment
    def twoSum(nums: Array[Int], target: Int): Array[Int] = {
        for (i <- 0 to nums.length - 1) {
            for (j <- 0 to nums.length - 1) {
                if (i != j && nums(i) + nums(j) == target) {
                    return Array(i,j)   
                }
            }
        }
        return Array(0,0)
    }
}
```
</details>

<details><summary>JavaScript</summary>

```javascript
var twoSum = function(nums, target) { // comment
    for (let i=0; i < nums.length; i++) {
        for (let j=0; j < nums.length; j++) {
            if (i != j && nums[i] + nums[j] == target) {
                return [i,j]  
            }
        }
    }
    return [0,0]
};
```
</details>

<details><summary>Kotlin</summary>

```java
class Solution { // comment
    fun twoSum(nums: IntArray, target: Int): IntArray {
        for (i in 0 until nums.size) {
            for (j in 0 until nums.size) {
                if (i != j && nums[i] + nums[j] == target) {
                    return intArrayOf(i,j)  
                }
            }
        }
        return intArrayOf(0,0) 
    }
}
```
</details>

<details><summary>Java</summary>

```java
class Solution { // comment
    public int[] twoSum(int[] nums, int target) {
        for (int i=0; i < nums.length; i++) {
            for (int j=0; j < nums.length; j++) {
                if (i != j && nums[i] + nums[j] == target) {
                    return new int[]{i,j};
                }
            }
        }
        return new int[]{};
    }
}
```
</details>

<details><summary>Python</summary>

```python
class Solution(object): # comment
    def twoSum(self, nums, target):
        for i in range(0, len(nums)):
            for j in range(0, len(nums)):
                if (i != j and nums[i] + nums[j] == target):
                    return [i,j]
        return []
```
</details>

<details><summary>C#</summary>

```csharp
public class Solution { // Comment
    public int[] TwoSum(int[] nums, int target) {
        for (int i=0; i < nums.Count(); i++) {
            for (int j=0; j < nums.Count(); j++) {
                if (i != j && nums[i] + nums[j] == target) {
                    return new int[]{i,j};
                }
            }
        }
        return new int[]{};
    }
}
```
</details>

<details><summary>Ruby</summary>

```ruby
def two_sum(nums, target)
    for i in 0..nums.length-1
        for j in 0..nums.length-1
            if i != j && nums[i] + nums[j] == target
                return [i,j]
            end
        end
    end
    return []
end
```
</details>


<details><summary>References</summary>

- [How to loop with indexes in Python](https://treyhunner.com/2016/04/how-to-loop-with-indexes-in-python/)

</details>


# Java Script

<details><summary>Arrays slice, splice and the spread operator</summary>

- Immutable slice and spread operator.

    ```javascript
    > let a = [1, 2, 3, 4, 5]
    > a
    (5) [1, 2, 3, 4, 5]
    > [...a.slice(0,3), 4.5, a[a.length-1]]
    (5) [1, 2, 3, 4.5, 5]
    > a
    (5) [1, 2, 3, 4, 5]
    ```

- Mutable splice
  - a.splice(a.length-1, 0, 4.5) is the same as:
  - same as a.splice(-1, 0, 4.5)
  - Insert 4.5 one before the last element in the array:

    ```javascript
    > a
    (5) [1, 2, 3, 4, 5]
    > a.splice(a.length-1, 0, 4.5)
    []
    > a
    (6) [1, 2, 3, 4, 4.5, 5]
    ```
</details>

<details><summary>JavaScript the Weird Parts</summary>
    
  - [Equality comparisons and sameness](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness)
    
  - [Operator precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)
  
  ```javascript
  console.log(3 + 4 * 5); // 3 + 20
// expected output: 23

console.log(4 * 3 ** 2); // 4 * 9
// expected output: 36

var a;
var b;

console.log(a = b = 5);
// expected output: 5;
  ```

</details>

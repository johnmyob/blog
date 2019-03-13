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
    > a.splice(a.length-1, 0, 4.5)
    []
    > a
    (6) [1, 2, 3, 4, 4.5, 5]
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

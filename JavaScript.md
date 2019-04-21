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
  
  ```javascript
    // using coersion and no coersion together
    const a = [undefined, null, false, 0, ""];
    a.forEach((v, i) => {
      if (v || v === 0) {
        console.log(`${v} at index ${i} is a value`);
      }
    });
  ```
  
  - Deep Object comparison
    - [online testing of any npm module](https://npm.runkit.com/npm)
  
  ```javascript
 var _ = require("lodash")
const one = {
  fruit: '🥝',
  nutrients: {
    energy: '255kJ',
    minerals: {
      name: 'calcium'
    }
  },
  daysOfWeek: [1,2,3],
};

const two = {
  fruit: '🥝',
  nutrients: {
    energy: '255kJ',
    minerals: {
      name: 'calcium'
    }
  },
  daysOfWeek: [1,2,3],
};

const three = {
  daysOfWeek: [1,2,3],
  fruit: '🥝',
  nutrients: {
    energy: '255kJ',
    minerals: {
      name: 'calcium'
    }
  },
};

// Using JavaScript
JSON.stringify(one) === JSON.stringify(two); // true
console.log(`JSON.stringify(one) === JSON.stringify(two): ${JSON.stringify(one) === JSON.stringify(two)}`);

// Using Lodash
_.isEqual(one, two); // true
console.log(`_.isEqual(one, two): ${_.isEqual(one, two)}`);

// Using JavaScript
JSON.stringify(three) === JSON.stringify(two); // true
console.log(`JSON.stringify(three) === JSON.stringify(two): ${JSON.stringify(three) === JSON.stringify(two)}`);

// Using Lodash
_.isEqual(three, two); // true
console.log(`_.isEqual(one, two): ${_.isEqual(three, two)}`);
  ```

</details>

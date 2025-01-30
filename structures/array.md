# Array

Array is a data structure used to store an ordered collection of elements. The elements in an array can be of any type: numbers, strings, objects, functions or other arrays. In JavaScript arrays are objects, making them flexible.

## Properties

- **Dynamic Size:** automatically resize when elements are added or removed.
- **Indexed Elements:** elements are stored by index, starting at `0`.
- **Different Types:** can store elements of different types.

## Best Practices

- Use array literals insted of the `Array` constructor to create arrays.
- Avoid creating sparse arrays for large datasets or perfomance-critical tasks.
- Utilize built-in methods like `filter`, `map` and `reduce` for searching and manipulating arrays.
- Remember that `sort` and `reverse` modify the original array.

## Example Code

### Creating

- Using `literal` syntax:
  ```js
  const arr = [1, 2, 3, 4];
  ```
- Using `constructor` syntax:
  ```js
  const arr1 = new Array(4);
  const arr2 = new Array(1, 2, 3, 4);
  console.log("Arr1:", arr1); // Output: [undefined, undefined, undefined, undefined]
  console.log("Arr2:", arr2); // Output: [1, 2, 3, 4]
  ```

### Common Methods

#### Adding

- `push()` — adds element(s) to the end.
  ```js
  const arr = [1, 2, 3];
  arr.push(4);
  console.log("Arr:", arr); // Output: [1, 2, 3, 4]
  ```
- `unshift()` — adds element(s) to the beginning.
  ```js
  const arr = [2, 3, 4];
  arr.unshift(1);
  console.log("Arr:", arr); // Output: [1, 2, 3, 4]
  ```

#### Removing

- `pop()` — removes the last element.
  ```js
  const arr = [1, 2, 3, 4];
  const last = arr.pop();
  console.log("Arr:", arr); // Output: [1, 2, 3]
  console.log("Last:", last); // Output: 4
  ```
- `shift()` — removes the first element.
  ```js
  const arr = [1, 2, 3, 4];
  const first = arr.shift();
  console.log("Arr:", arr); // Output: [2, 3, 4]
  console.log("First:", first); // Output: 1
  ```

#### Iteration

- `forEach()` — executes a function for each element.
  ```js
  const arr = [1, 2, 3, 4];
  arr.forEach((value) => console.log(value)); // Output: 1, 2, 3, 4
  ```
- `map()` — creates a new array by applying a function for each element.
  ```js
  const arr = [1, 2, 3, 4];
  const doubled = arr.map((value) => value * 2);
  console.log("Doubled:", doubled); // Output: [2, 4, 6, 8]
  ```

#### Searching and Filtering

- `indexOf()` — returns the index of the first occurrence of an element or `-1`.
  ```js
  const arr = [1, 2, 3, 4];
  console.log("Index of 4:", arr.indexOf(4)); // Output: 3
  console.log("Index of 5:", arr.indexOf(5)); // Output: -1
  ```
- `includes()` — checks if an element exists.
  ```js
  const arr = [1, 2, 3, 4];
  console.log("Include 4:", arr.includes(4)); // Output: true
  console.log("Include 5:", arr.includes(5)); // Output: false
  ```
- `find()` — return the first element that satisfies a condition.
  ```js
  const arr = [1, 2, 3, 4];
  console.log(
    "Find 4:",
    arr.find((value) => value > 3)
  ); // Output: 4
  console.log(
    "Find 5:",
    arr.find((value) => value > 4)
  ); // Output: undefined
  ```
- `filter()` — returns a new array with elements that pass a test condition.
  ```js
  const arr = [1, 2, 3, 4];
  console.log(
    "Filter >2:",
    arr.filter((value) => value > 2)
  ); // Output: [3, 4]
  console.log(
    "Filter >4:",
    arr.filter((value) => value > 4)
  ); // Output: []
  ```

#### Sorting and Reversing

- `sort()` — sorts elements.
  ```js
  const arr = [4, 3, 2, 1];
  console.log("Sort:", arr.sort()); // Output: [1, 2, 3, 4]
  ```
- `reverse()` — reverse the array.
  ```js
  const arr = [1, 2, 3, 4];
  console.log("Reverse:", arr.reverse()); // Output: [4, 3, 2, 1]
  ```

#### Combining and Spliting

- `concat()` — combines arrays.
  ```js
  console.log("Concat:", [1, 2].concat([3, 4])); // Output: [1, 2, 3, 4]
  ```
- `join()` — joins array elements into a string.
  ```js
  console.log("Join:", [1, 2, 3, 4].join(", ")); // Output: "1, 2, 3, 4"
  ```

### Multidimensional Arrays

Arrays in JavaScript can contain other arrays, allowing for the creation of multidimensional structures:

```js
const matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];
console.log("Matrix [1][2]:", matrix[1][2]); // Output: 6
```

### Sparce Arrays

Arrays with "missing" indices:

```js
const sparse = [];
sparse[9] = true;
console.log("Length:", sparse.length); // Output: 10
console.log("First element:", sparse[0]); // Output: undefined
console.log("Tenth element:", sparse[9]); // Output: true
```

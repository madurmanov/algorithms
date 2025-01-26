# LinearSearch

Linear Search is a simple algorithm that performs a sequeantial checking of all elements in a data structure.

## Actions

1. Start from the first element of the data structure.
2. Compare the current element with the target value.
3. If the element matches the target, return its index or the element.
4. If the current element doesn't match, move to the next element.
5. Continue until the element is found or the end of the data structure is reached.
6. If the element isn't found, return an indicator of absence.

## Complexity

- **Best Case: Ω(1)** — the element is found at the first position.
- **Average Case: Θ(n)** — the element is located somewhere in the middle.
- **Worst Case: O(n)** — the element is at the end of the data structure or not present.
- **Memory: O(1)** — no additional memory is required.

## Advantages

1. **Simple Implementation:** the algorithm is extremely simple and intuitive.
2. **No Data Requirements:** works with unsorted data.
3. **Supports Multiple Data Structures:** can be used with arrays, lists and other linear data structures.
4. **Low Memory Overhead:** memory complexity is O(1), as only one variable is used for iteration.

## Disadvantages

1. **Slow on Large Datasets:** linear iteration through all elements makes it inefficient for large data structures.
2. **No Optimization:** even if the target element is absent, the entire array must be checked.
3. **Inefficiency for Frequent Searches:** execution time grows linearly with data size.

## Use Cases

1. **Small Datasets:** works well for small data structures where the overhead of more complex algorithms is unnecessary.
2. **Unsorted Data:** when the data is unsorted and sorting isn't feasible.
3. **One-Time Operations:** for a one-off search where optimization isn't a priority.
4. **Simple Data Structures:** suitable for data structures where implementing advanced algorithms is challenging.

## Example Code

```js
function linearSearch(arr, target) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === target) {
      return i;
    }
  }
  return -1;
}

const numbers = [2, 4, 6, 8];
console.log("Numbers:", numbers);
console.log("Search 8:", linearSearch(numbers, 8)); // Output: 3
console.log("Search 9:", linearSearch(numbers, 9)); // Output: -1

const strings = ["apple", "orange", "banana", "cherry"];
console.log("Strings:", strings);
console.log("Search banana:", linearSearch(strings, "banana")); // Output: 2
console.log("Search mango:", linearSearch(strings, "mango")); // Output: -1
```

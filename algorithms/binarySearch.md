# Binary Search

Binary Search is an efficient searching algorithm used to find an element in a sorted array.

# Actions

1. Set two pointers: low (pointing to the start of the array) and high (pointing to the end).
2. Calculate the middle.
3. Compare the target value with the middle element.
   - If equal, return the index.
   - If smaller, update high point (search in the left half).
   - If larger, update low point (search in the right half).
4. Continue until low <= high.
5. If the element isn't found, return an indicator of absence.

## Complexity

- **Best Case: Ω(1)** — if the target value is at the middle.
- **Average Case: Θ(logn)** — the array is halved at each iteration.
- **Worst Case: O(logn)** — the element is at the end of the array or not present.
- **Memory: O(1)** — no additional memory is required.

## Advantages

- **Efficient for Large Arrays:** performs much faster than Linear Search on sorted arrays.

## Disadvantages

- **Requires Sorted Data:** the array must be sorted, which mine incur additional preprocessing time.
- **Not Ideal for Dynamic Arrays:** frequent modifications to the array require repeated sorting.

## Use Cases

- **Search in Static Data:** finding numbers, string or objects in sorted arrays.
- **Databases:** utilized in search systems and database indexing.
- **Library Implementations:** commonly used in methods of standard libraries (e.g. Array.prototype.includes for sorted arrays).

## Example Code

```js
function binarySearch(arr, target) {
  let low = 0;
  let high = arr.length - 1;

  while (low <= high) {
    let mid = Math.floor((low + high) / 2);

    if (arr[mid] === target) {
      return mid;
    } else if (arr[mid] < target) {
      low = mid + 1;
    } else {
      hight = mid - 1;
    }
  }

  return -1;
}

const numbers = [1, 3, 5, 7, 9, 11, 13, 15];
console.log("Numbers:", numbers);
console.log("Search 7:", binarySearch(numbers, 7)); // Output: 3
console.log("Search 8:", binarySearch(numbers, 8)); // Output: -1

const strings = ["apple", "banana", "cherry", "orange"];
console.log("Strings:", strings);
console.log("Search cherry:", binarySearch(strings, "cherry")); // Output: 2
console.log("Search mango:", binarySearch(strings, "mango")); // Output: -1
```

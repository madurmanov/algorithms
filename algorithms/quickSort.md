# Quick Sort

Quick Sort is a divide and conquer algorithm that splits an array into two halves by pivot and recursively sorts each half.

## Actions

1. Choose a pivot element from the array (commonly the first, last, middle, or a random element).
2. Rearrange the array so that all elements less than the pivot are placed to its left, and all elements greater than or equal to the pivot are placed to its right. After partitioning, the pivot is in its final sorted position.
3. Recursively apply Quick Sort to the subarrays formed by the elements to the left and right of the pivot.
4. No explicit merging is required because the subarrays are already arranged in order.

## Complexity

- **Best Case: Ω(nlogn)** — when the pivot divides the array into two nearly equal halves.
- **Average Case: Θ(nlogn)** — on average, the pivot results in balanced partitions.
- **Worst Case: O(n^2)** — when the pivot is consistently the smallest or largest element (for example, in an already sorted array with a poor pivot choice).
- **Memory: O(logn)** — due to the recursion stack in the best/average case; worst-case space complexity can be O(n).

## Advantages

- **Efficient for Large Datasets:** performs efficiently on large arrays when the pivot is chosen wisely.
- **In-Place Sorting:** many implementations sort the array in-place, requiring only minimal extra memory (mainly for the recursion stack).

## Disadvantages

- **Worst-Case Performance:** worst-case time complexity is O(n²), which may occur with poor pivot selection.
- **Unstable Sort:** the relative order of equal elements might not be preserved.
- **Recursive Overhead:** deep recursion may lead to stack overflow in environments with limited stack space, especially for large arrays.

## Use Cases

- **Large Datasets:** useful for large datasets.
- **General Purpose Sorting:** widely used in libraries and frameworks due to its practical performance.
- **Memory-Constrained Systems:** suitable when minimal extra memory allocation is required, as it sorts in-place.

## Example Code

```js
function quickSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }

  const pivot = arr[arr.length - 1];
  const left = [];
  const right = [];

  for (let i = 0; i < arr.length - 1; i++) {
    if (arr[i] < pivot) {
      left.push(arr[i]);
    } else {
      right.push(arr[i]);
    }
  }

  return [...quickSort(left), pivot, ...quickSort(right)];
}

const numbers = [8, 6, 4, 2];
console.log("Numbers:", numbers);
console.log("Sorted numbers:", quickSort(numbers)); // Output: [2, 4, 6, 8]

const strings = ["cherry", "banana", "orange", "apple"];
console.log("Strings:", strings);
console.log("Sorted strings:", quickSort(strings)); // Output: ["apple", "orange", "banana", "cherry"]
```

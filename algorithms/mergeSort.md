# Merge Sort

Merse Sort is a divide and conquer algorithm that splits an array into two halves, recursively sorts each half and then merges the sorted halves into one sorted array.

## Actions

1. . Split the input array into two halves until each subarray contains a single element.
2. . Apply merge sort recursively to each half.
3. . Merge the two sorted subarrays by comparing their elements and building a new sorted array.

## Complexity

- **Best Case: Ω(nlogn)** — even if the array is already sorted, the algorithm always divides and merges the array.
- **Average Case: Θ(nlogn)** — the array is divided and merged in logarithmic levels, with linear work on each level.
- **Worst Case: O(nlogn)** — regardless of the input order, the same division and merging process is performed.
- **Memory: O(n)** — additional memory is required to store the temporary arrays during the merge process.

## Advantages

- **Stable Sort:** relative order of equal elements.
- **Consistent Performance:** always runs in O(nlogn) time, regardless of the initial order of the elements.
- **Good for Linked Lists:** can be efficiently implemented for linked lists since the merge operation can be done without extra array space.

## Disadvantages

- **Extra Space Requirement:** the standard implementation requires O(n) extra space, which might be an issue for very large datasets.
- **Not In-Place:** because it requires extra memory for merging, it is not an in-place sorting algorithm.
- **Complex Implementation:** the merging process can be more complex compared to simpler algorithms like Insertion Sort for small datasets.

## Use Cases

- **Large Datasets:** useful for large datasets.
- **Stable Sorting Needs:** applicable when stability of the sort is required.
- **External Sorting:** often used in external sorting where the data is too large to fit in memory.

## Example Code

```js
function mergeSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }

  const mid = Math.floor(arr.length / 2);
  const left = arr.slice(0, mid);
  const right = arr.slice(mid);

  return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
  let result = [];
  let i = 0;
  let j = 0;

  while (i < left.length && j < right.length) {
    if (left[i] <= right[j]) {
      result.push(left[i]);
      i++;
    } else {
      result.push(right[j]);
      j++;
    }
  }

  return result.concat(left.slice(i)).concat(right.slice(j));
}

const numbers = [8, 6, 4, 2];
console.log("Numbers:", numbers);
console.log("Sorted numbers:", mergeSort(numbers)); // Output: [2, 4, 6, 8]

const strings = ["cherry", "banana", "orange", "apple"];
console.log("Strings:", strings);
console.log("Sorted strings:", mergeSort(strings)); // Output: ["apple", "orange", "banana", "cherry"]
```

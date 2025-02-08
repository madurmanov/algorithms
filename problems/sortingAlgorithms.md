# Sorting Algorithms

```js
/**
 * QuickSort algorithm to sort an array of numbers.
 *
 * @param {number[]} arr - The array to be sorted.
 * @return {number[]} - The sorted array.
 */
function quickSort(arr) {
  // Base case: if the array has 0 or 1 element, it's already sorted.
  if (arr.length <= 1) {
    return arr;
  }

  // Choose the pivot element. Here, we use the middle element as the pivot.
  const pivotIndex = Math.floor(arr.length / 2);
  const pivot = arr[pivotIndex];

  // Arrays to hold elements less than and greater than the pivot.
  const left = [];
  const right = [];

  // Partition the array into left and right arrays, excluding the pivot.
  for (let i = 0; i < arr.length; i++) {
    if (i === pivotIndex) continue; // Skip the pivot element itself

    if (arr[i] < pivot) {
      left.push(arr[i]);
    } else {
      right.push(arr[i]);
    }
  }

  // Recursively sort the left and right arrays, then concatenate them with the pivot in between.
  return [...quickSort(left), pivot, ...quickSort(right)];
}

const unsortedArray = [5, 3, 8, 4, 2, 7, 1, 10];
const sortedArray = quickSort(unsortedArray);
console.log("Sorted Array:", sortedArray); // Output: [1, 2, 3, 4, 5, 7, 8, 10]
```

## Explanation

1. **Base Case:** if the array has 0 or 1 element, it is already sorted, so we return it immediately.
2. **Choosing Pivot:** we choose the pivot as the middle element of the array. The pivot is used as a reference to partition the array.
3. **Partitioning Array:** we iterate through the array and compare each element (except the pivot) with the pivot:
   - Elements less than the pivot are pushed into the `left` array.
   - Elements greater than or equal to the pivot are pushed into the `right` array.
4. **Recursive Sorting:** the `quickSort` function is called recursively on both the `left` and `right` arrays to sort them.
5. **Concatenation:** the sorted array is formed by concatenating the sorted left array, the pivot, and the sorted right array.

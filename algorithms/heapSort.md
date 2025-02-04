# Heap Sort

Heap Sort is a sorting algorithm based on the heap data structure.

## Actions

1. Convert the array into a max-heap, where every parent node is greater than or equal to its child nodes.
2. Swap the first element (the maximum) with the last element in the array.
3. Reduce the heap size by one (excluding the last element, which is now in its final sorted position).
4. Apply the "heapify" procedure to the root to restore the heap property for the remaining array.
5. Repeat step 2, 3, 4 until the heap size is 1. The array is then completely sorted.

## Complexity

- **Best Case: Ω(nlogn)** — even when the array is already in order, building the heap and re-heapifying require O(nlogn) operations.
- **Average Case: Θ(nlogn)** — on average, the algorithm performs O(nlogn) comparisons and swaps.
- **Worst Case: O(nlogn)** — regardless of input order, the same division and merging process is performed.
- **Memory: O(1)** — no additional memory is required.

## Advantages

- **In-Place Sorting:** the algorithm sorts the data without requiring extra memory allocation.
- **Consistent Performance:** always runs in O(n log n) time in all cases.
- **No Worst-Case Degradation:** unlike Quick Sort, Heap Sort does not degrade to O(n^2) in the worst case.
- **Efficient for Large Datasets:** performs efficiently on large arrays when the pivot is chosen wisely.

## Disadvantages

- **Complex Implementation:** the algorithm is more complex to implement compared to simpler methods like Insertion Sort.
- **Unstable Sort:** the relative order of equal elements may not be preserved.
- **Poor Locality of Reference:** due to the nature of the heap structure, it might not fully utilize the cache memory, leading to slower practical performance on some systems.

## Use Cases

- **Large Datasets:** useful for large datasets.
- **Memory-Constrained Systems:** ideal when in-place sorting is necessary.
- **Systems with Worst-Case Guarantees:** used in scenarios where worst-case performance must be strictly bounded.
- **Real-Time Systems:** when predictable performance is more important than average-case speed.

## Example Code

```js
function heapify(arr, n, i) {
  let largest = i;
  let left = 2 * i + 1;
  let right = 2 * i + 2;

  if (left < n && arr[left] > arr[largest]) {
    largest = left;
  }

  if (right < n && arr[right] > arr[largest]) {
    largest = right;
  }

  if (largest !== i) {
    [arr[i], arr[largest]] = [arr[largest], arr[i]];
    heapify(arr, n, largest);
  }
}

function heapSort(arr) {
  let n = arr.length;

  for (let i = Math.floor(n / 2) - 1; i >= 0; i--) {
    heapify(arr, n, i);
  }

  for (let i = n - 1; i > 0; i--) {
    [arr[0], arr[i]] = [arr[i], arr[0]];
    heapify(arr, i, 0);
  }

  return arr;
}

const numbers = [8, 6, 4, 2];
console.log("Numbers:", numbers);
console.log("Sorted numbers:", heapSort(numbers)); // Output: [2, 4, 6, 8]

const strings = ["cherry", "banana", "orange", "apple"];
console.log("Strings:", strings);
console.log("Sorted strings:", heapSort(strings)); // Output: ["apple", "orange", "banana", "cherry"]
```

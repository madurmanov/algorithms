# Bubble Sort

Bubble Sort is a simple algorithm that performs a sequential comparing of adjacent elements in an array and swaps them if they are in the wrong order. This process is continues until the array is fully sorted.

## Actions

1. Iterate through the array.
2. Compare each pair of adjacent elements.
3. Swap the elements if the current one is larger than the next (for ascending order).
4. Repeat the process for the remaining elements, reducing the range of the array after each iteration.
5. The algorithm stops when no swaps are made during a pass.

## Complexity

- **Best Case: Ω(n)** — the array is already sorted, requiring only one iteration to verify.
- **Average Case: Θ(n^2)** — elements are arranged randomly.
- **Worst Case: O(n^2)** — the array is sorted in reverse order.
- **Memory: O(1)** — requires only a fixed number of variables.

## Advantages

- **Simple Implementation:** the algorithm is extremely simple and intuitive.
- **Stable Sort:** it preserves the relative order of elements with equal values.
- **Small Arrays:** works well for small dataset due to its simplicity.

## Disadvantages

- **Poor Performance:** highly inefficient for large dataset.
- **Redundant Comparisons:** performs unnecessary operations even on partially sorted arrays.

## Use Cases

- **Small Arrays:** useful for small arrays.
- **Stable Sorting Needs:** applicable when stability of the sort is required.

## Example Code

```js
function bubbleSort(arr) {
  let n = arr.length;
  let swapped;

  do {
    swapped = false;
    for (let i = 0; i < n - 1; i++) {
      if (arr[i] > arr[i + 1]) {
        [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]];
        swapped = true;
      }
    }
    n--;
  } while (swapped);

  return arr;
}

const numbers = [8, 6, 4, 2];
console.log("Numbers:", numbers);
console.log("Sorted numbers:", bubbleSort(numbers)); // Output: [2, 4, 6, 8]

const strings = ["cherry", "banana", "orange", "apple"];
console.log("Strings:", strings);
console.log("Sorted strings:", bubbleSort(strings)); // Output: ["apple", "orange", "banana", "cherry"]
```

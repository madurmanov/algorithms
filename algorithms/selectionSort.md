# Selection Sort

Selection Sort is an algorithm that sorts an array by finding the minimum element from the unsorted part of the array and placing it at the beginning.

## Actions

1. Initialize the current index as the minimum.
2. Compare the current element with the rest of the elements in the array.
3. If a smaller element is found, update the index of the minimum element.
4. After traversing the array, swap the minimum element with the element at the current position.
5. Repeat this process for all elements in the array except the last one.

## Complexity

- **Best Case: Ω(n^2)** — all comparisons are performed regardless of data order.
- **Average Case: Θ(n^2)** — elements are in random order.
- **Worst Case: O(n^2)** — the array is sorted in reverse order.
- **Memory: O(1)** — no additional memory is required.

## Advantages

- **Efficient for Small Arrays:** works well for small dataset.

## Disadvantages

- **Inefficient for Large Arrays:** the quadratic complexity makes it slow for large dataset.
- **High Number of Comparisons:** even if the array is partially sorted, all comparisons are performed.

## Use Cases

- **Small Arrays:** useful for small arrays.

## Example Code

```js
function selectionSort(arr) {
  for (let i = 0; i < arr.length - 1; i++) {
    let minIndex = i;

    for (let j = i + 1; j < arr.length; j++) {
      if (arr[j] < arr[minIndex]) {
        minIndex = j;
      }
    }

    if (minIndex !== i) {
      [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
    }
  }

  return arr;
}

const numbers = [8, 6, 4, 2];
console.log("Numbers:", numbers);
console.log("Sorted numbers:", selectionSort(numbers)); // Output: [2, 4, 6, 8]

const strings = ["cherry", "banana", "orange", "apple"];
console.log("Strings:", strings);
console.log("Sorted strings:", selectionSort(strings)); // Output: ["apple", "orange", "banana", "cherry"]
```

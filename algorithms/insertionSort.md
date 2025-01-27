# Insertion Sort

Insertion Sort is an algorithm that sorts an array by inserting each element into its correct position as it iterates through the array.

## Actions

1. The current element is compared to elements in the sorted part of the array.
2. If the element is smaller, it is shifted left until it reaches its correct position.
3. This process is repeated for all elements in the array.

## Complexity

- **Best Case: Ω(n)** — the array is already sorted.
- **Average Case: Θ(n^2)** — elements are in random order.
- **Worst Case: O(n^2)** — the array is sorted in reverse order.
- **Memory: O(1)** — no additional memory is required.

## Advantages

- **Efficient for Small Arrays:** works well for small dataset.
- **Stable Sort:** relative order of equal elements.

## Disadvantages

- **Inefficient for Large Arrays:** the quadratic complexity makes it slow for large dataset.
- **Order Dependency:** performance is highly dependent on the initial arrangement of elements.

## Use Cases

- **Small Arrays:** useful for small arrays.
- **Nearly Sorted Arrays:** works well for arrays that are almost sorted.

## Example Code

```js
function insertionSort(arr) {
  for (let i = 1; i < arr.length; i++) {
    let current = arr[i];
    let j = i - 1;

    while (j >= 0 && arr[j] > current) {
      arr[j + 1] = arr[j];
      j--;
    }

    arr[j + 1] = current;
  }

  return arr;
}

const numbers = [8, 6, 4, 2];
console.log("Numbers:", numbers);
console.log("Sorted numbers:", insertionSort(numbers)); // Output: [2, 4, 6, 8]

const strings = ["cherry", "banana", "orange", "apple"];
console.log("Strings:", strings);
console.log("Sorted strings:", insertionSort(strings)); // Output: ["apple", "orange", "banana", "cherry"]
```

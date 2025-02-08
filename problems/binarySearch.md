# Binary Search

## Solution

```js
/**
 * Performs binary search on a sorted array to find the index of a target value.
 *
 * @param {number[]} nums - A sorted array of numbers.
 * @param {number} target - The value to search for.
 * @return {number} - The index of the target if found; otherwise, -1.
 */
function binarySearch(nums, target) {
  let left = 0;
  let right = nums.length - 1;

  // Loop until the search range is exhausted
  while (left <= right) {
    // Calculate the middle index
    let mid = Math.floor((left + right) / 2);

    // Check if the target is found
    if (nums[mid] === target) {
      return mid;
    }

    // If the target is greater, ignore the left half
    if (nums[mid] < target) {
      left = mid + 1;
    } else {
      // If the target is smaller, ignore the right half
      right = mid - 1;
    }
  }

  // Target not found
  return -1;
}

const sortedArray = [1, 3, 5, 7, 9, 11];
const targetValue = 7;
const index = binarySearch(sortedArray, targetValue);
console.log("Index of", targetValue, "is:", index); // Output: Index of 7 is: 3
```

## Explanation

1. **Initialization:** two pointers, `left` and `right`, are initialized to the beginning and end of the array, respectively.
2. **Iteration:** the loop continues as long as `left` is less than or equal to `right`.
   - The middle index `mid` is calculated using `Math.floor((left + right) / 2)`.
   - If `nums[mid]` is equal to the target, the index `mid` is returned.
   - If `nums[mid]` is less than the target, it means the target must be in the right half of the array; therefore, update `left` to `mid + 1`.
   - If `nums[mid]` is greater than the target, update `right` to `mid - 1` to search in the left half.
3. **Return Result:** if the loop finishes without finding the target, the function returns `-1` to indicate that the target is not present in the array.

## Complexity

- **Time:** O(logn)
- **Memory:** O(1)

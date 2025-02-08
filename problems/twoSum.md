# Two Sum

## Solution

```js
/**
 * Function that returns the indices of the two numbers in the array `nums` whose sum equals the target.
 *
 * @param {number[]} nums - Array of numbers.
 * @param {number} target - Target sum.
 * @return {number[]} - An array containing two indices or an empty array if no solution is found.
 */
function twoSum(nums, target) {
  // Object to store numbers and their corresponding indices.
  const numToIndex = {};

  // Iterate through the array.
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i];
    // Calculate the complement needed to reach the target.
    const complement = target - num;

    // If the complement exists in the object, return the indices.
    if (complement in numToIndex) {
      return [numToIndex[complement], i];
    }

    // Save the current number and its index.
    numToIndex[num] = i;
  }

  // Return an empty array if no pair is found.
  return [];
}

const nums = [2, 3, 7, 9];
const target = 5;
const result = twoSum(nums, target);
console.log("Indices of the numbers that sum up to", target, ":", result);
```

## Explanation

1. **Initialization:** an object `numToIndex` is created to store numbers as keys and their indices as values.
2. **Iteration:** a `for` loop is used to iterate over the array `nums`, obtaining the index `i` and the value `num` at each iteration.
   - For each number, the complement is calculated as `target - num`.
   - If the complement exists in `numToIndex`, it means that a pair of numbers adding up to the target has been found. The function returns the array `[numToIndex[complement], i]` with the corresponding indices.
   - If the complement is not found, the current number and its index are saved in the `numToIndex` object.
3. **Return Result:** if the loop completes without finding a pair, the function returns an empty array.

## Complexity

- **Time:** O(n)
- **Memory:** O(n)

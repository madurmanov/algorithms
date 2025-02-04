# Two Sum

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

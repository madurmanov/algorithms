# Find the Median of Two Sorted Arrays

## Solution

```js
/**
 * Finds the median of two sorted arrays.
 *
 * @param {number[]} nums1 - First sorted array.
 * @param {number[]} nums2 - Second sorted array.
 * @return {number} - The median value.
 */
function findMedianSortedArrays(nums1, nums2) {
  // Ensure that nums1 is the smaller array to minimize binary search time.
  if (nums1.length > nums2.length) {
    return findMedianSortedArrays(nums2, nums1);
  }

  const x = nums1.length;
  const y = nums2.length;
  let low = 0;
  let high = x;

  while (low <= high) {
    // Partition indices for nums1 and nums2.
    const partitionX = Math.floor((low + high) / 2);
    const partitionY = Math.floor((x + y + 1) / 2) - partitionX;

    // If partitionX is 0, there are no elements on the left side in nums1.
    // Use -Infinity so that it does not affect max calculations.
    const maxLeftX = partitionX === 0 ? -Infinity : nums1[partitionX - 1];
    // If partitionX is at the end of nums1, there are no elements on the right side.
    // Use Infinity for min calculations.
    const minRightX = partitionX === x ? Infinity : nums1[partitionX];

    // Similarly for nums2.
    const maxLeftY = partitionY === 0 ? -Infinity : nums2[partitionY - 1];
    const minRightY = partitionY === y ? Infinity : nums2[partitionY];

    // Check if we have found the correct partitions.
    if (maxLeftX <= minRightY && maxLeftY <= minRightX) {
      // If the total number of elements is even, take the average of the two middle values.
      if ((x + y) % 2 === 0) {
        return (
          (Math.max(maxLeftX, maxLeftY) + Math.min(minRightX, minRightY)) / 2
        );
      } else {
        // If the total number of elements is odd, return the maximum of the left parts.
        return Math.max(maxLeftX, maxLeftY);
      }
    } else if (maxLeftX > minRightY) {
      // Move partitionX to the left.
      high = partitionX - 1;
    } else {
      // Move partitionX to the right.
      low = partitionX + 1;
    }
  }

  // If the arrays are not sorted or inputs are invalid.
  throw new Error("Input arrays are not sorted or invalid.");
}

const nums1 = [1, 3, 8];
const nums2 = [7, 9, 10, 11];

const median = findMedianSortedArrays(nums1, nums2);
console.log("Median is:", median); // Output: 8
```

## Explanation

1. **Ensure the Smaller Array is Used for Binary Search:** to achieve optimal efficiency, the binary search is performed on the smaller array. If `nums1` is larger than `nums2`, we swap them by recursively calling the function with reversed arguments.
2. **Define Partitions:**
   - We define a partition in `nums1` as `partitionX` and calculate the corresponding partition in `nums2` as `partitionY = Math.floor((x + y + 1) / 2) - partitionX`.
   - The idea is to split both arrays such that the left half (combined) contains the first half of the sorted elements and the right half contains the remaining elements.
3. **Handling Edge Cases with Infinity:**
   - If the partition is at the extreme left (i.e., no elements on the left), we assign `-Infinity` to `maxLeftX` (or `maxLeftY`).
   - If the partition is at the extreme right (i.e., no elements on the right), we assign `Infinity` to `minRightX` (or `minRightY`).
4. **Check for Correct Partitioning:**
   - The correct partition is found when the maximum element on the left side of `nums1` is less than or equal to the minimum element on the right side of `nums2` and vice versa.
   - If this condition is satisfied, then:
     - For an even total length, the median is the average of the greater of the left elements and the lesser of the right elements.
     - For an odd total length, the median is the maximum of the left elements.
5. **Adjusting the Binary Search:**
   - If `maxLeftX > minRightY`, move the partition in `nums1` to the left.
   - Otherwise, move the partition to the right.

## Complexity

- **Time:** O(log(min(m,n)))
- **Memory:** O(1)

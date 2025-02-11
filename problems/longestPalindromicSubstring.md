# Longest Palindromic Substring

## Solution

```js
/**
 * Finds the longest palindromic substring in the given string.
 *
 * @param {string} s - The input string.
 * @return {string} - The longest palindromic substring.
 */
function longestPalindromicSubstring(s) {
  if (!s || s.length < 1) return "";

  // Variables to track the start and end indices of the longest palindrome found.
  let start = 0;
  let end = 0;

  // Iterate over each character in the string, treating each as the center of a potential palindrome.
  for (let i = 0; i < s.length; i++) {
    // Check for odd-length palindromes (single center)
    let len1 = expandAroundCenter(s, i, i);
    // Check for even-length palindromes (two centers)
    let len2 = expandAroundCenter(s, i, i + 1);
    // Choose the longer palindrome length from the two cases.
    let len = Math.max(len1, len2);

    // If a longer palindrome is found, update the start and end indices.
    if (len > end - start) {
      start = i - Math.floor((len - 1) / 2);
      end = i + Math.floor(len / 2);
    }
  }

  // Return the longest palindromic substring.
  return s.substring(start, end + 1);
}

/**
 * Expands around the given center indices (left and right) to find the length of the palindrome.
 *
 * @param {string} s - The input string.
 * @param {number} left - The left index of the center.
 * @param {number} right - The right index of the center.
 * @return {number} - The length of the palindrome found.
 */
function expandAroundCenter(s, left, right) {
  while (left >= 0 && right < s.length && s[left] === s[right]) {
    left--;
    right++;
  }
  // Subtract 1 because the last iteration expanded one step too far on both sides.
  return right - left - 1;
}

const input = "babad";
const longestPalindrome = longestPalindromicSubstring(input);
console.log("Longest Palindromic Substring:", longestPalindrome); // Output: "bab" or "aba" (both are acceptable answers)
```

## Explanation

1. **Initial Check:** the function first checks if the string is empty or has less than one character. If so, it returns an empty string.
2. **Iteration:**
   - The algorithm iterates over each character in the string, considering each index as a potential center of a palindrome.
   - For each index `i`, two cases are checked:
     - Odd-length Palindrome: the center is at `i` (i.e., `left = i` and `right = i`).
     - Even-length Palindrome: the center is between `i` and `i + 1` (i.e., `left = i` and `right = i + 1`).
3. **Expanding Around the Center:** .
   - The helper function `expandAroundCenter` is used to expand outward from the center(s) as long as the characters on the left and right are equal.
   - It returns the length of the palindrome found by calculating the distance between the indices after expansion.
4. **Updating the Longest Palindrome:** .
   - After determining the length of the palindrome for both cases, the maximum length is compared with the previously found longest palindrome.
   - If a longer palindrome is found, the `start` and `end` indices are updated accordingly.
5. **Return Result:** finally, the function returns the substring between the `start` and `end` indices, which represents the longest palindromic substring in the input.

## Complexity

- **Time:** O(n^2)
- **Memory:** O(1)

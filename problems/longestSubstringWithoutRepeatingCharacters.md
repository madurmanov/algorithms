# Longest Substring Without Repeating Characters

## Solution

```js
/**
 * Finds the length of the longest substring without repeating characters.
 *
 * @param {string} s - The input string.
 * @return {number} - The length of the longest substring without repeating characters.
 */
function longestSubstringWithoutRepeatingCharacters(s) {
  // Map to store the last seen index of each character.
  const charIndexMap = new Map();
  let maxLength = 0;
  // 'start' marks the beginning of the current window.
  let start = 0;

  // Iterate over each character in the string.
  for (let i = 0; i < s.length; i++) {
    const char = s[i];

    // If the character has been seen before and its index is within the current window,
    // update the start of the window.
    if (charIndexMap.has(char) && charIndexMap.get(char) >= start) {
      start = charIndexMap.get(char) + 1;
    }

    // Update the last seen index of the character.
    charIndexMap.set(char, i);

    // Calculate the length of the current window and update maxLength if needed.
    maxLength = Math.max(maxLength, i - start + 1);
  }

  return maxLength;
}

const input = "abcabcbb";
const result = longestSubstringWithoutRepeatingCharacters(input);
console.log(
  "Length of the longest substring without repeating characters:",
  result
); // Output: 3
```

## Explanation

1. **Initialization:**
   - A `Map` called `charIndexMap` is used to store the last seen index of each character.
   - The variable `maxLength` is initialized to 0 to keep track of the maximum substring length found.
   - The variable `start` represents the starting index of the current window (substring) without repeating characters.
2. **Iteration:**
   - The function loops through each character in the string using its index `i`.
   - For each character, the algorithm checks if it has already been seen and if its last seen index is within the current window (i.e., greater than or equal to `start`).
3. **Adjusting Window:** if the current character is a repeat within the current window, update the `start` index to one position right of the previous occurrence of that character. This ensures that the new window does not include the repeated character.
4. **Updating Map and Maximum Length:**
   - The current character's index is updated in `charIndexMap`.
   - The length of the current window is calculated as `i - start + 1`, and `maxLength` is updated if this value is greater than the previous maximum.
5. **Return Result:** after processing all characters, the function returns `maxLength`, which represents the length of the longest substring without repeating characters.

## Complexity

- **Time:** O(n)
- **Memory:** O(min(n,m))

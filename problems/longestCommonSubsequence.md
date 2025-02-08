# Longest Common Subsequence

```js
/**
 * Computes the length of the longest common subsequence (LCS) of two strings.
 *
 * @param {string} text1 - The first string.
 * @param {string} text2 - The second string.
 * @return {number} - The length of the longest common subsequence.
 */
function longestCommonSubsequence(text1, text2) {
  const m = text1.length;
  const n = text2.length;

  // Create a 2D DP table with dimensions (m + 1) x (n + 1) and initialize all cells to 0.
  // dp[i][j] will hold the length of LCS for text1[0...i-1] and text2[0...j-1].
  const dp = Array.from({ length: m + 1 }, () => Array(n + 1).fill(0));

  // Build the table in a bottom-up manner.
  for (let i = 1; i <= m; i++) {
    for (let j = 1; j <= n; j++) {
      if (text1[i - 1] === text2[j - 1]) {
        // If characters match, add 1 to the result from the previous indices.
        dp[i][j] = dp[i - 1][j - 1] + 1;
      } else {
        // Otherwise, take the maximum from either excluding the current character from text1 or text2.
        dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
      }
    }
  }

  // The value in dp[m][n] is the length of the LCS for the two strings.
  return dp[m][n];
}

const text1 = "abcde";
const text2 = "ace";
const lcsLength = longestCommonSubsequence(text1, text2);
console.log("Length of the longest common subsequence:", lcsLength); // Output: 3
```

## Explanation

1. **Initialization:**
   - Determine the lengths of the two input strings, `text1` and `text2`, storing them in `m` and `n` respectively.
   - Create a 2D array `dp` with dimensions `(m + 1) x (n + 1)` filled with zeros. The cell `dp[i][j]` will store the length of the LCS for the substrings `text1[0...i-1]` and `text2[0...j-1]`.
2. **Building DP Table:**
   - Iterate through the strings using two nested loops starting from `i = 1` and `j = 1` (since the 0-th row and column are used for the base case of empty substrings).
   - If `text1[i - 1]` equals `text2[j - 1]`, it means that this character is part of the LCS. Thus, update `dp[i][j]` to be `dp[i - 1][j - 1] + 1`.
   - If they do not match, take the maximum value from either ignoring the current character of `text1` or `text2`. That is, `dp[i][j]` is set to `Math.max(dp[i - 1][j], dp[i][j - 1])`.
3. **Return Result:** after filling out the table, the bottom-right cell `dp[m][n]` contains the length of the longest common subsequence between the two strings.

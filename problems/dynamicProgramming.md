# Dynamic Programming

```js
/**
 * Determines the minimum number of coins needed to make up a given amount.
 * If it is not possible to form the amount with the given coins, returns -1.
 *
 * @param {number[]} coins - An array of distinct coin denominations.
 * @param {number} amount - The total amount to be formed.
 * @return {number} - The minimum number of coins required to form the amount, or -1 if it's not possible.
 */
function coinChange(coins, amount) {
  // Create a DP array with length (amount + 1) and initialize with Infinity.
  // dp[i] will represent the minimum coins needed for the amount i.
  const dp = new Array(amount + 1).fill(Infinity);

  // Base case: 0 coins are needed to form amount 0.
  dp[0] = 0;

  // Loop through all amounts from 1 to 'amount'
  for (let i = 1; i <= amount; i++) {
    // For each coin, try to update the dp value if the coin can be used.
    for (let coin of coins) {
      // If the coin's value is not more than the current amount
      if (coin <= i) {
        // dp[i] is the minimum of its current value and the number of coins needed for (i - coin) plus one coin
        dp[i] = Math.min(dp[i], dp[i - coin] + 1);
      }
    }
  }

  // If dp[amount] is still Infinity, it means it's not possible to form that amount with given coins.
  return dp[amount] === Infinity ? -1 : dp[amount];
}

const coins = [1, 2, 5];
const amount = 11;
const result = coinChange(coins, amount);
console.log("Minimum coins needed:", result); // Output: 3 (11 can be formed by 5 + 5 + 1)
```

## Explanation

1. **Initialization:**
   - A dynamic programming (DP) array `dp` of length `amount + 1` is created and filled with `Infinity`.
   - The value `dp[i]` represents the minimum number of coins required to make up the amount `i`.
2. **Filling DP Table:**
   - For each amount `i` from 1 to the target `amount`, the algorithm iterates over each coin denomination in the `coins` array.
   - If a coin's value is less than or equal to the current amount (`i`), the algorithm considers using that coin.
   - It then updates `dp[i]` to be the minimum of its current value and `dp[i - coin] + 1` (which represents using one coin of the current denomination plus the optimal solution for the remaining amount).
3. **Return Result:**
   - After filling in the DP table, if `dp[amount]` remains `Infinity`, it means that it is not possible to form the target amount with the given coin denominations, and the function returns `-1`.
   - Otherwise, `dp[amount]` is returned, representing the minimum number of coins needed.

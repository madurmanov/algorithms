# Valid Parentheses

```js
/**
 * Determines if the input string of parentheses is valid.
 * A string is considered valid if every opening bracket has a corresponding closing bracket in the correct order.
 *
 * @param {string} s - The input string containing only the characters '(', ')', '{', '}', '[' and ']'.
 * @return {boolean} - Returns true if the string is valid; otherwise, returns false.
 */
function isValid(s) {
  // Stack to keep track of opening brackets.
  const stack = [];

  // Mapping of closing brackets to their corresponding opening brackets.
  const mapping = {
    ")": "(",
    "}": "{",
    "]": "[",
  };

  // Iterate over each character in the string.
  for (let i = 0; i < s.length; i++) {
    const char = s[i];

    // If the character is an opening bracket, push it onto the stack.
    if (char === "(" || char === "{" || char === "[") {
      stack.push(char);
    }
    // If the character is a closing bracket.
    else if (char === ")" || char === "}" || char === "]") {
      // If the stack is empty or the top element does not match the corresponding opening bracket, it's invalid.
      if (stack.length === 0 || stack.pop() !== mapping[char]) {
        return false;
      }
    }
  }

  // If the stack is empty, all brackets were properly closed; otherwise, it's invalid.
  return stack.length === 0;
}

const s1 = "()[]{}";
const s2 = "([)]";
const s3 = "{[]}";

console.log("Is valid parentheses? ", isValid(s1)); // Output: true
console.log("Is valid parentheses? ", isValid(s2)); // Output: false
console.log("Is valid parentheses? ", isValid(s3)); // Output: true
```

## Explanation

1. **Initialization:** we create an empty stack (an array) to keep track of the opening brackets encountered in the string.
2. **Mapping Creation:** a mapping object `mapping` is defined where each closing bracket is mapped to its corresponding opening bracket. This helps in quickly checking if the current closing bracket matches the last seen opening bracket.
3. **Iteration:**
   - We loop through each character in the string.
   - If the character is an opening bracket (`(`, `{`, or `[`), we push it onto the stack.
   - If the character is a closing bracket (`)`, `}`, or `]`), we perform two checks:
     - If the stack is empty, it means there is no corresponding opening bracket, so the string is invalid.
     - Otherwise, we pop the top element from the stack and compare it to the expected opening bracket (using the mapping). If they don't match, the string is invalid.
4. **Final Check:**
   - After processing all characters, if the stack is empty, it means every opening bracket had a matching closing bracket in the correct order, so the string is valid.
   - If the stack is not empty, some opening brackets were not closed, making the string invalid.

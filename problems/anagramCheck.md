# Anagram Check

## Solution

```js
/**
 * Checks if two strings are anagrams of each other.
 *
 * @param {string} s - The first input string.
 * @param {string} t - The second input string.
 * @return {boolean} - Returns true if the strings are anagrams, false otherwise.
 */
function isAnagram(s, t) {
  if (s.length !== t.length) return false;

  // Convert strings to character arrays, sort them, and compare
  return s.split("").sort().join("") === t.split("").sort().join("");
}

console.log(isAnagram("listen", "silent")); // Output: true
console.log(isAnagram("hello", "world")); // Output: false
```

## Explanation

1. **Steps:**
   - If the lengths of the two strings are different, return `false`.
   - Convert both strings into character arrays.
   - Sort both arrays alphabetically.
   - Convert the sorted arrays back into strings.
2. **Return Result:** compare the two sorted strings. If they are equal, return `true`, otherwise return `false`.

## Complexity

- **Time:** O(nlogn)
- **Memory:** O(n)

# Anagram Check Using Hash Map

## Solution

```js
/**
 * Checks if two strings are anagrams using a frequency counter.
 *
 * @param {string} s - The first input string.
 * @param {string} t - The second input string.
 * @return {boolean} - Returns true if the strings are anagrams, false otherwise.
 */
function isAnagramUsingHashMap(s, t) {
  if (s.length !== t.length) return false;

  const count = {};

  for (let char of s) {
    count[char] = (count[char] || 0) + 1;
  }

  for (let char of t) {
    if (!count[char]) return false;
    count[char]--;
  }

  return true;
}

console.log(isAnagramUsingHashMap("listen", "silent")); // Output: true
console.log(isAnagramUsingHashMap("hello", "world")); // Output: false
```

## Explanation

1. **Initialization:**
   - If the lengths of the two strings are different, return `false`.
   - Create a hash map (object) to store character frequencies of the first string.
2. **Iteration:**
   - Iterate through the first string and increment character counts in the hash map.
   - Iterate through the second string and decrement corresponding character counts.
3. **Return Result:**
   - If any count becomes negative or a character is missing, return `false`.
   - If all counts are zero, return `true`.

## Complexity

- **Time:** O(n)
- **Memory:** O(1)

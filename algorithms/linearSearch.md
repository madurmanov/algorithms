# LinearSearch

```js
function linearSearch(arr, target) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === target) {
      return i;
    }
  }
  return -1;
}

const numbers = [2, 4, 6, 8];
console.log("Numbers:", numbers);
console.log("Search 8:", linearSearch(numbers, 8)); // Output: 3
console.log("Search 9:", linearSearch(numbers, 9)); // Output: -1

const strings = ["apple", "orange", "banana", "cherry"];
console.log("Strings:", strings);
console.log("Search banana:", linearSearch(strings, "banana")); // Output: 2
console.log("Search mango:", linearSearch(strings, "mango")); // Output: -1
```

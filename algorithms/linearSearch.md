# LinearSearch

Linear Search is a simple algorithm that performs a sequeantial checking of all elements in a data structure.

## Actions

1. Start from the first element of the data structure.
2. Compare the current element with the target value.
   - If the element matches the target, return the index.
   - If the current element doesn't match, move to the next element.
3. Continue until the element is found or the end of the data structure is reached.
4. If the element isn't found, return an indicator of absence.

## Complexity

- **Best Case: Ω(1)** — the element is found at the first position.
- **Average Case: Θ(n)** — the element is located somewhere in the middle.
- **Worst Case: O(n)** — the element is at the end of the data structure or not present.
- **Memory: O(1)** — no additional memory is required.

## Advantages

- **Simple Implementation:** the algorithm is extremely simple and intuitive.
- **No Data Requirements:** works with unsorted data.
- **Supports Multiple Data Structures:** can be used with arrays, lists and other linear data structures.
- **Low Memory Overhead:** memory complexity is O(1), as only one variable is used for iteration.

## Disadvantages

- **Slow on Large Datasets:** linear iteration through all elements makes it inefficient for large data structures.
- **No Optimization:** even if the target element is absent, the entire array must be checked.
- **Inefficiency for Frequent Searches:** execution time grows linearly with data size.

## Use Cases

- **Small Datasets:** works well for small data structures where the overhead of more complex algorithms is unnecessary.
- **Unsorted Data:** when the data is unsorted and sorting isn't feasible.
- **One-Time Operations:** for a one-off search where optimization isn't a priority.
- **Simple Data Structures:** suitable for data structures where implementing advanced algorithms is challenging.

## Example Code

### Array

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

### Stack

```js
class Stack {
  constructor() {
    this.items = [];
  }

  push(value) {
    this.items.push(value);
  }

  pop() {
    return this.items.pop();
  }

  all() {
    return this.items;
  }

  linearSearch(target) {
    for (let i = 0; i < this.items.length; i++) {
      if (this.items[i] === target) {
        return i;
      }
    }
    return -1;
  }
}

const stack = new Stack();
stack.push(2);
stack.push(4);
stack.push(6);
stack.push(8);

console.log("Stack:", stack.all());
console.log("Search 8:", stack.linearSearch(8)); // Output: 3
console.log("Search 9:", stack.linearSearch(9)); // Output: -1
```

### Queue

```js
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(value) {
    this.items.push(value);
  }

  dequeue() {
    return this.items.shift();
  }

  all() {
    return this.items;
  }

  linearSearch(target) {
    for (let i = 0; i < this.items.length; i++) {
      if (this.items[i] === target) {
        return i;
      }
    }
    return -1;
  }
}

const queue = new Queue();
queue.enqueue(2);
queue.enqueue(4);
queue.enqueue(6);
queue.enqueue(8);

console.log("Queue:", queue.all());
console.log("Search 8:", queue.linearSearch(8)); // Output: 3
console.log("Search 9:", queue.linearSearch(9)); // Output: -1
```

### List

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class SinglyLinkedList {
  constructor() {
    this.head = null;
  }

  append(value) {
    const node = new Node(value);
    if (!this.head) {
      this.head = node;
    } else {
      let current = this.head;
      while (current.next) {
        current = current.next;
      }
      current.next = node;
    }
  }

  all() {
    let current = this.head;
    const items = [];
    while (current) {
      items.push(current.value);
      current = current.next;
    }
    return items;
  }

  linearSearch(target) {
    let current = this.head;
    let index = 0;
    while (current) {
      if (current.value === target) {
        return index;
      }
      current = current.next;
      index++;
    }
    return -1;
  }
}

const list = new SinglyLinkedList();
list.append(2);
list.append(4);
list.append(6);
list.append(8);

console.log("List:", list.all());
console.log("Search 8:", list.linearSearch(8)); // Output: 3
console.log("Search 9:", list.linearSearch(9)); // Output: -1
```

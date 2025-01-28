# Stack

Stack is an abstract data structure that operates on the LIFO principle (Last In, First Out). Imagine a stack of plates: you can only add a new plate to the top and remove a plate from the top.

## Characteristics

- **Adding:** elements are added only to the top of the stack.
- **Removing:** only the top element can be removed.
- **Access:** you can't directly access elements from the middle or bottom, only from top.

## Best Practices

- For small tasks use arrays when you need a stack.
- For better performance you can implement a stack using objects to avoid array overhead.

## Use Cases

- **Memory Management:** stacks are used for managing functions calls in recursion.
- **Reversing Data:** useful for reversing strings or other data structures.
- **Algorithms:** used in algorithms like Depth-First Search (DFS), expression parsing and balancing parentheses.

## Operations

1. **Push:** adds an element to the top of stack.
2. **Pop:** removes the top element from the stack and returns it.
3. **Peek:** returns the top element without removing it.
4. **isEmpty:** checks if the stack is empty.
5. **Size:** returns the number of elements in the stack.

## Example Code

### Implementation Using an Array

```js
class Stack {
  constructor() {
    this.items = [];
  }

  push(element) {
    this.items.push(element);
  }

  pop() {
    if (this.isEmpty()) {
      return null;
    }
    return this.items.pop();
  }

  peek() {
    if (this.isEmpty()) {
      return null;
    }
    return this.items[this.items.length - 1];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }

  _all() {
    return this.items;
  }
}

const stack = new Stack();
stack.push(2);
stack.push(4);
stack.push(6);
stack.push(8);

console.log("Stack:", stack._all()); // Output: [2, 4, 6, 8]
console.log("Size:", stack.size()); // Output: 4
console.log("Pop:", stack.pop()); // Output: 8
console.log("Size:", stack.size()); // Output: 3
console.log("Peek:", stack.peek()); // Output: 6
```

### Implementation Using an Object

```js
class Stack {
  constructor() {
    this.items = {};
    this.count = 0;
  }

  push(element) {
    this.items[this.count] = element;
    this.count++;
  }

  pop() {
    if (this.isEmpty()) {
      return null;
    }
    this.count--;
    const topElement = this.items[this.count];
    delete this.items[this.count];
    return topElement;
  }

  peek() {
    if (this.isEmpty()) {
      return null;
    }
    return this.items[this.count - 1];
  }

  isEmpty() {
    return this.count === 0;
  }

  size() {
    return this.count;
  }

  _all() {
    return Object.values(this.items);
  }
}

const stack = new Stack();
stack.push(2);
stack.push(4);
stack.push(6);
stack.push(8);

console.log("Stack:", stack._all()); // Output: [2, 4, 6, 8]
console.log("Size:", stack.size()); // Output: 4
console.log("Pop:", stack.pop()); // Output: 8
console.log("Size:", stack.size()); // Output: 3
console.log("Peek:", stack.peek()); // Output: 6
```

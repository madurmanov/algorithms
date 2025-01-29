# Singly Linked List

Singly Linked List is a data structure consisting of a sequence of nodes, where each nodes contains value (actual data stored in the node) and pointer (reference to the next node). The key feature of a singly linked list is that it doesn't provide direct access to elements via an index. Instead, elements are accessed sequentially, starting from the head node.

## Characteristics

- **Dynamic Structure:** the list size can grow or shrink dynamically by adding or removing nodes.
- **Unidirectional Navigation:** each node points only the next node.
- **Non-Contiguous Memory Allocation:** nodes can be stored in different parts of memory and are linked via pointers.

## Use Cases

- **Implementing a Stack or Queue:** can efficiently implement a stack (LIFO) or a queue (FIFO) without memory reallocation like in an array.
- **Memory Management:** useful when dynamic memory allocation is important (e.g. in real-time systems).
- **Storing Data:** suitable when the number of elements is unknown in advance and frequent insertions/deletions occur.
- **Undo/Redo:** a linear structure is convenient for organizing state sequences.
- **Implementing Hash Tables:** used for resolving collisions by storing a list of values in a single table slot.

## Operations

- **insertAtBeginning**
- **insertAtEnd**
- **insertAtPosition**
- **removeFirst**
- **removeLast**
- **removeValue**
- **find**
- **traverseForward**

## Example Code

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
    this.size = 0;
  }

  insertAtBeginning(value) {
    const node = new Node(value);
    node.next = this.head;
    this.head = node;
    this.size++;
  }

  insertAtEnd(value) {
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
    this.size++;
  }

  insertAtPosition(value, position) {
    if (position < 0 || position > this.size) {
      throw new Error("Invalid position");
    }
    if (position === 0) {
      return this.insertAtBeginning(value);
    }
    const node = new Node(value);
    let current = this.head;
    let prev = null;
    let index = 0;
    while (index < position) {
      prev = current;
      current = current.next;
      index++;
    }
    node.next = current;
    prev.next = node;
    this.size++;
  }

  removeFirst() {
    if (!this.head) return;
    this.head = this.head.next;
    this.size--;
  }

  removeLast() {
    if (!this.head) return;
    if (!this.head.next) {
      this.head = null;
    } else {
      let current = this.head;
      let prev = null;
      while (current.next) {
        prev = current;
        current = current.next;
      }
      prev.next = null;
    }
    this.size--;
  }

  removeValue(value) {
    if (!this.head) return;
    if (this.head.value === value) {
      this.head = this.head.next;
      this.size--;
      return;
    }
    let current = this.head;
    let prev = null;
    while (current && current.value !== value) {
      prev = current;
      current = current.next;
    }
    if (current) {
      prev.next = current.next;
      this.size--;
    }
  }

  find(value) {
    let current = this.head;
    while (current) {
      if (current.value === value) return current;
      current = current.next;
    }
    return null;
  }

  traverseForward() {
    let current = this.head;
    const result = [];
    while (current) {
      result.push(current.value);
      current = current.next;
    }
    return result;
  }
}

const list = new SinglyLinkedList();

list.insertAtBeginning(2);
console.log("Insert at beginning 2:", list.traverseForward()); // Output: [2]
list.insertAtEnd(6);
console.log("Insert at end 6:", list.traverseForward()); // Output: [2, 6]
list.insertAtPosition(4, 1);
console.log("Insert at position (4, 1):", list.traverseForward()); // Output: [2, 4, 6]
console.log("Find 4:", list.find(4)); // Output: { value: 4; next: { value: 6; next: null; }}
list.removeFirst();
console.log("Remove first:", list.traverseForward()); // Output: [4, 6]
list.removeLast();
console.log("Remove last:", list.traverseForward()); // Output: [4]
list.removeValue(4);
console.log("Remove value 4:", list.traverseForward(4)); // Output: []
```

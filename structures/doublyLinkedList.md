# Doubly Linked List

Doubly Linked List is a data structure consisting of nodes, where each node contains value (data stored in the node), next pointer (reference to the next node) and previous pointer (reference to the previous node). Unlike a singly linked list, each node is aware of both its next and previous neighbors that enables traversal in both forward and backward directions.

## Characteristics

- **Bidirectional Navigation:** nodes contains references to both the next and previous nodes.
- **Flexible Insertion and Deletion:** nodes can be added or removed from any position without full traversal.
- **Increased Complexity:** requires more memory due to additinal pointers.

## Use Cases

- **Navigation Systems:** used in browsers for forward and backward navigation.
- **Implementing LRU Cache:** combined with a hash table it allows quick lookup, deletion and movement of recently used elements.
- **Text Editors:** managing text buffers where bidirectional traversal is needed.
- **Database Transactions:** keeping track of operations with rollback functionality.
- **File System Management:** managing directories and files with efficient access.

## Operations

- **insertAtBeginning**
- **insertAtEnd**
- **insertAtPosition**
- **removeFirst**
- **removeLast**
- **removeValue**
- **find**
- **traverseForward**
- **traverseBackward**

## Example Code

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
    this.prev = null;
  }
}

class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.size = 0;
  }

  insertAtBeginning(value) {
    const node = new Node(value);
    if (!this.head) {
      this.head = this.tail = node;
    } else {
      node.next = this.head;
      this.head.prev = node;
      this.head = node;
    }
    this.size++;
  }

  insertAtEnd(value) {
    const node = new Node(value);
    if (!this.tail) {
      this.head = this.tail = node;
    } else {
      node.prev = this.tail;
      this.tail.next = node;
      this.tail = node;
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
    if (position === this.size) {
      return this.insertAtEnd(value);
    }
    const node = new Node(value);
    let current = this.head;
    let index = 0;
    while (index < position) {
      current = current.next;
      index++;
    }
    node.next = current;
    node.prev = current.prev;
    current.prev.next = node;
    current.prev = node;
    this.size++;
  }

  removeFirst() {
    if (!this.head) return;
    if (this.head === this.tail) {
      this.head = this.tail = null;
    } else {
      this.head = this.head.next;
      this.head.prev = null;
    }
    this.size--;
  }

  removeLast() {
    if (!this.tail) return;
    if (this.head === this.tail) {
      this.head = this.tail = null;
    } else {
      this.tail = this.tail.prev;
      this.tail.next = null;
    }
    this.size--;
  }

  removeValue(value) {
    if (!this.head) return;
    let current = this.head;
    while (current && current.value !== value) {
      current = current.next;
    }
    if (!current) return;
    if (current === this.head) {
      return this.removeFirst();
    }
    if (current === this.tail) {
      return this.removeLast();
    }
    current.prev.next = current.next;
    current.next.prev = current.prev;
    this.size--;
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

  traverseBackward() {
    let current = this.tail;
    const result = [];
    while (current) {
      result.push(current.value);
      current = current.prev;
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
console.log("Find 4:", list.find(4)); // Output: { value: 4; next: { value: 6; next: null; prev: {}; }; prev: { value: 2; next: {}; prev: null; }; }
console.log("Traverse forward:", list.traverseForward()); // Output: [2, 4, 6]
console.log("Traverse backward:", list.traverseBackward()); // Output: [6, 4, 2]
list.removeFirst();
console.log("Remove first:", list.traverseForward()); // Output: [4, 6]
list.removeLast();
console.log("Remove last:", list.traverseForward()); // Output: [4]
list.removeValue(4);
console.log("Remove value 4:", list.traverseForward(4)); // Output: []
```

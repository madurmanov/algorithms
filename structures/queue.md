# Queue

Queue is an abstract data structure that operates on the FIFO principle (First In, First Out). Imagine line of people at a store: the first person to join the line is the first to be served and the last person must wait.

## Properties

- **Adding:** elements are added to the end of queue.
- **Removing:** elements are removed from the front of the queue.
- **Access:** elements are retrieved in the same order they were added.

## Best Practices

- For small tasks use arrays when you need a queue.
- For better performance you can implement a queue using objects to avoid array overhead.

## Use Cases

- **Task Scheduling:** used in task management, such as print queues or CPU task scheduling.
- **Real-Time Data Processing:** used in message queues or streaming data pipelines.
- **Algorithms:** used in algorithms like Breadth-First Search (BFS) and simulating processes.

## Operations

- **Enqueue:** adds an element to the end of the queue.
- **Dequeue:** removes an element from the front the queue and returns it.
- **Front:** returns the front element without removing it.
- **isEmpty:** check if the queue is empty.
- **Size:** returns the number of elements in the queue.

## Example Code

### Implementation Using an Array

```js
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(element) {
    this.items.push(element);
  }

  dequeue() {
    if (this.isEmpty()) {
      return null;
    }
    return this.items.shift();
  }

  front() {
    if (this.isEmpty()) {
      return null;
    }
    return this.items[0];
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

const queue = new Queue();
queue.enqueue(2);
queue.enqueue(4);
queue.enqueue(6);
queue.enqueue(8);

console.log("queue:", queue._all()); // Output: [2, 4, 6, 8]
console.log("Size:", queue.size()); // Output: 4
console.log("Dequeue:", queue.dequeue()); // Output: 2
console.log("Size:", queue.size()); // Output: 3
console.log("Front:", queue.front()); // Output: 4
```

### Implementation Using an Object

```js
class Queue {
  constructor() {
    this.items = {};
    this.head = 0;
    this.tail = 0;
  }

  enqueue(element) {
    this.items[this.tail] = element;
    this.tail++;
  }

  dequeue() {
    if (this.isEmpty()) {
      return null;
    }
    const removed = this.items[this.head];
    delete this.items[this.head];
    this.head++;
    return removed;
  }

  front() {
    if (this.isEmpty()) {
      return null;
    }
    return this.items[this.head];
  }

  isEmpty() {
    return this.head === this.tail;
  }

  size() {
    return this.tail - this.head;
  }

  _all() {
    return Object.values(this.items);
  }
}

const queue = new Queue();
[2, 4, 6, 8].forEach((value) => queue.enqueue(value));

console.log("Queue:", queue._all()); // Output: [2, 4, 6, 8]
console.log("Size:", queue.size()); // Output: 4
console.log("Dequeue:", queue.dequeue()); // Output: 2
console.log("Size:", queue.size()); // Output: 3
console.log("Front:", queue.front()); // Output: 4
```

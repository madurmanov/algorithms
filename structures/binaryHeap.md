# Binary Heap

Binary Heap is a specialized data structure typically implemented as a complete binary tree that satisfies a specific property:

- **Max-Heap:** the value of each parent node is greater than or equal to the values of its children. Thus, the maximum element is always at the root.
- **Min-Heap:** the value of each parent node is less than or equal to the values of its children, so the minimum element is at the root.

## Properties

- **Complete Binary Tree:** a heap is a complete binary tree, meaning all levels except possibly the last are completely filled, and the last level is filled from left to right.

## Use Cases

- **Implementation of Algorithms:** used to implement priority queues, in heap sort (a sorting algorithm), and in various graph algorithms (e.g., Dijkstra's shortest path algorithm).

## Operations

- **Peek**
- **Insert**
- **Extract**

## Example Code

```js
class Heap {
  constructor() {
    this.heap = [];
  }

  swap(i, j) {
    [this.heap[i], this.heap[j]] = [this.heap[j], this.heap[i]];
  }

  parentIndex(index) {
    return Math.floor((index - 1) / 2);
  }

  leftChildIndex(index) {
    return 2 * index + 1;
  }

  rightChildIndex(index) {
    return 2 * index + 2;
  }

  insert(value) {
    this.heap.push(value);
    this.heapifyUp();
  }

  peek() {
    return this.heap.length > 0 ? this.heap[0] : null;
  }

  extract() {
    if (this.heap.length === 0) return null;
    if (this.heap.length === 1) return this.heap.pop();

    const result = this.heap[0];
    this.heap[0] = this.heap.pop();
    this.heapifyDown();
    return result;
  }
}

class MinHeap extends Heap {
  heapifyUp() {
    let index = this.heap.length - 1;
    while (index > 0) {
      let parent = this.parentIndex(index);
      if (this.heap[parent] > this.heap[index]) {
        this.swap(parent, index);
        index = parent;
      } else {
        break;
      }
    }
  }

  heapifyDown() {
    let index = 0;
    const length = this.heap.length;

    while (this.leftChildIndex(index) < length) {
      let smallest = this.leftChildIndex(index);
      let right = this.rightChildIndex(index);

      if (right < length && this.heap[right] < this.heap[smallest]) {
        smallest = right;
      }

      if (this.heap[index] > this.heap[smallest]) {
        this.swap(index, smallest);
        index = smallest;
      } else {
        break;
      }
    }
  }
}

class MaxHeap extends Heap {
  heapifyUp() {
    let index = this.heap.length - 1;
    while (index > 0) {
      let parent = this.parentIndex(index);
      if (this.heap[parent] < this.heap[index]) {
        this.swap(parent, index);
        index = parent;
      } else {
        break;
      }
    }
  }

  heapifyDown() {
    let index = 0;
    const length = this.heap.length;

    while (this.leftChildIndex(index) < length) {
      let left = this.leftChildIndex(index);
      let right = this.rightChildIndex(index);
      let largest = left;

      if (right < length && this.heap[right] > this.heap[left]) {
        largest = right;
      }

      if (this.heap[index] < this.heap[largest]) {
        this.swap(index, largest);
        index = largest;
      } else {
        break;
      }
    }
  }
}

const minHeap = new MinHeap();

[11, 3, 13, 5, 7, 17, 19].forEach((value) => minHeap.insert(value));

console.log("Minimum element:", minHeap.peek()); // Output: 3
console.log("Extracted element:", minHeap.extract()); // Output: 3
console.log("New minimum element:", minHeap.peek()); // Output: 5

const maxHeap = new MaxHeap();

[11, 3, 13, 5, 7, 17, 19].forEach((value) => maxHeap.insert(value));

console.log("Maximum element:", maxHeap.peek()); // Output: 19
console.log("Extracted element:", maxHeap.extract()); // Output: 19
console.log("New maximum element:", maxHeap.peek()); // Output: 17
```

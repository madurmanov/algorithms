# Algorithms and Data Structures

## Asymptotic growth notations

| Symbols         | Borders        | Growth |
| --------------- | -------------- | :----: |
| Θ (Big Theta)   | Top and Bottom |   =n   |
| O (Big O)       | Top            |  <=n   |
| o (Small O)     | Top            |   <n   |
| Ω (Big Omega)   | Bottom         |  >=n   |
| ω (Small Omega) | Bottom         |   >n   |

## Complexity

| Name         | Notation |
| ------------ | :------: |
| Constant     |   O(1)   |
| Logarithmic  | O(logn)  |
| Linear       |   O(n)   |
| Linearithmic | O(nlogn) |
| Quadratic    |  O(n^2)  |
| Exponential  |  O(2^n)  |
| Factorial    |  O(n!)   |

![Complexity Chart](complexity.png)

## Data Structures

- [Array](structures/array.md)
- [Stack](structures/stack.md)
- [Queue](structures/queue.md)
- [Singly Linked List](structures/signlyLinkedList.md)
- [Doubly Linked List](structures/doublyLinkedList.md)
- [Hash Table](structures/hashTable.md)
- [Binary Search Tree (BST)](structures/binarySearchTree.md)

| Name               |        Access         |        Search         |        Insert         |        Delete         |
| ------------------ | :-------------------: | :-------------------: | :-------------------: | :-------------------: |
| Array              |         O(1)          |         O(n)          |      Ω(1) / O(n)      |      Ω(1) / O(n)      |
| Stack              |         O(n)          |         O(n)          |         O(1)          |         O(1)          |
| Queue              |         O(n)          |         O(n)          |         O(1)          |         O(1)          |
| Singly Linked List |      Ω(1) / O(n)      |      Ω(1) / O(n)      |         O(1)          |         O(1)          |
| Doubly Linked List |      Ω(1) / O(n)      |      Ω(1) / O(n)      |         O(1)          |         O(1)          |
| Hash Table         |      Θ(1) / O(n)      |      Θ(1) / O(n)      |      Θ(1) / O(n)      |      Θ(1) / O(n)      |
| Binary Search Tree | Ω(1) / Θ(logn) / O(n) | Ω(1) / Θ(logn) / O(n) | Ω(1) / Θ(logn) / O(n) | Ω(1) / Θ(logn) / O(n) |

## Algorithms

- **Search:**
  - [Linear Search](algorithms/linearSearch.md)
  - [Binary Search](algorithms/binarySearch.md)
  - [Deep-First Search](algorithms/deepFirstSearch.md)
  - [Breadth-First Search](algorithms/breadthFirstSearch.md)
- **Sort:**
  - [Bubble Sort](algorithms/bubbleSort.md)
  - [Insertion Sort](algorithms/insertionSort.md)
  - [Selection Sort](algorithms/selectionSort.md)
  - [Merge Sort](algorithms/mergeSort.md)
  - [Quick Sort](algorithms/quickSort.md)
  - [Heap Sort](algorithms/heapSort.md)

# Algorithms and Data Structures

An **algorithm** is a finite sequence of well-defined steps designed to solve a specific problem or compute a result. Algorithms can be represented as text, pseudocode, flowcharts or program code. They must exhibit **finiteness**, **determinism**, **effectiveness** and have **input/output data**.

**Key Properties of Algorithms:**

- **Finiteness** — must complete in a finite number of steps.
- **Determinism** — each step must be precisely defined.
- **Effectiveness** — must produce a correct result.
- **Input/Output Data** — takes one or more inputs and produces one or more outputs.

A **data structure** is a way of organizing, storing and managing data in computer memory to enable efficient access and modification. Different data structures are optimized for different operations, such as insertion, deletion, search and sorting.

**Key Properties of Data Structures:**

- **Organization** — defines how data is stored (linear, hierarchical, etc.).
- **Efficiency** — allows basic operations to be performed in optimal time.
- **Flexibility** — ability to dynamically change the size or structure of data.

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
| Cubic        |  O(n^3)  |
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
- [Binary Heap](structures/binaryHeap.md)

| Name               |        Access         |        Search         |        Insert         |        Delete         |
| ------------------ | :-------------------: | :-------------------: | :-------------------: | :-------------------: |
| Array              |         O(1)          |         O(n)          |      Ω(1) / O(n)      |      Ω(1) / O(n)      |
| Stack              |         O(n)          |         O(n)          |         O(1)          |         O(1)          |
| Queue              |         O(n)          |         O(n)          |         O(1)          |         O(1)          |
| Singly Linked List |      Ω(1) / O(n)      |      Ω(1) / O(n)      |         O(1)          |         O(1)          |
| Doubly Linked List |      Ω(1) / O(n)      |      Ω(1) / O(n)      |         O(1)          |         O(1)          |
| Hash Table         |      Θ(1) / O(n)      |      Θ(1) / O(n)      |      Θ(1) / O(n)      |      Θ(1) / O(n)      |
| Binary Search Tree | Ω(1) / Θ(logn) / O(n) | Ω(1) / Θ(logn) / O(n) | Ω(1) / Θ(logn) / O(n) | Ω(1) / Θ(logn) / O(n) |

| Name        | Create | Search Max | Extract Max | Increase Key | Insert  | Delete  | Merge  |
| ----------- | :----: | :--------: | :---------: | :----------: | :-----: | :-----: | :----: |
| Binary Heap |  O(n)  |    O(1)    |   O(logn)   |   O(logn)    | O(logn) | O(logn) | O(m+n) |

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

## Problems

1. [Two Sum](problems/twoSum.md)
   - **Description:** given an array of numbers and a target number, find a pair of indices such that the sum of the values equals the target.
   - **Test:** knowledge of hash tables and time optimization (achieving O(n) solution).
2. [Reverse a Linked List](problems/reverseLinkedList.md)
   - **Description:** given a singly linked list, reverse it so that the last element becomes the first.
   - **Test:** ability to work with linked data structures and understanding pointers.
3. [Detect Cycle in a Linked List](problems/detectCycleLinkedList.md)
   - **Description:** determine if a linked list contains a cycle.
   - **Test:** application of Floyd's cycle detection algorithm (the "tortoise and the hare"), pointer manipulation, and loop handling.
4. [Merge Two Sorted Lists](problems/mergeTwoSortedLists.md)
   - **Description:** given two sorted lists, merge them into one sorted list.
   - **Test:** ability to work with iterators/pointers, and understanding merging techniques in sorting.
5. [Binary Search](problems/binarySearch.md)
   - **Description:** implement the binary search algorithm on a sorted array.
   - **Test:** understanding of algorithmic complexity O(logn) and both recursive and iterative approaches.
6. [Sorting Algorithms](problems/sortingAlgorithms.md)
   - **Description:** implement algorithms such as QuickSort, MergeSort, or Bubble Sort.
   - **Test:** understanding of sorting principles, problem partitioning, recursion, and time complexity.
7. [Longest Substring Without Repeating Characters](problems/longestSubstringWithoutRepeatingCharacters.md)
   - **Description:** find the length of the longest substring without repeating characters.
   - **Test:** string manipulation, application of the "sliding window" technique, and optimization skills.
8. [Longest Common Subsequence](problems/longestCommonSubsequence.md)
   - **Description:** find the length of the longest common subsequence for two strings.
   - **Test:** dynamic programming, and optimization in terms of memory and time.
9. [Valid Parentheses](problems/validParentheses.md)
   - **Description:** determine if the parentheses in a string are correctly paired (e.g., “()[]{}”).
   - **Test:** use of stacks to verify matching pairs.
10. [Dynamic Programming](problems/dynamicProgramming.md)
    - **Description:** classic problems such as:
      - **Fibonacci:** calculate Fibonacci numbers using memoization or tabulation.
      - **Coin Change:** determine the minimum number of coins required for a given amount.
      - **Climbing Stairs:** count the number of ways to climb a staircase taking 1 or 2 steps at a time.
    - **Test:** ability to break down a problem into subproblems and optimally use resources.
11. [Longest Palindromic Substring](problems/longestPalindromicSubstring.md)
    - **Description:** find the longest substring that is a palindrome.
    - **Test:** combination of string manipulation and dynamic programming or expanding from the center.
12. [Find the Median of Two Sorted Arrays](problems/findMedianOfTwoSortedArrays.md)
    - **Description:** given two sorted arrays, find the median of the merged array.
    - **Test:** ability to use binary search in an unusual context and optimize the solution to O(log(min(m, n))).
13. [Lowest Common Ancestor](problems/lowestCommonAncestor.md)
    - **Description:** in a binary tree, find the lowest common ancestor of two nodes.
    - **Test:** working with trees, understanding recursion, and tree traversal techniques.
14. [Graph Traversal](problems/graphTraversal.md)
    - **Description:** implement graph traversal algorithms such as Depth-First Search (DFS) and Breadth-First Search (BFS)..
    - **Test:** ability to work with graph data structures, and understanding queues and stacks.
15. [Anagram Check](problems/anagramCheck.md)
    - **Description:** determine whether two strings are anagrams of each other.
    - **Test:** working with hash tables, sorting strings or arrays, and comparing character counts.

# Binary Search Tree

Binary Search Tree is a data structure that consists of nodes, where each node contains a key (or value) and two child nodes (left and right). The left subtree of each node contains only nodes with keys less than node's key. The right subtree of each node contains only nodes with keys greater than node's key. This properly allows for fast search, insertion and deletion operations.

## Properties

- **Binary Tree:** each node can have at most two children.
- **Order Rule:** for any node, the left subtree contains values smaller than the node and the right subtree contains values greater than the node.
- **Unique Values:** typically, BST nodes contains unique keys, although some implementations allow duplicates.
- **Logarithmic Depth:** balanced BST have a depth of O(logn) making operations efficient.
- **Recursive Structure:** each subtree of a BST is itself a binary search tree.
- **Efficient Search:** searching for an element takes O(logn) in balanced tree and O(n) in the worst case (unbalanced tree).
- **Ordered Traversal:** in-order traversal returns elements in sorted order.
- **Dynamic Structure:** the tree can be dynamically modified by inserting and deleting elements.

## Use Cases

- **Fast Lookup, Insertion and Deletion:** used in databases, indexes and dictionaries where quick element retrieval is crucial.
- **Autocomplete and Dictionary Storage:** can be applied in autocomplete systems for efficient prefix-based word searching.
- **Data Sorting:** elements can be sorted by inserting them into a BST and performing an in-order traversal.
- **Implementation of Priority Structures:** in some cases BST are used for priority queues when ordered access is required.
- **Interval and Range Queries:** variants line interval trees are used in geometric algorithms and time interval analysis.
- **Complition and Code Interpretation:** used in parsers for constructing expression trees and abstact syntax trees.
- **Data Compression:** applied in Huffman coding where a tree structure is built based on symbol frequency.

## Operations

- **Insert**
- **Remove**
- **Search**
- **TraverseInorder**
- **TraversePreorder**
- **TraversePostorder**

## Example Code

```js
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class BinarySearchTree {
  constructor() {
    this.root = null;
  }

  insert(value) {
    const node = new Node(value);
    if (!this.root) {
      this.root = node;
      return;
    }
    let current = this.root;
    while (true) {
      if (value < current.value) {
        if (!current.left) {
          current.left = node;
          return;
        }
        current = current.left;
      } else {
        if (!current.right) {
          current.right = node;
          return;
        }
        current = current.right;
      }
    }
  }

  remove(value) {
    this.root = this._remove(this.root, value);
  }

  _remove(node, value) {
    if (!node) return null;
    if (value < node.value) {
      node.left = this._remove(node.left, value);
    } else if (value > node.value) {
      node.right = this._remove(node.right, value);
    } else {
      if (!node.left) return node.right;
      if (!node.right) return node.left;
      const minRight = this._findMin(node.right);
      node.value = minRight.value;
      node.right = this._remove(node.right, minRight.value);
    }
    return node;
  }

  _findMin(node) {
    while (node.left) node = node.left;
    return node;
  }

  search(value) {
    let current = this.root;
    while (current) {
      if (value === current.value) return current;
      current = value < current.value ? current.left : current.right;
    }
    return null;
  }

  traverseInorder() {
    const result = [];
    this._traverseInorder(this.root, result);
    return result;
  }

  _traverseInorder(node, result) {
    if (node) {
      this._traverseInorder(node.left, result);
      result.push(node.value);
      this._traverseInorder(node.right, result);
    }
  }

  traversePreorder() {
    const result = [];
    this._traversePreorder(this.root, result);
    return result;
  }

  _traversePreorder(node, result) {
    if (node) {
      result.push(node.value);
      this._traverseInorder(node.left, result);
      this._traverseInorder(node.right, result);
    }
  }

  traversePostorder() {
    const result = [];
    this._traversePostorder(this.root, result);
    return result;
  }

  _traversePostorder(node, result) {
    if (node) {
      this._traverseInorder(node.left, result);
      this._traverseInorder(node.right, result);
      result.push(node.value);
    }
  }
}

const BST = new BinarySearchTree();

[11, 3, 13, 5, 7, 17, 19].forEach((value) => BST.insert(value));

console.log("In-order:", BST.traverseInorder()); // Output: [3, 5, 7, 11, 13, 17, 19]
console.log("Pre-order:", BST.traversePreorder()); // Output: [11, 3, 5, 7, 13, 17, 19]
console.log("Post-order:", BST.traversePostorder()); // Output: [3, 5, 7, 13, 17, 19, 11]

console.log("Search 7:", BST.search(7)); // Output: { value: 7, left: null, right: null }

BST.remove(11);
console.log("Remove 11:", BST.traverseInorder()); // Output: [3, 5, 7, 13, 17, 19]
```

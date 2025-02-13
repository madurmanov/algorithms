# Lowest Common Ancestor

## Solution

```js
// Definition for a binary tree node.
function TreeNode(val, left, right) {
  this.val = val === undefined ? 0 : val;
  this.left = left === undefined ? null : left;
  this.right = right === undefined ? null : right;
}

/**
 * Finds the lowest common ancestor (LCA) of two nodes in a binary tree.
 *
 * @param {TreeNode} root - The root of the binary tree.
 * @param {TreeNode} p - The first target node.
 * @param {TreeNode} q - The second target node.
 * @return {TreeNode} - The lowest common ancestor node of p and q.
 */
function lowestCommonAncestor(root, p, q) {
  // Base case: if the current node is null or equals one of the target nodes, return it.
  if (root === null || root === p || root === q) {
    return root;
  }

  // Recursively search for p and q in the left and right subtrees.
  const left = lowestCommonAncestor(root.left, p, q);
  const right = lowestCommonAncestor(root.right, p, q);

  // If both left and right are non-null, then the current node is the LCA.
  if (left !== null && right !== null) {
    return root;
  }

  // Otherwise, return the non-null child.
  return left !== null ? left : right;
}

// Constructing a sample binary tree:
//         3
//        / \
//       5   1
//      / \  / \
//     6   2 0   8
//        / \
//       7   4

const root = new TreeNode(3);
root.left = new TreeNode(5);
root.right = new TreeNode(1);
root.left.left = new TreeNode(6);
root.left.right = new TreeNode(2);
root.right.left = new TreeNode(0);
root.right.right = new TreeNode(8);
root.left.right.left = new TreeNode(7);
root.left.right.right = new TreeNode(4);

// Let's say we want to find the LCA for nodes with values 5 and 4.
const p = root.left; // Node with value 5
const q = root.left.right.right; // Node with value 4

const lca = lowestCommonAncestor(root, p, q);
console.log("Lowest Common Ancestor:", lca ? lca.val : null); // Output: 5
```

## Explanation

1. **Base Case:** if the current node (`root`) is `null`, or if it equals either of the target nodes (`p` or `q`), the function returns the current node. This handles the case where one of the nodes is found or the subtree is empty.
2. **Recursive Search:** the function calls itself recursively to search for `p` and `q` in the left subtree (`root.left`) and right subtree (`root.right`).
3. **Combining Results:**
   - If both recursive calls return non-null values, it means that one target node is found in the left subtree and the other in the right subtree. Hence, the current node is the lowest common ancestor.
   - If only one of the recursive calls returns a non-null value, that non-null result is propagated upward as the potential LCA.
4. **Return Result:** the final returned node is the lowest common ancestor of `p` and `q`.

## Complexity

- **Time:** O(n)
- **Memory:** O(n)

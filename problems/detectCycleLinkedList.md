# Detect Cycle in a Linked List

## Solution

```js
// Definition for a singly-linked list node.
function ListNode(val, next) {
  this.val = val === undefined ? 0 : val;
  this.next = next === undefined ? null : next;
}

/**
 * Function to determine if a linked list contains a cycle.
 *
 * @param {ListNode} head - The head of the linked list.
 * @return {boolean} - Returns true if a cycle is detected, otherwise false.
 */
function hasCycle(head) {
  // Initialize two pointers, slow and fast, both starting at the head.
  let slow = head;
  let fast = head;

  // Traverse the list while fast and fast.next are not null.
  while (fast !== null && fast.next !== null) {
    slow = slow.next; // Move slow pointer one step.
    fast = fast.next.next; // Move fast pointer two steps.

    // If the pointers meet, a cycle exists.
    if (slow === fast) {
      return true;
    }
  }

  // If we reach here, fast reached the end of the list, so no cycle exists.
  return false;
}

// Create nodes for the linked list.
let node3 = new ListNode(3);
let node2 = new ListNode(2, node3);
let node1 = new ListNode(1, node2);

// Introduce a cycle for testing: connect the tail to node2.
node3.next = node2;

// Test for cycle:
const result = hasCycle(node1);
console.log("Does the linked list have a cycle:", result); // Output: true

// To test a list without a cycle, simply break the cycle:
node3.next = null;
console.log("Does the linked list have a cycle:", hasCycle(node1)); // Output: false
```

## Explanation

1. **Initialization:** two pointers, `slow` and `fast`, are initialized to the head of the linked list.
2. **Iteration:** the loop continues as long as `fast` and `fast.next` are not `null`.
   - The `slow` pointer moves one node at a time (`slow = slow.next`).
   - The `fast` pointer moves two nodes at a time (`fast = fast.next.next`).
3. **Cycle Detection:** if at any point the `slow` pointer equals the `fast` pointer, it indicates that the linked list has a cycle, and the function returns `true`.
4. **No Cycle:** if the loop terminates because `fast` or `fast.next` becomes `null`, it means the linked list does not have a cycle, and the function returns `false`.

## Complexity

- **Time:** O(n)
- **Memory:** O(1)

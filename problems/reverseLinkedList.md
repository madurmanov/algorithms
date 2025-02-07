# Reverse a Linked List

```js
// Definition for a singly-linked list node.
function ListNode(val, next) {
  this.val = val === undefined ? 0 : val;
  this.next = next === undefined ? null : next;
}

/**
 * Function to reverse a singly linked list.
 *
 * @param {ListNode} head - The head of the original linked list.
 * @return {ListNode} - The head of the reversed linked list.
 */
function reverseLinkedList(head) {
  let prev = null;
  let curr = head;

  // Iterate until the end of the list is reached
  while (curr !== null) {
    let nextTemp = curr.next; // Store the next node
    curr.next = prev; // Reverse the current node's pointer
    prev = curr; // Move prev to the current node
    curr = nextTemp; // Move to the next node
  }

  // prev will be the new head of the reversed list
  return prev;
}

// Create nodes for the linked list.
let node3 = new ListNode(3);
let node2 = new ListNode(2, node3);
let node1 = new ListNode(1, node2);

let reversedHead = reverseLinkedList(node1);

// Print the values of the reversed list:
let current = reversedHead;
let result = [];
while (current) {
  result.push(current.val);
  current = current.next;
}
console.log("Reversed list:", result);
```

## Explanation

1. **Initialization:** two variables are created: `prev`, which is initially set to `null`, and `curr`, which points to the head of the list.
2. **Iteration:** while the current node `curr` is not `null`.
   - Save a reference to the next node (`nextTemp = curr.next`).
   - Reverse the pointer of the current node by setting `curr.next` to `prev`.
   - Update the variables: move `prev` to `curr` and `curr` to the saved next node.
3. **Return Result:** once `curr` becomes `null` (i.e., the entire list has been traversed), `prev` will point to the new head of the reversed list.

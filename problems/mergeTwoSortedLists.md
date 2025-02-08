# Merge Two Sorted Lists

## Solution

```js
// Definition for a singly-linked list node.
function ListNode(val, next) {
  this.val = val === undefined ? 0 : val;
  this.next = next === undefined ? null : next;
}

/**
 * Merges two sorted linked lists and returns the head of the new sorted list.
 *
 * @param {ListNode} l1 - The head of the first sorted linked list.
 * @param {ListNode} l2 - The head of the second sorted linked list.
 * @return {ListNode} - The head of the merged sorted linked list.
 */
function mergeTwoLists(l1, l2) {
  // Create a dummy node that will help in building the new list.
  let dummy = new ListNode(0);
  let current = dummy;

  // While both lists have nodes, compare their values.
  while (l1 !== null && l2 !== null) {
    if (l1.val < l2.val) {
      // If l1's value is smaller, attach it to the current node.
      current.next = l1;
      l1 = l1.next; // Move l1 pointer to the next node.
    } else {
      // If l2's value is smaller or equal, attach it to the current node.
      current.next = l2;
      l2 = l2.next; // Move l2 pointer to the next node.
    }
    // Move the current pointer to the newly attached node.
    current = current.next;
  }

  // If one of the lists still has nodes, attach the remaining nodes.
  if (l1 !== null) {
    current.next = l1;
  }
  if (l2 !== null) {
    current.next = l2;
  }

  // The merged list is next to the dummy node.
  return dummy.next;
}

// Creating first sorted list: 1 -> 3 -> 5
let l1 = new ListNode(1, new ListNode(3, new ListNode(5)));

// Creating second sorted list: 2 -> 4 -> 6
let l2 = new ListNode(2, new ListNode(4, new ListNode(6)));

// Merging the two lists
let mergedHead = mergeTwoLists(l1, l2);

// Printing the merged list:
let current = mergedHead;
let mergedListValues = [];
while (current !== null) {
  mergedListValues.push(current.val);
  current = current.next;
}
console.log("Merged Sorted List:", mergedListValues.join(", ")); // Output: 1, 2, 3, 4, 5, 6
```

## Explanation

1. **Node Definition:** we define a `ListNode` constructor function to create nodes for the linked list. Each node has a `val` property to store the value and a `next` property that points to the next node in the list.
2. **Dummy Node Creation:** a dummy node (`dummy`) is created to act as a placeholder at the beginning of the new merged list. This simplifies the process of attaching nodes without handling special cases for the head of the list. A `current` pointer is initialized to point to this dummy node.
3. **Merging Process:** .
   - We iterate through both linked lists (`l1` and `l2`) as long as neither is exhausted.
   - At each iteration, we compare the values of the current nodes in `l1` and `l2`.
   - The node with the smaller value is attached to `current.next`, and its corresponding pointer (`l1` or `l2`) is moved to the next node.
   - The `current` pointer is advanced to point to the newly attached node.
4. **Handling Remaining Nodes:** If one of the lists still has nodes after the main loop, we attach the remainder of that list to the merged list. Since both input lists are already sorted, the remaining nodes are also in order.
5. **Return Result:** Finally, we return `dummy.next`, which is the head of the newly merged sorted list.

## Complexity

- **Time:** O(n+m)
- **Memory:** O(1)

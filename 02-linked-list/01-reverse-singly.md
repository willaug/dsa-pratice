# 🔁 Reverse a Singly Linked List

> Copy this into your docs and fill the placeholders. Keep it short & practical.

## What it is

Reverse a singly linked list **in-place** by flipping each node’s `next` pointer so the list points backward.

## When to use

* Need the list in reverse order **without** extra memory.
* Preparing for problems like “add two numbers (lists)”, “palindrome check” (via half-reverse), etc.

## Mental model (1-liner)

“Walk the list once; for each node, **redirect `next` to the previous node**.”

## Pointers

* `prev` → starts `null`
* `curr` → starts `head`
* `next` → temp to hold `curr.next`

## Per-node steps

1. `next = curr.next`
2. `curr.next = prev`
3. `prev = curr`
4. `curr = next`
   ➡️ End: **`prev` is the new head**

## Code (JavaScript / Node 20+)

```js
class ListNode {
  constructor(val, next = null) {
    this.val = val;
    this.next = next;
  }
}

/**
 * Reverse a singly linked list.
 * Time: O(n) | Space: O(1)
 */
function reverse(head) {
  let prev = null, curr = head;
  while (curr) {
    const next = curr.next; // 1) save
    curr.next = prev;       // 2) flip
    prev = curr;            // 3) advance prev
    curr = next;            // 4) advance curr
  }
  return prev; // new head
}
```

## ASCII walkthrough (fill with your nodes)

```
Before:  A → B → C → null
Pass1:   A.next=null   prev=A, curr=B
Pass2:   B.next=A      prev=B, curr=C
Pass3:   C.next=B      prev=C, curr=null (stop)
After:   C → B → A → null  (head = C)
```

## Complexity

* **Time:** O(n) — single pass
* **Space:** O(1) — constant extra pointers

## Edge cases

* Empty list → returns `null`
* Single node → returns the same node

## Test snippet (optional)

```js
const a = new ListNode(1, new ListNode(2, new ListNode(3)));
const newHead = reverse(a);
// Expect: 3 -> 2 -> 1
```

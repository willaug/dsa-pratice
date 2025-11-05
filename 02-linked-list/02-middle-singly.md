# 🎯 Find the Middle of a Singly Linked List

> Copy into your docs and fill in examples. Simple, practical, and ready to use.

## What it is

Find the **middle node** using **two pointers**:

* `slow` moves **1** step
* `fast` moves **2** steps
  When `fast` reaches the end, `slow` is at the middle.

## When to use

* Need the middle to split a list (e.g., merge sort on lists).
* Palindrome check (reverse second half).
* Detect balanced partitions.

## Mental model (1-liner)

“Advance `fast` twice as fast as `slow`; when `fast` finishes, `slow` is in the middle.”

## Code (JavaScript / Node 20+)

```js
class ListNode {
  constructor(val, next = null) {
    this.val = val;
    this.next = next;
  }
}

/**
 * Returns the middle node.
 * If length is even, returns the **second** middle (LeetCode style).
 * Time: O(n) | Space: O(1)
 */
function middleNode(head) {
  let slow = head, fast = head;
  while (fast && fast.next) {
    slow = slow.next;         // +1 step
    fast = fast.next.next;    // +2 steps
  }
  return slow;
}

/**
 * Variant: return the **first** middle when length is even.
 * Trick: start fast one step ahead.
 */
function firstMiddle(head) {
  if (!head) return null;
  let slow = head, fast = head.next;
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
  }
  return slow;
}
```

## ASCII walkthrough (second middle)

List: `1 → 2 → 3 → 4 → 5 → 6 → null`
Initial: `slow=1`, `fast=1`

* Pass 1: `slow=2`, `fast=3`
* Pass 2: `slow=3`, `fast=5`
* Pass 3: `slow=4`, `fast=null` → **middle = 4** (second of the two middles)

## Complexity

* **Time:** O(n) — single pass
* **Space:** O(1) — constant

## Edge cases

* Empty list → returns `null`
* One node → that node is the middle
* Even length → pick **second** middle (default) or use `firstMiddle` to pick the **first**

## Test snippet (optional)

```js
const a = new ListNode(1,
  new ListNode(2,
    new ListNode(3,
      new ListNode(4,
        new ListNode(5,
          new ListNode(6))))));

console.log(middleNode(a).val);  // 4  (second middle)
console.log(firstMiddle(a).val); // 3  (first middle)
```

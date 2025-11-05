# ♻️ Detect Cycles in a Singly Linked List

> Copy into your docs and fill examples later. Simple, practical, and ready to use.

## What it is

Detect whether a linked list has a **cycle** (a node points back to a previous node), and optionally find the **cycle start** and **cycle length**. Uses **Floyd’s Tortoise & Hare**:

* `slow` moves **1** step
* `fast` moves **2** steps
  If they ever meet, there’s a **cycle**.

## When to use

* Validate list integrity (no self-loops).
* Problems that require cycle info (start node, length).
* Avoid infinite loops during traversal.

## Mental model (1-liner)

“If a loop exists, the fast pointer will eventually **lap** the slow pointer.”

---

## Code (JavaScript / Node 20+)

```js
class ListNode {
  constructor(val, next = null) {
    this.val = val;
    this.next = next;
  }
}

/**
 * 1) Has cycle? (Floyd)
 * Time: O(n) | Space: O(1)
 */
function hasCycle(head) {
  let slow = head, fast = head;
  while (fast && fast.next) {
    slow = slow.next;         // +1
    fast = fast.next.next;    // +2
    if (slow === fast) return true;
  }
  return false;
}
```

```js
/**
 * 2) Find cycle start node (if any)
 * Steps:
 *  - First, run Floyd until slow==fast (if never, return null).
 *  - Then, move one pointer to head; advance both 1 step at a time.
 *  - Where they meet is the cycle start.
 * Time: O(n) | Space: O(1)
 */
function detectCycleStart(head) {
  let slow = head, fast = head;

  // phase 1: meet inside the cycle (if it exists)
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
    if (slow === fast) {
      // phase 2: find entry
      let p1 = head, p2 = slow;
      while (p1 !== p2) {
        p1 = p1.next;
        p2 = p2.next;
      }
      return p1; // cycle entry
    }
  }
  return null; // no cycle
}
```

```js
/**
 * 3) Find cycle length (returns 0 if no cycle)
 * After slow==fast, keep one fixed and move the other until they meet again, counting steps.
 * Time: O(n) | Space: O(1)
 */
function cycleLength(head) {
  let slow = head, fast = head;

  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
    if (slow === fast) {
      // measure length
      let count = 1;
      fast = fast.next;
      while (fast !== slow) {
        fast = fast.next;
        count++;
      }
      return count;
    }
  }
  return 0;
}
```

---

## ASCII walkthrough (meeting idea)

```
head → a → b → c → d → e
              ↑       ↓
              h ← g ← f
slow: +1 each step
fast: +2 each step

They must meet somewhere inside the loop if it exists.
Then, resetting one pointer to head and advancing both +1
lands them together at the cycle entry.
```

---

## Complexity

* **Time:** O(n)
* **Space:** O(1)

## Edge cases

* Empty list or single node without self-loop → no cycle
* Self-loop (node.next === node) → cycle exists; start is that node
* Multiple nodes but no back-pointer → no cycle

## Test snippet (optional)

```js
// Helper to make a cycle at position pos (0-based), or no cycle if pos = -1
function makeCycle(head, pos) {
  if (pos < 0) return head;
  let idx = 0, cur = head, entry = null, tail = null;
  while (cur) {
    if (idx === pos) entry = cur;
    tail = cur;
    cur = cur.next;
    idx++;
  }
  if (tail && entry) tail.next = entry;
  return head;
}

// Example:
const a = new ListNode(1, new ListNode(2, new ListNode(3, new ListNode(4))));
makeCycle(a, 1); // cycle starts at node with value 2
console.log(hasCycle(a));                 // true
console.log(cycleLength(a));              // e.g., 3
console.log(detectCycleStart(a).val);     // 2
```

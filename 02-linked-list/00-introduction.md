# 🔗 Linked List (Template)

A **linked list** stores elements as **nodes** where each node holds a **value** and a **pointer to the next node**. Unlike arrays, elements aren’t contiguous in memory—nodes are chained together.

### 📌 Characteristics of Linked Lists

1. **Structure**: `Node { value, next }` with a `head` (first) and optional `tail` (last).
2. **Operations**: Fast **insert/remove at head** (`O(1)`), linear **search/access** (`O(n)`).
3. **Variants**: Singly (next only) and doubly (prev & next).
4. **Memory**: Extra pointer per node (overhead vs arrays).

### 💚 Best choice

* Frequent **insert/remove at the beginning**.
* Size changes often; **no need for random access** by index.
* Streaming data where you only need **front/back** operations.

### ⚠️ Watch out

* **No O(1) random access** (indexing is `O(n)`).
* Keep `tail` updated to get **O(1) push at end**.
* Avoid losing references when modifying `next`.

---

### 💛 In JavaScript (Node 20+)

```js
// Minimal singly linked list

class ListNode {
  constructor(value, next = null) {
    this.value = value;
    this.next = next;
  }
}

class SinglyLinkedList {
  constructor() {
    this.head = null; // first node
    this.tail = null; // last node (optional but handy)
    this.size = 0;
  }

  // Insert at end: O(1) with tail, else O(n)
  push(value) {
    const node = new ListNode(value);
    if (!this.head) {
      this.head = this.tail = node;
    } else {
      this.tail.next = node;
      this.tail = node;
    }
    this.size++;
    return this;
  }

  // Insert at beginning: O(1)
  unshift(value) {
    const node = new ListNode(value, this.head);
    this.head = node;
    if (!this.tail) this.tail = node;
    this.size++;
    return this;
  }

  // Remove from beginning: O(1)
  shift() {
    if (!this.head) return null;
    const val = this.head.value;
    this.head = this.head.next;
    if (!this.head) this.tail = null;
    this.size--;
    return val;
  }

  // Find first node by predicate: O(n)
  find(pred) {
    let cur = this.head;
    while (cur) {
      if (pred(cur.value)) return cur;
      cur = cur.next;
    }
    return null;
  }

  // Reverse in-place: O(n) time, O(1) space
  reverse() {
    let prev = null, cur = this.head;
    this.tail = this.head;
    while (cur) {
      const next = cur.next;
      cur.next = prev;
      prev = cur;
      cur = next;
    }
    this.head = prev;
    return this;
  }

  // Utility: convert to array (for debugging/tests)
  toArray() {
    const out = [];
    let cur = this.head;
    while (cur) { out.push(cur.value); cur = cur.next; }
    return out;
  }
}

// Quick demo
const list = new SinglyLinkedList();
list.unshift(2).unshift(1).push(3); // 1 -> 2 -> 3
// list.toArray() // [1, 2, 3]
// list.shift();  // removes 1 => 2 -> 3
// list.reverse(); // 3 -> 2
```

---

### ⏱️ Complexity (common ops)

| Operation                 | Time | Space |
| ------------------------- | ---- | ----- |
| `unshift` (add front)     | O(1) | O(1)  |
| `shift` (remove front)    | O(1) | O(1)  |
| `push` (add end, w/ tail) | O(1) | O(1)  |
| `find / access by index`  | O(n) | O(1)  |
| `reverse`                 | O(n) | O(1)  |

---

### 🧩 Mini-walkthrough (reverse passes)

List: `1 -> 2 -> 3 -> null`

* Pass 1: `prev=null, cur=1` → `1.next=null` → `prev=1, cur=2`
* Pass 2: `2.next=1` → `prev=2, cur=3`
* Pass 3: `3.next=2` → `prev=3, cur=null` → **head=3**

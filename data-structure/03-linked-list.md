[README > Data Structure > Linked List](../README.md)

## 🔗 Linked List
A linked list is a linear data structure where elements are stored in nodes, and each node points to the next node in the sequence.

### 📌 Characteristics of Linked Lists
- Linked lists are dynamic in size. They can grow and shrink as needed.
- Each element (node) contains a value and a reference (pointer) to the next node.
- Linked lists can efficiently insert and delete elements without reorganizing the entire structure.

### 🥊 Linked List vs Arrays
- **Memory Allocation**: Arrays use contiguous memory allocation, while linked lists use non-contiguous memory allocation.
- **Size**: Arrays have a fixed size, whereas linked lists can grow and shrink dynamically.
- **Insertion/Deletion**: Linked lists allow for efficient insertion and deletion of elements, while arrays may require shifting elements.
- **Access Time**: Arrays provide O(1) access time for elements, while linked lists provide O(n) access time.

### 💚 Best choice
- Use linked lists when you need efficient insertions and deletions.
- Use arrays when you need fast access to elements by index.
- Consider the trade-offs between memory usage and access speed when choosing between linked lists and arrays.
- Linked lists are often used in scenarios where frequent insertions and deletions occur.
- They can be more memory-efficient than arrays for certain applications.

### 💛 In JavaScript
- JavaScript does not have a built-in linked list data structure, but it can be implemented using objects.
- Linked lists can be singly linked (each node points to the next) or doubly linked (each node points to both the next and previous nodes).

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
  }

  insert(value) {
    const newNode = new Node(value);
    if (!this.head) {
      this.head = newNode;
    } else {
      let current = this.head;
      while (current.next) {
        current = current.next;
      }
      current.next = newNode;
    }
  }
}
```

---
**Resources**
- [DSA Linked Lists](https://www.w3schools.com/dsa/dsa_theory_linkedlists.php)

<br>
<br>

---

by @willaug ❤️

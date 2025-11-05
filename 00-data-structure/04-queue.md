[README > Data Structure > Queue](../README.md)

## ➡️ Queue
A queue is a linear data structure that follows the First In First Out (FIFO) principle. Elements are added to the back (rear) and removed from the front.

### 📌 Characteristics of Queues
- Queues are dynamic in size and can grow and shrink as needed.
- Elements are processed in the order they arrive.
- Queues can efficiently insert and delete elements from both ends.

### 🥊 Queue vs Stacks
- **Order**: Queues follow FIFO, while stacks follow Last In First Out (LIFO).
- **Operations**: Queues support enqueue (add) and dequeue (remove) operations, while stacks support push (add) and pop (remove) operations.
- **Use Cases**: Queues are used in scenarios like scheduling and buffering, while stacks are used in function calls and backtracking.

### 💚 Best choice
- Use queues when you need to process elements in the order they arrive.
- Use stacks when you need to reverse the order of elements or manage function calls.
- Consider the trade-offs between memory usage and access speed when choosing between queues and stacks.

### 💛 In JavaScript
- JavaScript does not have a built-in queue data structure, but it can be implemented using arrays or linked lists.
- Queues can be implemented using the `Array` methods `push()` and `shift()`.

```js
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(item) {
    this.items.push(item);
  }

  dequeue() {
    return this.items.shift();
  }

  isEmpty() {
    return this.items.length === 0;
  }
}
```

---
**Resources**
- [Difference between Queue and Deque (Queue vs. Deque)](https://www.geeksforgeeks.org/dsa/difference-between-queue-and-deque-queue-vs-deque/)

<br>
<br>

---

by @willaug ❤️

[README > Data Structure > Stack](../README.md)

## 🔋 Stack
A stack is a linear data structure that follows the Last In First Out (LIFO) principle. Elements are added to the top and removed from the top.

### 📌 Characteristics of Stacks
- Stacks are dynamic in size and can grow and shrink as needed.
- Elements are processed in the reverse order they arrive.
- Stacks can efficiently insert and delete elements from the top.

### 🥊 Stack vs Queues
- **Order**: Stacks follow LIFO, while queues follow First In First Out (FIFO).
- **Operations**: Stacks support push (add) and pop (remove) operations, while queues support enqueue (add) and dequeue (remove) operations.
- **Use Cases**: Stacks are used in scenarios like function calls and backtracking, while queues are used in scheduling and buffering.

### 💚 Best choice
- Use stacks when you need to reverse the order of elements or manage function calls.
- Use queues when you need to process elements in the order they arrive.
- Consider the trade-offs between memory usage and access speed when choosing between stacks and queues.

### 💛 In JavaScript
- JavaScript does not have a built-in stack data structure, but it can be implemented using arrays or linked lists.
- Stacks can be implemented using the `Array` methods `push()` and `pop()`.

```js
class Stack {
  constructor(maxSize) {
    this.items = [];
    this.maxSize = maxSize;
  }

  push(item) {
    if (!this.isFull()) {
      this.items.push(item);
    } else {
      throw new Error("Stack is full");
    }
  }

  pop() {
    return this.items.pop();
  }

  isEmpty() {
    return this.items.length === 0;
  }

  isFull() {
    return this.items.length === this.maxSize;
  }
}
```

---
**Resources**
- [Stack Data Structure](https://www.geeksforgeeks.org/dsa/stack-data-structure/)

<br>
<br>

---

by @willaug ❤️

- Collisions (when two keys hash to the same index) are handled using techniques like chaining or open addressing.

### 🥊 Hashmap vs Objects
- **Key Types**: Hashmaps can use any data type as a key, while objects only use strings and symbols.
- **Performance**: Hashmaps generally provide better performance for large datasets due to their underlying implementation.
- **Use Cases**: Hashmaps are used for caching, indexing, and fast lookups, while objects are used for simple key-value pairs.

### 💚 Best choice
- Use hashmaps when you need fast lookups and insertions.
- Use objects when you need a simple key-value store with string keys.
- Consider the trade-offs between memory usage and access speed when choosing between hashmaps and objects.

### 💛 In JavaScript
- JavaScript has a built-in `Map` object that implements a hashmap.
- Maps can use any value (including objects) as keys.

```js
const map = new Map();
map.set('key1', 'value1');
map.set('key2', 'value2');
console.log(map.get('key1')); // Output: value1
```

---
**Resources**
- [What is a Hash Map?](https://www.freecodecamp.org/news/what-is-a-hash-map/)

<br>
<br>

---

by @willaug ❤️

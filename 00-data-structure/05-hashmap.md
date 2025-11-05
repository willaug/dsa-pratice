[README > Data Structure > Hashmap](../README.md)

## 🌍 Hashmap
Hashmap is a data structure that implements an associative array abstract data type, a structure that can map keys to values. A hashmap uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.

### 📌 Characteristics of Hashmaps
- Hashmaps provide fast insertion, deletion, and access operations.
- They use a hash function to compute an index into an array of buckets.
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

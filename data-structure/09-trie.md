[README > Data Structure > Trie](../README.md)

## ⁉️ Trie
A trie (pronounced "try") is a specialized tree-like data structure used to store and retrieve keys in a dataset of strings. It is particularly useful for tasks involving prefix matching, autocomplete, and spell checking.

### 📌 Characteristics of Tries
- **Structure**: A trie consists of nodes, where each node represents a single character of a key. The path from the root to a node represents the prefix of the key.
- **Efficiency**: Tries can provide faster search times compared to traditional data structures like binary search trees, especially for prefix-based queries.
- **Space Complexity**: While tries can consume more memory than other data structures due to the storage of multiple pointers, they can be optimized using techniques like path compression.

### 🥊 Trie vs Other Data Structures
- **Trie vs Hash Table**: Tries are more efficient for prefix-based searches, while hash tables offer average-case O(1) time complexity for exact key lookups.
- **Trie vs Binary Search Tree**: Tries can handle a larger set of keys with common prefixes more efficiently than binary search trees, which may become unbalanced.
- **Use Cases**: Tries are commonly used in applications like autocomplete systems, spell checkers, and IP routing.

### 💚 Best choice
- Use tries when you need to perform frequent prefix-based searches or store a large set of strings with common prefixes.
- Consider the trade-offs between memory usage and search efficiency when choosing between tries and other data structures.

### 💛 In JavaScript
- JavaScript does not have a built-in trie data structure, but it can be implemented using objects or classes.
- Tries can be implemented using a `TrieNode` class to represent each node.

```js
class TrieNode {
  constructor() {
    this.children = {};
    this.isEndOfWord = false;
  }
}

class Trie {
  constructor() {
    this.root = new TrieNode();
  }

  insert(word) {
    let currentNode = this.root;
    for (let char of word) {
      if (!currentNode.children[char]) {
        currentNode.children[char] = new TrieNode();
      }
      currentNode = currentNode.children[char];
    }
    currentNode.isEndOfWord = true;
  }

  search(word) {
    let currentNode = this.root;
    for (let char of word) {
      if (!currentNode.children[char]) {
        return false;
      }
      currentNode = currentNode.children[char];
    }
    return currentNode.isEndOfWord;
  }

  startsWith(prefix) {
    let currentNode = this.root;
    for (let char of prefix) {
      if (!currentNode.children[char]) {
        return false;
      }
      currentNode = currentNode.children[char];
    }
    return true;
  }
}
```

---
**Resources**
- [Trie Data Structure](https://www.geeksforgeeks.org/dsa/trie-insert-and-search/)

<br>
<br>

---

by @willaug ❤️

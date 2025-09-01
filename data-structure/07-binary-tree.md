[README > Data Structure > Binary Tree](../README.md)

## 🔋 Binary Tree

A binary tree is a hierarchical data structure in which each node has at most two children, referred to as the left child and the right child. Binary trees are widely used in computer science for various applications, including searching, sorting, and representing hierarchical data.

### 📌 Characteristics of Binary Trees
- **Structure**: Each node contains a value and references to its left and right children.
- **Height**: The height of a binary tree is the length of the longest path from the root to a leaf.
- **Balanced**: A balanced binary tree maintains a height difference of at most one between its left and right subtrees.

### 🥊 Binary Tree vs Binary Search Tree
- **Structure**: Both are tree data structures, but a binary search tree (BST) has an additional property where the left child is less than the parent and the right child is greater.
- **Search Efficiency**: Searching in a BST is more efficient (O(log n) on average) compared to a regular binary tree (O(n)).
- **Use Cases**: Binary trees are used for hierarchical data representation, while BSTs are used for fast data retrieval.


### 💚 Best choice
- Use binary trees when you need to represent hierarchical relationships.
- Use binary search trees when you need fast search, insert, and delete operations.
- Consider the trade-offs between complexity and performance when choosing between binary trees and binary search trees.

### 💛 In JavaScript
- JavaScript does not have a built-in binary tree data structure, but it can be implemented using objects or classes.
- Binary trees can be implemented using a `Node` class to represent each node.

```js
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class BinaryTree {
  constructor() {
    this.root = null;
  }

  insert(value) {
    const newNode = new Node(value);
    if (!this.root) {
      this.root = newNode;
    } else {
      this._insertNode(this.root, newNode);
    }
  }

  _insertNode(node, newNode) {
    if (newNode.value < node.value) {
      if (!node.left) {
        node.left = newNode;
      } else {
        this._insertNode(node.left, newNode);
      }
    } else {
      if (!node.right) {
        node.right = newNode;
      } else {
        this._insertNode(node.right, newNode);
      }
    }
  }
} 
```

---
**Resources**
- [Binary Tree Data Structure](https://www.geeksforgeeks.org/dsa/binary-tree-data-structure/)

<br>
<br>

---

by @willaug ❤️

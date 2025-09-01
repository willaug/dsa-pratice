[README > Data Structure > B-Tree](../README.md)

## 🌲 B-Tree
A B-tree is a self-balancing tree data structure that maintains sorted data and allows for efficient insertion, deletion, and search operations. It is commonly used in databases and file systems to store large amounts of data that cannot fit into memory.

### 📌 Characteristics of B-Trees
- **Structure**: A B-tree consists of nodes, where each node can have multiple children and contains a sorted list of keys. The keys act as separation values that divide the children into subtrees.
- **Balance**: B-trees are balanced, meaning that all leaf nodes are at the same depth. This ensures that the tree remains efficient for search operations.
- **Node Capacity**: Each node in a B-tree can contain a variable number of keys and children, allowing for a more compact representation of data.

### 🥊 B-Tree vs Other Data Structures
- **B-Tree vs Binary Search Tree**: B-trees can have multiple children per node, making them more suitable for disk-based storage systems. Binary search trees are typically used in-memory.
- **B-Tree vs Hash Table**: B-trees maintain sorted data and allow for range queries, while hash tables provide fast exact lookups but do not maintain order.
- **Use Cases**: B-trees are commonly used in databases, file systems, and other applications that require efficient access to large amounts of sorted data.

### 💚 Best choice
- Use B-trees when you need to store large amounts of sorted data and require efficient search, insert, and delete operations.
- Consider the trade-offs between complexity and performance when choosing between B-trees and other data structures.

### 💛 In JavaScript
- JavaScript does not have a built-in B-tree data structure, but it can be implemented using objects or classes.
- B-trees can be implemented using a `BTreeNode` class to represent each node.

```js
class BTreeNode {
  constructor(order) {
    this.keys = [];
    this.children = [];
    this.isLeaf = true;
    this.order = order;
  }
}

class BTree {
  constructor(order) {
    this.root = new BTreeNode(order);
    this.order = order;
  }

  insert(key) {
    const root = this.root;
    if (root.keys.length === 2 * this.order - 1) {
      const newNode = new BTreeNode(this.order);
      this.root = newNode;
      newNode.children.push(root);
      this.splitChild(newNode, 0);
      this.insertNonFull(newNode, key);
    } else {
      this.insertNonFull(root, key);
    }
  }

  splitChild(parent, index) {
    const fullChild = parent.children[index];
    const newChild = new BTreeNode(this.order);
    parent.children.splice(index + 1, 0, newChild);
    parent.keys.splice(index, 1, fullChild.keys[this.order - 1]);
    newChild.keys = fullChild.keys.splice(this.order - 1);
    if (!fullChild.isLeaf) {
      newChild.children = fullChild.children.splice(this.order);
    }
  }

  insertNonFull(node, key) {
    let i = node.keys.length - 1;
    if (node.isLeaf) {
      node.keys.push(null);
      while (i >= 0 && key < node.keys[i]) {
        node.keys[i + 1] = node.keys[i];
        i--;
      }
      node.keys[i + 1] = key;
    } else {
      while (i >= 0 && key < node.keys[i]) {
        i--;
      }
      i++;
      if (node.children[i].keys.length === 2 * this.order - 1) {
        this.splitChild(node, i);
        if (key > node.keys[i]) {
          i++;
        }
      }
      this.insertNonFull(node.children[i], key);
    }
  }
}
```

---
**Resources**
- [Introduction of B Tree](https://www.geeksforgeeks.org/dsa/introduction-of-b-tree-2/)

<br>
<br>

---

by @willaug ❤️

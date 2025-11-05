[README > Data Structure > Graph](../README.md)

## 🗺️ Graph
A graph is a collection of nodes (or vertices) connected by edges. Graphs are used to represent relationships between objects and can be either directed (edges have a direction) or undirected (edges do not have a direction).

### 📌 Characteristics of Graphs
- **Structure**: A graph consists of vertices and edges. Each edge connects two vertices.
- **Weight**: Edges can have weights (costs) associated with them, representing the cost of traversing the edge.
- **Connectivity**: A graph can be connected (there is a path between any two vertices) or disconnected (some vertices are not reachable from others).

### 🥊 Graph vs Tree
- **Structure**: Trees are a type of graph with a hierarchical structure and no cycles. Graphs can have cycles and do not have a strict hierarchy.
- **Traversal**: Graphs can be traversed using algorithms like Depth-First Search (DFS) and Breadth-First Search (BFS), while trees can be traversed using pre-order, in-order, and post-order traversal.
- **Use Cases**: Graphs are used to represent networks, relationships, and connections, while trees are used for hierarchical data representation.

### 💚 Best choice
- Use graphs when you need to represent complex relationships and connections between objects.
- Use trees when you need to represent hierarchical relationships.
- Consider the trade-offs between complexity and performance when choosing between graphs and trees.

### 💛 In JavaScript
- JavaScript does not have a built-in graph data structure, but it can be implemented using objects or classes.
- Graphs can be implemented using an adjacency list or adjacency matrix.

```js
class Graph {
  constructor() {
    this.adjacencyList = {};
  }

  addVertex(vertex) {
    if (!this.adjacencyList[vertex]) {
      this.adjacencyList[vertex] = [];
    }
  }

  addEdge(vertex1, vertex2) {
    this.adjacencyList[vertex1].push(vertex2);
    this.adjacencyList[vertex2].push(vertex1); // For undirected graph
  }

  removeEdge(vertex1, vertex2) {
    this.adjacencyList[vertex1] = this.adjacencyList[vertex1].filter(
      (v) => v !== vertex2
    );
    this.adjacencyList[vertex2] = this.adjacencyList[vertex2].filter(
      (v) => v !== vertex1
    );
  }

  removeVertex(vertex) {
    while (this.adjacencyList[vertex].length) {
      const adjacentVertex = this.adjacencyList[vertex].pop();
      this.removeEdge(vertex, adjacentVertex);
    }
    delete this.adjacencyList[vertex];
  }
}
```

---
**Resources**
- [Graph Algorithms](https://www.geeksforgeeks.org/dsa/graph-data-structure-and-algorithms/)

<br>
<br>

---

by @willaug ❤️

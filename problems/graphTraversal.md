# Graph Traversal

## Solution

```js
/**
 * Performs Depth-First Search (DFS) on a graph starting from a given node.
 *
 * @param {Object} graph - The graph represented as an adjacency list.
 * @param {string} start - The starting node for DFS.
 * @return {string[]} - An array representing the order in which nodes are visited.
 */
function dfs(graph, start) {
  const visited = new Set();
  const result = [];

  /**
   * Helper function for recursive DFS.
   *
   * @param {string} node - The current node being visited.
   */
  function dfsRecursive(node) {
    // If the node has already been visited, skip it.
    if (visited.has(node)) return;

    // Mark the node as visited and add it to the result.
    visited.add(node);
    result.push(node);

    // Recur for all unvisited neighbors.
    for (const neighbor of graph[node]) {
      dfsRecursive(neighbor);
    }
  }

  dfsRecursive(start);
  return result;
}

/**
 * Performs Breadth-First Search (BFS) on a graph starting from a given node.
 *
 * @param {Object} graph - The graph represented as an adjacency list.
 * @param {string} start - The starting node for BFS.
 * @return {string[]} - An array representing the order in which nodes are visited.
 */
function bfs(graph, start) {
  const visited = new Set();
  const queue = [start];
  const result = [];

  // Continue until there are no more nodes to visit.
  while (queue.length > 0) {
    const node = queue.shift();

    // If the node has not been visited, process it.
    if (!visited.has(node)) {
      visited.add(node);
      result.push(node);

      // Enqueue all unvisited neighbors.
      for (const neighbor of graph[node]) {
        if (!visited.has(neighbor)) {
          queue.push(neighbor);
        }
      }
    }
  }
  return result;
}

const graph = {
  A: ["B", "C"],
  B: ["A", "D", "E"],
  C: ["A", "F"],
  D: ["B"],
  E: ["B", "F"],
  F: ["C", "E"],
};

const startNode = "A";

const dfsResult = dfs(graph, startNode);
const bfsResult = bfs(graph, startNode);

console.log("DFS Traversal Order:", dfsResult); // Output: [ 'A', 'B', 'D', 'E', 'F', 'C' ]
console.log("BFS Traversal Order:", bfsResult); // Output: [ 'A', 'B', 'C', 'D', 'E', 'F' ]
```

## Explanation

1. **Graph Representation:** the graph is represented as an object where each key is a node (e.g., `'A'`) and its value is an array of neighbor nodes (e.g., `['B', 'C']`).
2. **Depth-First Search (DFS):**
   - A recursive helper function `dfsRecursive` is used to traverse the graph.
   - A `Set` named `visited` keeps track of nodes that have been visited to avoid cycles.
   - Each time a node is visited, it is added to the `result` array.
   - The function recursively visits each unvisited neighbor.
3. **Breadth-First Search (BFS):**
   - A queue (implemented as an array) is used to traverse the graph level by level.
   - Nodes are dequeued, and if they haven’t been visited, they are processed (added to `visited` and `result`).
   - All unvisited neighbors of the current node are enqueued for later processing.

## Complexity

- **Time:** O(V+E)
- **Memory:** O(V)

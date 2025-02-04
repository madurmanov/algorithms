# Deep-First Search

Deep-First Search (DFS) is an algorithm used for traversing or searching in graphs and trees. It works by exploring as far as possible along each branch before backtracking.

## Actions

1. Choose a starting node.
2. Mark the node as visited.
3. Recursively visit each unvisited neighbor of the chosen node.
4. If all neighbors are visited, backtrack to the previous node and repeat for any remaining unvisited neighbors.
5. Continue until all nodes have been visited.

## Complexity

- **Best Case: Ω(1)** — the element is found at the first position.
- **Average Case: Θ(V+E)** — where V is the number of vertices and E is the number of edges in the graph.
- **Worst Case: O(V+E)** — when the algorithm must visit all nodes and edges of the graph.
- **Memory: O(V)** — in the worst case, the recursion stack (or the additional data structure for tracking visited nodes) may hold up to V nodes.

## Advantages

- **Memory Efficiency:** — uses memory proportional to the number of vertices.
- **Path Finding:** — DFS can be easily modified to track paths and detect cycles.

## Disadvantages

- **Shortest Path:** — the algorithm does not guarantee the shortest path in unweighted graphs.
- **Can Get Stuck:** — in graphs with cycles, DFS may require additional mechanisms (e.g., marking visited nodes) to avoid infinite loops.
- **Stack Overflow Risk:** — in very deep or large graphs, recursive DFS can lead to a stack overflow if not implemented iteratively.

## Use Cases

- **Graph Traversal:** — used to traverse all nodes in a graph.
- **Path Finding:** — applicable for finding paths in mazes or graphs.
- **Cycle Detection:** — useful for detecting cycles in graphs.
- **Topological Sorting:** — DFS is a basis for topological sorting in directed acyclic graphs (DAGs).
- **Solving Puzzles:** — applied in algorithms for solving puzzles that require exploring possible paths.

## Example Code

```js
const graph = {
  A: ["B", "C"],
  B: ["D", "E"],
  C: ["F"],
  D: [],
  E: ["F"],
  F: [],
};

function dfs(node, visited = new Set()) {
  if (visited.has(node)) {
    return;
  }

  visited.add(node);

  for (let neighbor of graph[node]) {
    dfs(neighbor, visited);
  }

  return visited;
}

dfs("A").forEach((value) => console.log(value)); // Output: A, B, D, E, F, C
```

# Breadth-First Search

Breadth-First Search (BFS) is an algorithm for traversing or searching in graphs or trees that explores all nodes at the present depth level before moving on to nodes at the next depth level.

## Actions

1. Enqueue the starting node and mark it as visited.
2. While the queue is not empty, dequeue a node from the front of the queue.
3. For each neighbor of the dequeued node, if the neighbor has not been visited, mark it as visited and enqueue it.
4. Continue the process until the queue is empty, thus traversing the graph level by level.

## Complexity

- **Best Case: Ω(1)** — the element is found at the first position.
- **Average Case: Θ(V+E)** — where V is the number of vertices and E is the number of edges in the graph.
- **Worst Case: O(V+E)** — when the algorithm must visit all nodes and edges of the graph.
- **Memory: O(V)** — in the worst case, the recursion stack (or the additional data structure for queue and tracking visited nodes) may hold up to V nodes.

## Advantages

- **Shortest Path:** — BFS finds the shortest path in unweighted graphs.
- **Level Order Traversal:** — it naturally organizes the traversal of the graph level by level.

## Disadvantages

- **Memory Efficiency:** — BFS can use a lot of memory when processing wide graphs because it needs to store all nodes at the current level in the queue.
- **Not Suitable for Deep Graphs:** — in graphs with a great depth, the algorithm might be less memory-efficient than DFS.

## Use Cases

- **Shortest Path in Unweighted Graphs:** — used for finding the shortest path in graphs without weights.
- **Level Order Traversal in Trees:** — applied to traverse trees level by level.
- **Web Crawling:** — useful for crawling web pages where pages at one level are processed before moving on to the next.
- **Networking:** — used in routing and network protocols to discover nearby nodes.

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

function bfs(start) {
  const queue = [start];
  const visited = new Set([start]);

  while (queue.length > 0) {
    const node = queue.shift();
    console.log(node);

    for (let neighbor of graph[node]) {
      if (!visited.has(neighbor)) {
        visited.add(neighbor);
        queue.push(neighbor);
      }
    }
  }
}

dfs("A"); // Output: A, B, C, D, E, F
```

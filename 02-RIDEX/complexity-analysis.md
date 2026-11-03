# RIDEX – Time and Space Complexity Analysis

## 1. Introduction

Algorithmic efficiency is an important consideration in ride-booking systems.

RIDEX uses different data structures and algorithms to support driver retrieval, matching and shortest-path calculation.

This document analyses the expected time and space complexity of the major operations.

## 2. Complexity Notation

Let:

- n = Number of drivers.
- V = Number of graph vertices.
- E = Number of graph edges.
- k = Number of eligible drivers after compatibility filtering.

## 3. Driver Lookup – unordered_map

RIDEX uses an unordered_map to retrieve drivers using their identifiers.

| Operation | Average Time Complexity | Worst Case |
|---|---|---|
| Insertion | O(1) | O(n) |
| Lookup | O(1) | O(n) |
| Deletion | O(1) | O(n) |

### Why is it useful?

A hash table provides average constant-time lookup.

This is useful when the matching engine needs to retrieve a driver using an identifier rather than searching through every driver.

## 4. Vehicle Compatibility Filtering

Suppose the system examines n candidate drivers.

If each driver's vehicle compatibility is checked once, the complexity is:

**Time Complexity: O(n)**

The filtering process uses O(k) space if it stores the eligible candidates separately.

Here, k represents the number of compatible drivers.

## 5. Driver Matching and Priority Queue

Suppose k compatible drivers are inserted into a priority queue.

| Operation | Time Complexity |
|---|---|
| Insert one candidate | O(log k) |
| Insert k candidates | O(k log k) |
| Retrieve highest-priority candidate | O(1) |
| Remove highest-priority candidate | O(log k) |

The priority queue requires O(k) space to store all eligible candidates.

If scoring each candidate takes O(1), calculating all k scores takes O(k).

Therefore, building the priority queue through individual insertions takes O(k log k) overall.

## 6. Graph Representation – Adjacency List

For a graph containing V vertices and E edges:

**Space Complexity: O(V + E)**

An adjacency list stores each vertex and its connected edges.

This is useful for sparse graphs where storing a complete V × V matrix would waste memory.

## 7. Dijkstra's Algorithm

RIDEX uses Dijkstra's algorithm with an adjacency list and min-heap.

The commonly stated time complexity for this implementation is:

\[
O((V+E)\log V)
\]

### Why?

1. Vertices are processed using a min-heap.
2. Heap operations take logarithmic time.
3. Edges are examined during relaxation.
4. Distance values are updated when shorter paths are discovered.

For a standard implementation using a binary heap with lazy duplicate entries, the complexity is commonly expressed as:

\[
O((V+E)\log V)
\]

The distance array and graph require:

\[
O(V+E)
\]

space, with the heap requiring up to O(E) entries in the lazy-duplicate implementation.

## 8. Overall Complexity Summary

| Operation | Time Complexity | Space Complexity |
|---|---|---|
| Driver lookup | O(1) average | O(n) for stored drivers |
| Compatibility filtering | O(n) | O(k) for stored candidates |
| Candidate scoring | O(k) | O(1) auxiliary per candidate |
| Priority queue insertion | O(k log k) | O(k) |
| Priority retrieval | O(1) | O(1) |
| Priority removal | O(log k) | O(k) queue storage |
| Adjacency-list graph | O(V + E) construction | O(V + E) |
| Dijkstra's algorithm | O((V + E) log V) | O(V + E) |

## 9. Why Not Use Other Approaches?

### Driver Lookup: Vector vs unordered_map

A vector requires O(n) time for a linear search by driver ID.

An unordered_map provides O(1) average lookup.

Therefore, unordered_map is more suitable for repeated identifier-based retrieval.

### Driver Selection: Complete Sorting vs Priority Queue

Sorting k candidates requires O(k log k) time.

A priority queue also requires O(k log k) time to build through individual insertions, but it is useful when candidates are consumed in priority order without requiring a fully sorted collection.

If only the best driver is required and all candidates are already available, a linear scan can be O(k), so a priority queue is not automatically faster for every selection workload.

### Graph Storage: Adjacency Matrix vs Adjacency List

An adjacency matrix requires O(V²) space.

An adjacency list requires O(V + E) space.

For sparse transportation graphs, an adjacency list is generally more memory-efficient.

## 10. Performance Considerations

The choice of data structures affects the performance and scalability of a ride-booking engine.

Some important considerations include:

- Use hash-based lookup for repeated driver retrieval.
- Filter incompatible candidates before ranking.
- Use priority queues when priority-based retrieval is needed.
- Use adjacency lists for sparse transportation graphs.
- Use an appropriate shortest-path algorithm for the graph's weight constraints.

## 11. Conclusion

RIDEX demonstrates the importance of selecting data structures and algorithms according to the requirements of individual operations.

Rather than using one approach for every problem, the system combines hash tables, priority queues and graph algorithms to support different parts of the ride-booking workflow efficiently.

Understanding these complexity trade-offs is essential when designing maintainable and efficient software systems.

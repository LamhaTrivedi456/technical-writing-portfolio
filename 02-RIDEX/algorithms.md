# RIDEX – Algorithms and Data Structures

## 1. Introduction

RIDEX uses data structures and graph algorithms to solve two important problems:

1. Finding a suitable driver for a ride request.
2. Calculating the shortest path between locations.

The project combines hash-based lookup, priority-based selection and graph traversal techniques to support these operations.

## 2. Driver Lookup Using unordered_map

An `unordered_map` stores key-value pairs using a hash table.

In RIDEX, it is used for efficient driver lookup.

For example:

```cpp
unordered_map<int, Driver> drivers;
```

Here:
- The key represents a driver ID.
- The value represents the corresponding Driver object.

### Example

```cpp
auto it = drivers.find(driverId);

if (it != drivers.end()) {
    Driver selectedDriver = it->second;
}
```

### Why unordered_map?

A vector would require searching through elements to locate a particular driver by ID.

An `unordered_map` provides average O(1) lookup, making it useful when retrieving drivers using unique identifiers.

Its worst-case lookup complexity can be O(n).

## 3. Vehicle Compatibility Filtering

Before selecting a driver, the system checks whether the associated vehicle satisfies the ride requirements.

For example:

A rider requests a particular vehicle category.

The matching engine considers only drivers whose vehicles meet the requested category.

This reduces the number of candidates that need to be evaluated.

### Why filter first?

- Avoids considering incompatible vehicles.
- Reduces unnecessary scoring operations.
- Makes driver selection more relevant.
- Separates eligibility checks from ranking logic.

## 4. Driver Matching Using Rating-Distance Scoring

After compatibility filtering, eligible drivers are evaluated using a rating-distance-based score.

The two important factors are:

- Driver rating.
- Distance from the pickup location.

A suitable matching strategy combines these factors to determine driver priority.

The exact scoring formula and weighting depend on the implementation.

For example, a hypothetical scoring approach could be:

```text
Higher rating + Shorter distance
              |
              v
       Better Priority
```

The system uses the matching score to prioritize suitable drivers.

## 5. Priority Queue for Driver Selection

A priority queue is a data structure that provides efficient access to the highest-priority or lowest-priority element, depending on its comparator.

RIDEX uses a priority queue to organize driver candidates according to their matching score.

### Conceptual Example

| Driver | Rating | Pickup Distance |
|---|---:|---:|
| Driver A | 4.8 | 3 km |
| Driver B | 4.5 | 1 km |
| Driver C | 4.9 | 7 km |

The matching strategy evaluates these attributes to assign priority.

The priority queue helps retrieve the preferred candidate without sorting the entire candidate collection after every selection.

### Why priority_queue?

- Efficient insertion.
- Efficient access to the highest-priority element.
- Useful for ranking candidate drivers.
- Avoids requiring a complete sort for every selection.

The exact ordering depends on the priority-queue comparator and score definition.

## 6. Graph Representation Using Adjacency Lists

Ride-booking systems involve locations connected through roads or routes.

A graph provides a suitable representation.

A graph contains:

- Vertices: Locations.
- Edges: Connections between locations.
- Weights: Distance or travel cost.

RIDEX uses an adjacency-list representation.

### Example

Consider three locations:

```text
       A
      / \
     4   2
    /     \
   B---1---C
```

Adjacency-list representation:

```text
A -> (B, 4), (C, 2)
B -> (A, 4), (C, 1)
C -> (A, 2), (B, 1)
```

### Why an Adjacency List?

An adjacency list stores only the connections that exist.

For sparse graphs, it is generally more space-efficient than an adjacency matrix.

Its space complexity is O(V + E), where V is the number of vertices and E is the number of edges.

## 7. Dijkstra's Shortest-Path Algorithm

Dijkstra's algorithm calculates shortest paths from a source vertex to other reachable vertices in a weighted graph with non-negative edge weights.

RIDEX uses this algorithm to support route calculation.

### How It Works

1. Assign distance 0 to the source vertex.
2. Assign infinity to all other vertices.
3. Insert the source into a min-heap.
4. Extract the vertex with the smallest known distance.
5. Examine its neighbouring vertices.
6. Update distances when a shorter route is found.
7. Repeat until the priority queue is empty or the required destination is finalized.

### Example

Consider the following graph:

```text
       A
      / \
     4   2
    /     \
   B---1---C
```

Suppose the source is A and the destination is B.

Possible routes:

- Direct route: A → B = 4
- Alternative route: A → C → B = 2 + 1 = 3

Dijkstra's algorithm identifies:

```text
Shortest Path: A → C → B
Total Cost: 3
```

### Why Use a Min-Heap?

A min-heap allows the algorithm to efficiently retrieve the vertex with the smallest tentative distance.

This avoids repeatedly scanning all vertices to find the next vertex to process.

## 8. Overall Algorithm Pipeline

```text
          Ride Request
                |
                v
         Driver Lookup
          unordered_map
                |
                v
     Vehicle Compatibility
             Filter
                |
                v
       Matching Score
                |
                v
        priority_queue
                |
                v
       Driver Selection
                |
                v
       Route Calculation
                |
                v
      Dijkstra's Algorithm
                |
                v
        Booking Workflow
```

## 9. Algorithm Selection: Why These Data Structures?

| Requirement | Selected Approach | Reason |
|---|---|---|
| Driver lookup | unordered_map | Average O(1) lookup |
| Driver selection | priority_queue | Efficient priority retrieval |
| Location connections | Adjacency List | Efficient graph storage |
| Shortest path | Dijkstra | Weighted shortest-path calculation |
| Matching flexibility | Strategy Pattern | Separates selection logic |

## 10. Conclusion

RIDEX demonstrates how multiple data structures and algorithms can work together to solve a practical engineering problem.

The combination of hash-based lookup, compatibility filtering, priority-based selection and graph-based shortest-path calculation creates a structured approach to driver matching and route computation.

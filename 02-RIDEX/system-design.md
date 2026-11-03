# RIDEX – System Design

## 1. Introduction

RIDEX is a C++ ride-booking and driver-matching engine designed around modular software components.

The system focuses on managing ride requests, identifying compatible drivers, selecting suitable drivers and calculating shortest paths between locations.

The design combines object-oriented programming, reusable matching strategies and efficient data structures.

## 2. Design Objectives

The main design objectives are:

1. **Modularity:** Separate rider, driver, vehicle, booking and matching responsibilities.
2. **Extensibility:** Allow matching strategies to evolve independently.
3. **Efficiency:** Use appropriate data structures for driver lookup and selection.
4. **Maintainability:** Organize the application into reusable components.
5. **Algorithmic Efficiency:** Use graph algorithms to calculate shortest paths.

## 3. Main System Components

### 3.1 Rider Management

Responsible for representing riders and their ride requests.

Typical responsibilities:
- Maintain rider information.
- Submit ride requests.
- Provide pickup and destination details.

### 3.2 Driver Management

Represents drivers participating in the ride-booking system.

Typical responsibilities:
- Maintain driver information.
- Track driver-related attributes.
- Support driver lookup.
- Provide information required for matching.

### 3.3 Vehicle Management

Represents vehicles associated with drivers.

The system checks vehicle compatibility before considering a driver for a particular ride request.

This prevents assigning an unsuitable vehicle to a requested ride category.

### 3.4 Booking Management

Coordinates the ride-booking workflow.

Responsibilities include:
- Receiving ride requests.
- Coordinating driver matching.
- Managing booking-related information.
- Supporting payment-related operations.

### 3.5 Driver Matching Engine

The matching engine identifies suitable drivers for a ride request.

Its responsibilities include:

1. Retrieve candidate drivers.
2. Filter drivers based on vehicle compatibility.
3. Evaluate eligible drivers using a rating-distance-based score.
4. Use a priority queue to select a preferred candidate.

### 3.6 Route Calculation Module

The route calculation component models locations as vertices and connections as weighted edges.

Dijkstra's algorithm calculates shortest paths using an adjacency-list graph representation and a min-heap.

## 4. Data Structure Selection

Different data structures are used for different system requirements.

| Data Structure | Purpose | Reason |
|---|---|---|
| unordered_map | Driver lookup | O(1) average-case lookup |
| priority_queue | Driver selection | Efficient priority-based retrieval |
| Adjacency List | Graph representation | Stores connected locations efficiently |
| Min-Heap | Shortest-path processing | Efficiently retrieves the minimum-distance vertex |

## 5. Design Pattern

### Strategy Design Pattern

The Strategy Pattern separates driver-matching behaviour from the booking workflow.

Instead of placing all matching logic inside one large function, matching behaviour can be represented through separate interchangeable strategies.

For example, possible strategy variations could include:

- Rating-focused selection.
- Distance-focused selection.
- Combined rating-distance selection.

These are examples of potential strategy variations; only the strategies actually implemented should be listed as existing project features.

### Benefits

- Reduces tight coupling.
- Improves code organization.
- Supports future matching strategies.
- Makes the matching component easier to maintain.
- Follows the Open/Closed Principle when new strategies can be introduced without modifying existing client code.

## 6. Driver Matching Design

Driver matching follows a filtering and ranking approach.

### Stage 1: Candidate Retrieval

Retrieve available driver information using the driver's identifier or lookup structure.

### Stage 2: Compatibility Filtering

Remove drivers whose vehicles do not satisfy the ride requirements.

### Stage 3: Score Evaluation

Evaluate eligible drivers using the project's rating-distance-based scoring logic.

### Stage 4: Priority-Based Selection

Use a priority queue to organize eligible candidates according to their matching priority.

### Stage 5: Assignment

Select the preferred candidate and continue the booking workflow.

## 7. Route Calculation Design

The transportation network is represented as a weighted graph.

- Vertices represent locations.
- Edges represent connections between locations.
- Edge weights represent travel costs or distances.

Dijkstra's algorithm finds the shortest path from a source location to reachable destinations when edge weights are non-negative.

An adjacency list stores graph connections, while a min-heap helps retrieve the next vertex with the smallest known distance.

## 8. Design Trade-offs

| Design Decision | Advantage | Consideration |
|---|---|---|
| unordered_map | Fast average-case lookup | Does not maintain sorted order |
| priority_queue | Efficient priority retrieval | Does not provide direct arbitrary element updates |
| Adjacency List | Space-efficient for sparse graphs | Neighbour lookup requires scanning a vertex's adjacency list |
| Strategy Pattern | Flexible matching logic | Introduces additional abstractions |
| Dijkstra's Algorithm | Efficient shortest-path calculation | Requires non-negative edge weights |

## 9. Future Design Improvements

Potential improvements include:

- Geospatial indexing for nearby-driver retrieval.
- Real-time driver availability management.
- Traffic-aware routing.
- Concurrent booking request handling.
- More advanced matching strategies.
- Improved monitoring and logging.

## 10. Conclusion

RIDEX demonstrates how modular software design, appropriate data structure selection and algorithmic problem-solving can be combined to build a ride-booking engine.

The separation of booking, matching and route-calculation responsibilities makes the system easier to understand and extend.

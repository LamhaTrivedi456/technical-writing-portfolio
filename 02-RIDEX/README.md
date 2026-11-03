# RIDEX – Ride Booking and Driver Matching Engine

### A C++ Based Ride Booking and Driver Assignment System

**Developed by Lamha Trivedi**

## 1. Overview

RIDEX is a C++ ride-booking and driver-matching engine designed to demonstrate how data structures, object-oriented programming and graph algorithms can be applied to a real-world transportation problem.

The system models the core operations of a ride-booking platform, including riders, drivers, vehicles, ride requests, driver assignment and payment-related workflows.

A key part of RIDEX is its driver-matching mechanism, which identifies suitable drivers using vehicle compatibility and a rating-distance-based selection score.

The project also uses graph algorithms to calculate shortest paths between locations, helping model route-based transportation decisions.

## 2. Key Features

- Modular ride-booking engine built using C++.
- Object-oriented design using classes, composition and polymorphism.
- Strategy Design Pattern for flexible matching strategies.
- Driver assignment using rating-distance-based scoring.
- Vehicle compatibility filtering.
- `unordered_map` for efficient average-case driver lookup.
- `priority_queue` for selecting suitable drivers.
- Dijkstra's algorithm for shortest-path calculation.
- Adjacency-list graph representation.
- JSON-based input/output workflow.
- Booking, matching and payment-related operations.

## 3. How RIDEX Works

The general workflow follows these stages:

1. A rider submits a ride request.
2. The system receives the pickup and destination information.
3. Available drivers are retrieved.
4. Drivers are filtered according to vehicle compatibility.
5. Suitable drivers are evaluated using the matching score.
6. A priority queue helps select a preferred driver.
7. Dijkstra's algorithm can be used to calculate the shortest route in the weighted graph.
8. The ride assignment and booking information are processed.
9. Payment-related operations are handled as part of the booking workflow.

## 4. Technical Stack

| Category | Technology |
|---|---|
| Programming Language | C++ |
| Object-Oriented Design | OOP |
| Data Structures | STL, unordered_map, priority_queue |
| Graph Representation | Adjacency List |
| Graph Algorithm | Dijkstra's Algorithm |
| Design Pattern | Strategy Pattern |
| Data Exchange | JSON-based I/O |

## 5. Core Engineering Concepts

### Object-Oriented Programming

The project uses object-oriented principles to organize riders, drivers, vehicles and booking-related responsibilities.

Concepts include:

- Encapsulation
- Composition
- Inheritance
- Polymorphism
- Modular class design

### Strategy Design Pattern

The Strategy Pattern allows matching behaviour to be separated from the main booking workflow.

This makes it easier to introduce or modify driver-selection strategies without tightly coupling them to the booking logic.

### Driver Matching

The matching engine uses:

- Vehicle compatibility filtering.
- Driver information lookup.
- Rating-distance-based scoring.
- Priority queues for driver selection.

### Graph Algorithms

Dijkstra's algorithm is used for shortest-path calculation on a weighted graph represented using adjacency lists.

## 6. System Workflow

```text
        Rider Request
              |
              v
       Booking System
              |
              v
      Driver Information
              |
              v
   Vehicle Compatibility Filter
              |
              v
      Matching Strategy
              |
              v
     Priority Queue Selection
              |
              v
       Driver Assignment
              |
              v
       Booking Workflow
              |
              v
      Payment Processing
```

## 7. Documentation

The following documents explain the engineering and implementation concepts behind RIDEX.

| Document | Description |
|---|---|
| [System Design](./system-design.md) | Explains component responsibilities and design decisions. |
| [Architecture](./architecture.md) | Describes the architecture and system workflows. |
| [Algorithms](./algorithms.md) | Explains driver matching, priority queues and Dijkstra's algorithm. |
| [Complexity Analysis](./complexity-analysis.md) | Analyses the time and space complexity of core operations. |
| [Technical Blog](./technical-blog.md) | Explains how driver matching can be implemented using data structures and algorithms. |

## 8. Engineering Challenges

Some of the important engineering problems addressed by RIDEX include:

- Organizing different entities using object-oriented design.
- Finding suitable drivers efficiently.
- Filtering drivers according to vehicle requirements.
- Balancing driver ratings and distance during selection.
- Representing locations and routes using graph structures.
- Keeping matching logic modular and extensible.

## 9. Future Improvements

Potential enhancements include:

- Real-time driver location tracking.
- Dynamic traffic-aware route calculation.
- Geospatial indexing for nearby-driver searches.
- Concurrent ride-request processing.
- Advanced driver-matching strategies.
- Live booking status updates.
- Improved payment integration.

## 10. About the Developer

**Lamha Trivedi**

Computer Science Engineering Student | Software Developer | GenAI Enthusiast

I enjoy applying data structures, algorithms and software design principles to practical engineering problems.

RIDEX reflects my interest in building modular software systems and understanding how algorithmic decisions influence application performance.

- [LinkedIn](https://linkedin.com/in/lamha-trivedi)
- [GitHub](https://github.com/LamhaTrivedi456)
- Email: lamhatrivedi546@gmail.com

---

*Designing efficient systems by combining algorithms, data structures and practical software engineering.*

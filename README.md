# Floyd–Warshall Algorithm with Path Reconstruction (C++)

## Overview
This project provides an academic implementation of the **Floyd–Warshall algorithm**
for solving the **All-Pairs Shortest Path (APSP)** problem in a weighted directed graph.
In addition to computing the shortest distances between all pairs of vertices,
the program reconstructs and prints the **actual shortest paths** between vertices.

The implementation is written in **C++** and uses dynamic memory allocation
to manage distance and path reconstruction matrices.

---

## Algorithm Description
The **Floyd–Warshall algorithm** is a classical dynamic programming technique
used to find the shortest paths between all pairs of vertices in a graph.
The algorithm iteratively considers each vertex as an intermediate point
and updates the shortest known distances accordingly.

### Time and Space Complexity
- **Time Complexity:** \(O(V^3)\)
- **Space Complexity:** \(O(V^2)\)

where \(V\) denotes the number of vertices in the graph.

---

## Path Reconstruction
To reconstruct the actual shortest paths, an auxiliary matrix called `next` is used.

- `next[i][j]` stores the **next vertex to visit after vertex `i`**
  when following the shortest path from `i` to `j`.
- If no path exists between two vertices, `next[i][j]` is set to `-1`.

### Rationale for Using `next[i][k]`
During the relaxation step of the Floyd–Warshall algorithm, when a shorter path
from vertex `i` to vertex `j` through an intermediate vertex `k` is found,
the following update is applied:

next[i][j] = next[i][k]

This is because the first vertex after `i` on the shortest path from `i` to `k`
is also the first vertex on the shortest path from `i` to `j`
when the path passes through `k`.

Preserving this information guarantees correct and complete reconstruction
of the shortest path.


## Input Format
1. An integer `V` representing the number of vertices
2. A `V × V` adjacency matrix
---
### Input Rules
- `0` on the main diagonal (distance from a vertex to itself)
- Positive integer → weight of an edge
- `-1` → no direct edge between vertices

### Example Input
4
0 5 -1 10
-1 0 3 -1
-1 -1 0 1
-1 -1 -1 0

---

## Output Description
The program outputs:
1. The shortest distance matrix
2. The reconstructed shortest paths between all vertex pairs

### Example Output (Partial)
Path from 0 to 3: 0 -> 1 -> 2 -> 3
---
This output indicates that the shortest path from vertex `0` to vertex `3`
passes through vertices `1` and `2`.

## Implementation Details
- Infinite distances are represented using a large constant (`INF`)
- Dynamic memory allocation (`new` / `delete`) is used for matrix management
- The implementation correctly handles disconnected vertices
- Paths are printed in a readable sequential format

---

## Build and Run
Compile and execute the program using a C++ compiler such as `g++`
```bash
g++ src/floyd_warshall.cpp -o floyd
./floyd
```

## Applications
- Network routing and communication systems
- Transportation and traffic analysis
- Graph-based optimization problems
- Educational demonstrations of dynamic programming algorithms

---

## Author
Abtin Fooladkhah




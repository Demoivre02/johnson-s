# Johnson's Algorithm for All-Pairs Shortest Path

This Python code implements Johnson's algorithm for solving the all-pairs shortest path problem in a graph. The algorithm incorporates a reweighting technique that transforms the input graph, making it suitable for the application of Dijkstra's algorithm for each vertex.

## Overview

Johnson's algorithm consists of the following steps:

1. **Graph Reweighting:** Add an extra node to the graph and apply the Bellman-Ford algorithm to calculate the shortest paths from the extra node to all other nodes. Reweight the edges accordingly.

2. **Dijkstra's Algorithm:** Apply Dijkstra's algorithm for each vertex in the reweighted graph to find the shortest paths to all other nodes.

3. **Reverse Reweighting:** Reverse the reweighting process to obtain the final shortest paths.

## Usage

The code includes a sample graph defined within the script. However, the code can also read a graph from a file using the `read_graph` function (currently commented out).

```python
if __name__ == "__main__":
    graph_new = deepcopy(graph)
    t1 = datetime.utcnow()
    final_distances = johnsons(graph_new)
    if not final_distances:
        print("Negative cycle")
    else:
        print(compute_min(final_distances))
    print(datetime.utcnow() - t1)
```

Replace the provided graph with your graph or uncomment the `read_graph` function to read a graph from a file.

## File Input

To read a graph from a file, use the `read_graph` function. The file should contain lines with three integers separated by spaces representing edges and their weights:

```
1 2 3
2 3 5
3 1 -2
```

## Note

This algorithm is efficient for sparse graphs and can handle graphs with negative weights and negative cycles.

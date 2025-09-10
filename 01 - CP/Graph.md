## About bipartite graph

A graph without an odd cycle is called a bipartite graph. This is equivalent to:

- one can paint vertices in two colors so that no edge connects vertices of the same color.

For such a graph, one can partition the vertex set into two sets by the color. These set are called partite sets (or simply parts).  
The partite sets of a connected bipartite graph are unique, and they can be found by performing DFS (Depth-First Search) or BFS (Breadth-First search) from an arbitrary vertex.
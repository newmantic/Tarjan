# Tarjan


Tarjan's Algorithm is an algorithm for finding Strongly Connected Components (SCCs). A strongly connected component (SCC) of a directed graph is a maximal subgraph where every vertex is reachable from every other vertex in that subgraph.
Input: A directed graph G = (V, E) with vertices V and edges E.
Output: A list of all SCCs in the graph.


Initialization:
Create an empty stack to keep track of the vertices in the current path of the depth-first search (DFS).
Maintain an array index to assign unique indexes to each vertex when it is first visited.
Maintain an array lowlink to track the lowest index reachable from a vertex.

Initialize current_index to 0 to assign indexes.
For each vertex v that has not been visited:
Set index[v] = current_index and lowlink[v] = current_index, then increment current_index.
Push v onto the stack.

For each adjacent vertex w of v:

If w has not been visited:
Recursively call the DFS function on w.

Update lowlink[v] as follows:
lowlink[v] = min(lowlink[v], lowlink[w])
If w is in the stack (i.e., w is part of the current path):

Update lowlink[v]:
lowlink[v] = min(lowlink[v], index[w])

Identify SCCs:
After exploring all neighbors of v, check if lowlink[v] equals index[v]:
If true, v is a root of an SCC:
Pop vertices from the stack until v is reached, forming an SCC.
Collect the popped vertices as one SCC.

Repeat:
Repeat the above steps for all vertices in the graph.

Time Complexity:
The time complexity of Tarjan’s algorithm is O(V + E), where V is the number of vertices and E is the number of edges, because each vertex and edge is processed at most once.

The algorithm is efficient and uses a single depth-first search.
The stack is crucial for maintaining the current path and helping to identify SCCs.

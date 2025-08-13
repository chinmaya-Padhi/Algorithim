## Spanning Tree (ST)
- A connected subgraph T(V,E') of graph G(V,E) is said to be spanning tree if :
    - 'T' should be contain all vertices og "G' .
    - 'S' shouuld contain ('V'-1) edges .
![image](img1.jpg)
 - **Note** Given a graph having 'n' vertices & 'e' edges of G(V,E) , then maximum no of spanning trees possible is **(n^n-2)** [ **solution space** ] 
![image](img2.jpg)
### KRUSKAL'S ALGO:
- construct min heap with 'e' edges.
- Take one by one edges add in spanning tree ( cycle should not be created )
      - Best case (n-1) edges
      - worst case 'e' edges
![image](img3.jpg)
## Pseudocode for Kruskal’s Algorithm (Heap Version)
Algorithm Kruskal(E, cost, n):
1. Construct a heap from all edges using Heapify based on their costs.
2. for each vertex i from 1 to n:
       parent[i] := -1      // Initialize disjoint set
3. edge_count := 0
4. mincost := 0.0
5. while (edge_count < n - 1) and (heap is not empty):
       (u, v) := DeleteMin(heap)   // Remove edge with smallest cost
       Reheapify(heap)
       j := Find(u)
       k := Find(v)
       if j ≠ k:
           edge_count := edge_count + 1
           t[edge_count, 1] := u
           t[edge_count, 2] := v
           mincost := mincost + cost[u, v]
           Union(j, k)
6. if edge_count ≠ n - 1:
       print "No spanning tree"
   else:
       return mincost
---
Explanation Line by Line
Step 1 – Heapify edges

Construct a heap out of the edge costs using Heapify;

We store all edges (u, v) in a min-heap based on cost[u, v].

This ensures we can efficiently extract the smallest-cost edge at each step.

Step 2 – Initialize Disjoint Set

for i := 1 to n do parent[i] := -1;

We use a Union-Find (Disjoint Set) data structure to check whether two vertices are already connected.

parent[i] = -1 means vertex i is its own parent initially.

Step 3 – Start variables

i := 0; mincost := 0.0;

i (or edge_count) keeps track of how many edges we’ve added to the MST.

mincost keeps track of total MST cost.

Step 4 – Main loop

while (i < n-1) and (heap not empty)

We keep adding edges until the MST has n-1 edges or the heap is empty (disconnected graph).

Step 5 – Pick smallest edge

Delete a minimum cost edge (u, v) from the heap

This is the key part of Kruskal’s — always pick the smallest available edge.

Step 6 – Find set representatives

j := Find(u); k := Find(v);

We find the root parent (representative) of each vertex.

If j == k, adding (u, v) would form a cycle, so we skip it.

Step 7 – Add edge to MST

If j ≠ k, we:

Add (u, v) to the MST list t.

Add cost[u, v] to mincost.

Union the sets j and k.

Step 8 – End condition

If i ≠ n-1 after loop ends → the graph was disconnected.

Otherwise → return mincost.

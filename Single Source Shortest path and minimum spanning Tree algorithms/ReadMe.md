
1.	SINGLE SOURCE SHORTEST PATH ALGORITHM
Given a connected weighted directed graph G(V,E), associated with each edge ⟨u,v⟩∈E, there is a weight w(u,v). The single source shortest paths (SSSP) problem is to find a shortest path from a given source r to every other vertex v∈V-{r}. The weight (length) of a path p=⟨ v0 , v1 ,…, vk ⟩ is the sum of the weights of its constituent edges:
w(p)= ∑i=1 kw( vi-1 , vi )
The weight of a shortest path from u to v is defined by δ(u,v)=min{w(p): p is a path from u to v}.

Representation of a shortest path tree
The shortest path tree rooted at s is a directed subgraph G'=(V',E') where V'⊆V   
and E'⊆E such that every v∈V' is reachable from s; and for all v∈V', the unique 
simple path in G' from s to v is a shortest path from s to v in G. In other words, for 
each vertex v∈V, we maintain a predecessor p(v) that is either a vertex or NIL. 
Thus, the output for a single shortest paths problem is a tree rooted at the source.

 
Initialization:
INITIALIZE (G,s)
1	d[s] ← 0 
2	 p[s] ← NIL 
3	 for all v∈V-{s} 
4	        do d[v] ← ∞ 
5	         p[v] ← NIL
Shortest Paths and Relaxation
The main technique used by the shortest path algorithms introduced here is relaxation, a method that repeatedly decreases an upper bound on the length of an actual shortest path for each vertex until the upper bound equals the length of the shortest path. For each vertex v, we maintain an attribute d[v] which is an upper bound on the length of a shortest path from source s to v. d[v] is also called the shortest path estimate.
RELAX (u,v,w)
 1    if  d[v]>d[u]+w(u,v)
 2          then  d[v] ←  d[u]+w(u,v)
 3                       p[v] ←  u


Different Algorithms are:
1.	Dijkstra’s Algorithm
2.	The Bellman-Ford Algorithm


Dijkstra’s Algorithm:
Dijkstra's algorithm assumes that all the edges in G are non-negative. The algorithm maintains a set S of vertices whose final shortest path weights from the source s have already been determined. That is, for all the vertices v∈S, we have d[v]=δ(s,v). The algorithm repeatedly selects a vertex u∈V-S with the minimum shortest-path estimate, inserts u to S, and relaxes all the edges leaving u. Also, a priority queue Q that contains all the vertices in V-S is maintained, keyed by their d values.
Below are the steps for finding shortest path using Dijkstra’s algorithm:
•	Built a graph using adj list for all the edges and their weight based on the graph is directed or undirected for all the 4 inputs.
•	Created a shortest path tree set called visited that keeps track of vertices included in shortest path tree
•	Assigned a distance value to all vertices in the input graph. Initialized all distance values as infinite in the starting and distance value as 0 for the source vertex so that it should be picked first.
•	Created a data structure for parent which keep track of path followed and used to display in the output.
•	Until “visited” does not included all vertices, a vertex with the minimum distance value has been picked and added to visited. The distance value of all the adjacent vertices has been updated.

Algorithm:

DIJKSTRA-SHORT (G,w,s)

 1     INITIALIZE (G,s)
 2     S ←  ∅
 3     Q ←  V
 4    while  Q≠∅
 5                  do  u ←  EXTRACT-MIN (Q)
 6                         S ←  S∪{u}
 7                        for each vertex v∈ Adj [u]
 8                                 do  RELAX (u,v,w)



 
 
The Graphs I used to run the Dijkstra’s algorithm are below:

Graph0

Directed	Graph1

Un-Directed	Graph2

Directed	Graph3

Un-Directed	Graph4

Un- Directed	Graph5

The graphs are present in the repo..please refer to the text files above....

The Results for the above graphs are: -
Single source Shortest paths for graph0.txt is: 
===========================================================
Number of Vertices provided: 6
Number of Edges provided: 10
The Graph is: DIRECTED
Start or Source provided: A
******************************************
Dijkstra's Algorithm results:
******************************************
Vertex 		Distance 	 Path
A -> B 		 1 		 A B 
A -> C 		 2 		 A C 
A -> D 		 3 		 A C D 
A -> E 		 3 		 A B E 
A -> F 		 6 		 A C D F 
******************************************************************
Time taken for this input to execute is : 0.9884834289550781 
******************************************************************
Single source Shortest paths for graph1.txt is: 
===========================================================
Number of Vertices provided: 8
Number of Edges provided: 11
The Graph is: UN DIRECTED
Start or Source provided: A
******************************************
Dijkstra's Algorithm results:
******************************************
Vertex 		Distance 	 Path
A -> B 		 2 		 A B 
A -> D 		 10 		 A D 
A -> C 		 8 		 A B C 
A -> E 		 11 		 A D E 
A -> F 		 17 		 A D E F 
A -> G 		 21 		 A D E H G 
A -> H 		 18 		 A D E H 
******************************************************************
Time taken for this input to execute is : 1.5134811401367188
******************************************************************
Single source Shortest paths for graph2.txt is: 
===========================================================
Number of Vertices provided: 9
Number of Edges provided: 16
The Graph is: DIRECTED
Start or Source provided: A
******************************************
Dijkstra's Algorithm results:
******************************************
Vertex 		Distance 	 Path
A -> B 		 3 		 A B 
A -> C 		 7 		 A B C 
A -> D 		 1 		 A D 
A -> H 		 8 		 A B H 
A -> I 		 12 		 A D I 
A -> E 		 9 		 A D E 
A -> G 		 11 		 A D E G 
A -> F 		 21 		 A D F 
******************************************************************
Time taken for this input to execute is : 0.9999275207519531 
******************************************************************
Single source Shortest paths for graph3.txt is: 
===========================================================
Number of Vertices provided: 9
Number of Edges provided: 18
The Graph is: UN DIRECTED
Start or Source provided: A
******************************************
Dijkstra's Algorithm results:
******************************************
Vertex 		Distance 	 Path
A -> C 		 9 		 A C 
A -> D 		 13 		 A D 
A -> B 		 22 		 A B 
A -> H 		 56 		 A B H 
A -> F 		 54 		 A C F 
A -> E 		 46 		 A D E 
A -> I 		 53 		 A D I 
A -> G 		 69 		 A D E G 

******************************************************************
Time taken for this input to execute is : 1.005411148071289 
******************************************************************
Single source Shortest paths for graph4.txt is: 
===========================================================
Number of Vertices provided: 7
Number of Edges provided: 12
The Graph is: UN DIRECTED
Start or Source provided: A
******************************************
Dijkstra's Algorithm results:
******************************************
Vertex 		Distance 	 Path
A -> B 		 1 		 A B 
A -> C 		 2 		 A C 
A -> D 		 3 		 A C D 
A -> E 		 3 		 A B E 
A -> F 		 6 		 A C D F 
A -> G 		 11 		 A B E G 
******************************************************************
Time taken for this input to execute is : 0.0 
******************************************************************
Single source Shortest paths for graph5.txt is: 
===========================================================
Number of Vertices provided: 9
Number of Edges provided: 16
The Graph is: DIRECTED
Start or Source provided: A
******************************************
Dijkstra's Algorithm results:
******************************************
Vertex 		Distance 	 Path
A -> B 		 4 		 A B 
A -> C 		 15 		 A B C 
A -> D 		 13 		 A B D 
A -> E 		 15 		 A B D E 
A -> F 		 19 		 A B D F 
A -> G 		 22 		 A B D E G 
A -> H 		 19 		 A B D E H 
A -> I 		 29 		 A B D E H I 
******************************************************************
Time taken for this input to execute is : 1.0058879852294922
******************************************************************

Data Structure Used: 
The algorithm used to find the shortest path in both Directed and Undirected weighted graphs is Dijkstra’s algorithm. Graph, Adjacency List, python List, Python Default dictionary are the data Structures used in this program to find the shortest 
path.

Complexity Analysis of Dijkstra’s algorithm:
Generally, Dijkstra’s algorithm has the following run times when implemented
using queues(which is a better approach):
•	Worst case time complexity: Θ(E+V log V)
•	Average case time complexity: Θ(E+V log V)
•	Best case time complexity: Θ(E+V log V)
•	Space complexity: Θ(V)
Here E is number of edges in the graph and V is the number of vertices.
I have used python’s defaultdict to build an adjacency list to represent the graph.
Time Complexity of this implementation is O(V2). As the relaxation of vertex 
happens for the minimum picked vertex weight. And have not used a priority 
Queue so the final complexity for my code would be Θ(E+V^2).  V^2 for the 
Vertex relaxation and it happens for every edge.

Graph #	Directed Graph’s Runtimes	Graph #	Un-Directed Graph’s Runtimes
Graph0	0.9884834289550781	Graph1	1.5134811401367188
Graph2	0.9999275207519531	Graph3	1.005411148071289
Graph5	1.0058879852294922	Graph4	0.0
** Runtimes in the above table are in Micro seconds
 

2.	MINIMUM SPANNING TREE
A spanning tree is a subset of Graph G, which has all the vertices covered with minimum possible number of edges. Hence, a spanning tree does not have cycles and it cannot be disconnected. By this definition, we can draw a conclusion that every connected and undirected Graph G has at least one spanning tree. A disconnected graph does not have any spanning tree, as it cannot be spanned to all its vertices.
               
We found three spanning trees off one complete graph. A complete undirected graph can have maximum nn-2 number of spanning trees, where n is the number of nodes. In the above addressed example, n is 3, hence 33−2 = 3 spanning trees are possible.
There are a few general properties of spanning trees.
1.	A connected graph can have more than one spanning tree. They can have as many as |v|^{|v|-2},∣v∣∣v∣−2, where |v|∣v∣ is the number of vertices in the graph.
2.	All possible spanning trees for a graph G have the same number of edges and vertices.
3.	Spanning trees do not have any cycles.
4.	Spanning trees are all minimally connected. That is, if any one edge is removed, the spanning tree will no longer be connected.
5.	Adding any edge to the spanning tree will create a cycle. So, a spanning tree is maximally acyclic.
6.	Spanning trees have |n| - 1∣n∣−1 edges, where |n|∣n∣ is the number of vertices
Minimum Spanning Tree (MST)
In a weighted graph, a minimum spanning tree is a spanning tree that has minimum weight than all other spanning trees of the same graph. In real-world situations, this weight can be measured as distance, congestion, traffic load or any arbitrary value denoted to the edges.
Different Algorithms are:
1.	Kruskal’s Algorithm
2.	Prim’s Algorithm

KRUSKAL’S ALGORITHM: 

Kruskal’s algorithm uses the greedy approach to find the minimum spanning tree for the given graph. Kruskal’s algorithm treats every node as an independent tree and connects one with another only if it has the lowest cost compared to all other options available.
Steps to create Minimum Spanning tree using Kruskal’s Algorithm:
•	It starts with a forest where each vertex is a tree (i.e. a single node tree).
•	It finds a safe edge to add to the growing forest by finding, of all the edges that connect any two trees in the forest, an edge (𝑢, 𝑣) of least weight. 
•	Kruskal’s algorithm qualifies as a greedy algorithm because at each step it adds to the forest an edge of least possible weight. 
•	At the end of the algorithm: We are left with one cloud that encompasses the MST A tree T which is our MST

Algorithm:

Kruskal()
solve all edges in ascending order of their weight in an array e
	ans = 0
	for i = 1 to m
		v = e.first
		u = e.second
		w = e.weight
		if merge(v,u) // there will be no cycle
			then ans += w

The graphs are present in the repo..please refer to the text files above....
**All the graphs mentioned above are undirected

The Results for the above graphs are: -
===========================================================
The Minimum Spanning Tree using Kruskal's Algorithm for graph0.txt :

**************************************
Kruskal's Algorithm Results
**************************************
Edge Selected 		 Weight

A -> B 			   1
B -> C 			   1
C -> D 			   1
B -> E 			   2
D -> F 			   3
******************************************************************
The total Cost for Minimum Spanning Tree is 8 
******************************************************************
Time taken for this input to execute is : 1.001119613647461
******************************************************************

===========================================================
The Minimum Spanning Tree using Kruskal's Algorithm for graph1.txt :
===========================================================
**************************************
Kruskal's Algorithm Results
**************************************
Edge Selected 		 Weight

D -> E 			   1
A -> B 			   2
G -> H 			   3
B -> C 			   6
E -> F 			   6
E -> H 			   7
C -> D 			   8
******************************************************************
The total Cost for Minimum Spanning Tree is 33 
******************************************************************
Time taken for this input to execute is : 1.0066032409667969
******************************************************************

===========================================================
The Minimum Spanning Tree using Kruskal's Algorithm for graph2.txt :
===========================================================
**************************************
Kruskal's Algorithm Results
**************************************
Edge Selected 		 Weight
A -> D 			   1
E -> G 			   2
A -> B 			   3
C -> H 			   3
B -> C 			   4
C -> I 			   6
D -> E 			   8
G -> F 			   15
******************************************************************
The total Cost for Minimum Spanning Tree is 42 
******************************************************************
Time taken for this input to execute is : 0.9937286376953125
******************************************************************

===========================================================
The Minimum Spanning Tree using Kruskal's Algorithm for graph3.txt :
===========================================================
**************************************
Kruskal's Algorithm Results
**************************************
Edge Selected 		 Weight

C -> D 			   4
A -> C 			   9
E -> F 			   18
H -> I 			   19
G -> I 			   20
A -> B 			   22
E -> G 			   23
D -> E 			   33
******************************************************************
The total Cost for Minimum Spanning Tree is 148 
******************************************************************
Time taken for this input to execute is : 0.0
******************************************************************

===========================================================
The Minimum Spanning Tree using Kruskal's Algorithm for graph4.txt :
===========================================================
**************************************
Kruskal's Algorithm Results
**************************************
Edge Selected 		 Weight
A -> B 			   1
B -> C 			   1
C -> D 			   1
B -> E 			   2
D -> F 			   3
F -> G 			   6
******************************************************************
The total Cost for Minimum Spanning Tree is 14 
******************************************************************
Time taken for this input to execute is : 1.0004043579101562
******************************************************************

===========================================================
The Minimum Spanning Tree using Kruskal's Algorithm for graph5.txt :
===========================================================
**************************************
Kruskal's Algorithm Results
**************************************
Edge Selected 		 Weight
F -> C 			   1
D -> E 			   2
H -> F 			   2
A -> B 			   4
E -> H 			   4
E -> G 			   7
C -> A 			   8
G -> I 			   9
******************************************************************
The total Cost for Minimum Spanning Tree is 37 
******************************************************************
Time taken for this input to execute is : 1.0001659393310547
******************************************************************

Data Structure Used: 
The algorithm used to find the Minimum spanning Tree is Kruskal’s algorithm. 
Graph, python List, Python dictionary are the data Structures used in this program to find the MST using Kruskal’s algorithm.

Complexity Analysis of Kruskal’s algorithm:
•	O(E logE) or O(E logV). 
•	Sorting of edges takes O(ELogE) time. 
•	After sorting, we iterate through all edges and apply find-union algorithm.
•	The find and union operations can take at most O(LogV) time. 
•	So overall complexity is O(ELogE +ELogV) time. 
•	The value of E can be at most O(V2), so O(LogV) are O(LogE)same. 
•	Therefore, overall time complexity is O(ElogE) or O(ElogV).
 
Here E is number of edges in the graph and V is the number of vertices.

Graph Number	Total Cost	Runtime 
Graph0	8	1.001119613647461
Graph1	33	1.0066032409667969
Graph2	42	0.9937286376953125
Graph3	148	0.0
Graph4	14	1.0004043579101562
Graph5	37	1.0001659393310547


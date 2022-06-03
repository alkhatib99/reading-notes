# Graph

## Table of Content

- [Graph](#graph)
  - [Table of Content](#table-of-content)
  - [What is a Graph?](#what-is-a-graph)
    - [Common Terminology When Working With Graph](#common-terminology-when-working-with-graph)
  - [Directed & Undirected](#directed--undirected)
    - [Undirected Graphs](#undirected-graphs)
    - [Directed Graph](#directed-graph)
  - [Complete vs Connected vs Disconnected](#complete-vs-connected-vs-disconnected)
    - [Complete Graphs](#complete-graphs)
    - [Connected](#connected)
    - [Disconnected](#disconnected)
  - [Acyclic vs Cyclic](#acyclic-vs-cyclic)
    - [Acyclic Graph](#acyclic-graph)
    - [Cyclic Graphs](#cyclic-graphs)

## What is a Graph?

A graph is a non-linear data structure that can be looked at as a collection of `vertices` (`nodes`) potentially connected by line segments named `edges`

### Common Terminology When Working With Graph

1- *Vertex* or *Node*: A data object that can have zero or more adjacent vertices.

2- *Edge*: A Edge is a connection between two nodes.

3-*Neighbor*: The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.

4-  *Degree*: The degree of a vertex is the number of edges connected to that vertex.

## Directed & Undirected

### Undirected Graphs

An `Undirected Graph` is a graph where each edge is undirected or bi-directional. This means that the undirected graph does not move in any direction.

For example, in the graph below, `Node C` is connected to `Node A`, `Node E` and `Node B`. There are no “directions” given to point to specific vertices. The connection is bi-directional.

![' '](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/UndirectedGraph.PNG).

The undirected graph we are looking at has nodes and 7 undirected edges

Vertices/Nodes = {a, b, c, d, e, f}

Edges = {(a,c),(a,d),(b,c),(b,f),(c,e),(d,e),(e,f)}

### Directed Graph

A `Directed Graph` also called a `Digraph` is a graph where every edge is directed.

Unlike an undirected graph, a `Digraph` has direction. Each node is directed at another node with a specific requirement of what node should be referenced next.

Compare the visual below with the undirected graph above. Can you see the difference? The `Digraph` has arrows pointing to specific nodes.

![' '](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DirectedGraph.PNG)

The directed graph above has six vertices and eight directed edges

Vertices = {a,b,c,d,e,f}

Edges = {(a,c),(b,c),(b,f),(c,e),(d,a),(d,e)(e,c)(e,f)}

## Complete vs Connected vs Disconnected

### Complete Graphs

A complete graph is when all nodes are connected to all other nodes.

![CompleteGraph](https://github.com/codefellows/seattle-dsa-501-n1/raw/31b0969f0c70ede76463d036a0aef432fb4714bc/readings/assets/CompleteGraph.PNG)

Take a close look at each of the vertices in the graph above. Do you notice that
each vertex is actually connected to every other node on the graph? That is what makes
it a complete graph.

### Connected

A connected graph is graph that has all of `vertices`/`nodes` have at least one
edge.

![ConnectedGraph](https://github.com/codefellows/seattle-dsa-501-n1/raw/31b0969f0c70ede76463d036a0aef432fb4714bc/readings/assets/ConnectedGraph.PNG)

In the visual above, this looks a lot more than what you are used to seeing.
If you look closely at the different vertices of the graph, you will see that each node
is connected to at least one other node or vertices. A `Tree` is a form of a connected graph. We will
talk more about that in a bit.

### Disconnected

A disconnected graph is a graph where some vertices may
not have edges.

![DisconnectedGraph](https://github.com/codefellows/seattle-dsa-501-n1/raw/31b0969f0c70ede76463d036a0aef432fb4714bc/readings/assets/DisconnectedGraph.PNG)

In the above visual, the disconnected graph shows that some nodes may not always be connected to other
nodes or vertices of the graph. It is complelty possible to have standalone nodes or edges (also known as islands)
in a graph data structure.

## Acyclic vs Cyclic

In addition to Undirected and Directed graphs, we also have
acyclic and cyclic graphs.

### Acyclic Graph

An acyclic graph is a directed graph without cycles.

A cycle is when a node can be traversed through and potentially end up back at itself.

Here is an example of 3 acyclic graphs:

![ThreeAcyclicGraphs](https://github.com/codefellows/seattle-dsa-501-n1/raw/31b0969f0c70ede76463d036a0aef432fb4714bc/readings/assets/threeAcyclic.png)

A directed acyclic graph is also called a DAG. This can also be represented as what we know as a **tree**.

### Cyclic Graphs

A Cyclic graph is a graph that has cycles.

A cycle is defined as a path of a positive length that starts and ends at the same vertex.

Here is an example of a two different cyclic graphs:

![Acyclic](https://github.com/codefellows/seattle-dsa-501-n1/raw/31b0969f0c70ede76463d036a0aef432fb4714bc/readings/assets/cyclic.PNG)

[Home](README.md)

<br>

# Graphs

<br>

## Readings from [Graphs](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/graphs.html)

<br>

### Overview

<br>

> A `graph` is a non-linear data structure that can be looked at as a collection of vertices (or nodes) potentially connected by line segments named edges.

- Here is some common terminology used when working with Graphs:
  - `Vertex`
    - A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
  - `Edge`
    - An edge is a connection between two nodes.
  - `Neighbor`
    - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
  - `Degree`
    - The degree of a vertex is the number of edges connected to that vertex.

<br>

### Directed vs Undirected

<br>

#### Undirected Graphs

<br>

> An Undirected Graph is a graph where each edge is undirected or bi-directional.

> This means that the undirected graph does not move in any direction.

<br>

#### Directed Graphs (Digraph)

<br>

> A `Directed Graph` also called a `Digraph` is a graph where every edge is directed.

> Unlike an undirected graph, a `Digraph` has direction. Each node is directed at another node with a specific requirement of what node should be referenced next.

<br>

### Complete vs Connected vs Disconnected

<br>

#### Complete Graphs

<br>

> A `complete graph` is when all nodes are connected to all other nodes.

<br>

#### Connected

<br>

> A `connected graph` is graph that has all of vertices/nodes have at least one edge.

> A `Tree` is a form of a `connected graph`. 

<br>

#### Disconnected

<br>

> A `disconnected graph` is a graph where some vertices may not have edges.

> It is complelty possible to have `standalone` nodes or edges (also known as `islands`) in a graph data structure.

<br>

### Acyclic vs Cyclic

<br>

#### Acyclic Graph

<br>

> An `acyclic graph` is a directed graph without cycles.

> A cycle is when a node can be traversed through and potentially end up back at itself.

> A directed acyclic graph is also called a `DAG`. This can also be represented as what we know as a `tree`.

<br>

#### Cyclic Graphs

<br>

> A `Cyclic graph` is a graph that has cycles.

> A `cycle` is defined as a path of a positive length that starts and ends at the same vertex.

<br>

### Graph Representation

<br>

- We represent graphs through:
  - Adjacency Matrix
  - Adjacency List

<br>

#### Adjacency Matrix

<br>

> An `Adjacency matrix` is represented through a 2-dimensional array.

> If there are n vertices, then we are looking at an n x n Boolean matrix.

> Each Row and column represents each vertex of the data structure.

> The elements of both the column and the row must add up to 1 if there is an edge that connects the two, or zero if there isn’t a connection.

> A `sparse graph` is when there are very few connections. a dense graph is when there are many connections.

> Within an `adjacency matrix`, an undirected graph will always be symmetric.

> This is not the case for a `directed graph`.

<br>

#### Adjacency List

<br>

> An `adjacency list` is the most common way to represent graphs.

> An `adjacency list` is a collection of linked lists or array that lists all of the other vertices that are connected.

> `Adjacency lists` make it easy to view if one vertices connects to another.

- We can visually see that we are working with a collection of some sort. The visual is depicting a Linked List, but you could easily make it an array of arrays if you’d like.
- Each index or node (depending on the data structure you choose to represent the adjacency list) will be a vertex within the graph.
- Every time you add an edge, you will find the appropriate vertices in the data structure and add it to the appropriate location.

<br>

### Weighted Graphs

<br>

> A `weighted graph` is a graph with numbers assigned to its edges.

> These numbers are called `weights`.

> ? A great way to represent the `{vertices, weight}` connection is through some sort of `key/value` pair data structure.

<br>

### Traversals

<br>

#### Breadth First

<br>

> In a `breadth first traversal`, you are starting at a specific vertex/node.

> This node must be specified when calling the `BreadthFirst()` method.

> The breadth-first traversal of a `graph` is like that of a `tree`, with the `exception` that graphs can have `cycles`.

> Traversing a graph that has cycles will result in an infinite loop….this is bad.

> To prevent such behavior, we need to have some way to keep track of whether a vertex has been “visited” before.

> Upon each visit, we’ll add the previously-unvisited vertex to a visited set, so we know not to visit it again as traversal continues.

<br>

> `Breadth first traversal` is when you visit all the nodes that are closest to the root as possible.

> From there you traverse outwards, level by level, until you have visited all the vertices/nodes.

<br>

- Here is what the algorithm breadth first traversal looks like:
  - Enqueue the declared start node into the Queue.
  - Create a loop that will run while the node still has nodes present.
  - Dequeue the first node from the queue
  - if the Dequeue‘d node has unvisited child nodes, add the unvisited children to visited set and insert them into the queue.

<br>

```py
ALGORITHM BreadthFirst(vertex)
    DECLARE nodes <-- new List()
    DECLARE breadth <-- new Queue()
    DECLARE visited <-- new Set()

    breadth.Enqueue(vertex)
    visited.Add(vertex)

    while (breadth is not empty)
        DECLARE front <-- breadth.Dequeue()
        nodes.Add(front)

        for each child in front.Children
            if(child is not visited)
                visited.Add(child)
                breadth.Enqueue(child)   

    return nodes;
```

<br>

- Here is a breakdown of what is going on:
  - We have declared that our starting node (or root) is going to be Node A.
  - The first thing we want to do is Enqueue the root.
  - We also need to add the root to the visited set.
  - Next, we enter a while loop. We want this loop to keep running until there are no more nodes in our queue.
  - Once we are in the while loop, we want to Dequeue the front node and then check to see if it has any children.
  - if there are children of the node we are currently looking at, we want to add them to visited set. This will help us know that we have already seen that node before, and won’t accidently push us into an infinite loop if the graph was cyclic. In addition to tracking each child node as visited, we want to place any of its children that have not yet been visited into the queue.
  - The process will complete until the queue is empty.
  - Once the while loop breaks, we can then return the list of nodes. This list will contain, in order, all the nodes that were traversed.

<br>

- A few things to note about breadth-first traversals:
  - If there are any disconnected nodes (such as islands) with the graph data structure, they will not be traversed.
  - Breadth-first only outputs the nodes that are connected in some relation to the root that you pass in.

<br>

#### Depth First

<br>

> In a `depth first traversal`, we approach it a bit different than the way we do when working with a `depth first traversal` of a tree.

> Similar to how the breadth-first uses a queue, we are going to use a Stack for our depth-first traversal.

<br>

- The algorithm for a depth first traversal is as follows:
  - Push the root node into the stack
  - Start a while loop while the stack is not empty
  - Peek at the top node in the stack
  - If the top node has unvisited children, mark the top node as visited, and then Push any unvisited children back into the stack.
  - If the top node does not have any unvisited children, Pop that node off the stack
  - repeat until the stack is empty.

<br>

### Real World Uses of Graphs

<br>

- Graphs are extremely popular when it comes to it’s uses. Here are just a few examples of graphs in use:
  - GPS and Mapping
  - Driving Directions
  - Social Networks
  - Airline Traffic
  - Netflix uses graphs for suggestions of products

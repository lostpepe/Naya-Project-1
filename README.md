# Naya-Project-1
First project of the data science course


This is the first project of the data sience course at Naya College.
The objective of the project is to consolidate some basic python knowledge

The desing was dictated as part of the problem definition.

Assumptions:
- The type used for the name of the nodes is immutable and supports __eq__ and __nq__ methods
- The nodes in the graph may be connected to nodes not in the graph. Operations on the graph should not fail a cause of this
- The nodes of a graph could be modified outside the graph. The graph holds references to the node objects.
- The weight of the edges are not negative.

Issues:

We found a couple of issues during the implementation.
- Lack of methods defined to support encapsulation. For example there is no method in the class node to retrive the name.
We decided to add methods to support iteration of neighbors, edges and make the class Node and Graph iterable.
- It is not clear why the operation of updating a node with a node of the same name is not part of the Node class.
We decided to add this operation to the class mode to simplify the Graph class.
- It is not clear why the Node operation doens't support the the setitem protocol while the method update has the same signature and functionality.
We decided to add support for this protocol.
- We never recived a clear answer about the expected behavior of the add_edge method of the Graph class.
After several internal deliverations trying to decypher the intention of the method we decided that the method will add the nodes of the edge if they are not part of the graph.
- The graph pathologies. Zombi nodes. Let's say that node(1) is connected to node(2) and we just insert node(1) in the graph. node(1) degree is one, but in the graph is 0. This is why we don't interact directly with the node retirved form the graph but thru a service of graph. Phantom edges. Let's consider graph1= {(1,2) (2,3)} graph2 = {(1,3)} if you perform graph3 = graph1 + graph2 then graph 1 will now include {(1,2),(2,3),(1,3)} just becuase the reference of node(1) got updated during the sum.

Style:
We know that if a function doens't return a value is like returning None but do to secure coding practicies we prefer all the functions to have clear exit and a defult return value.

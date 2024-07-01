---
title: "What Makes a Tree a Tree"
weight: 15
pre: "3. "
---

{{< youtube zZ7vDmZEEIo  >}}

[Video Materials](video)

Trees can come in many shapes and sizes. There are, however some constraints to making a valid tree. 

- A tree has a single root
- A child has exactly one parent
- A tree is fully connected (IE a single tree)
- A tree has no cycles (IE no loops)


## Valid Trees

Any combination of the following represents a valid tree:
- A tree with a single node; just a root,
![Single](/images/14/2Tree_Simple.png)

- A tree where each node has a single child, or
![Linear](/images/14/2Tree_Linear.png)

- A tree where nodes have many children.
![Linear](/images/14/2Tree_Wide.png)


## Invalid Trees

Below are some examples of invalid trees.

- A cycle 
![Cycle](/images/14/2Tree_Cycle.png)
Again, cycles are essentially loops that occur in our tree. In this example, we see that our leaf has two parents. One way to determine whether your data structure has a cycle is if there is more than one way to get from the root to any node. 

- A cycle 
![Cycle](/images/14/2Tree_Cycle2.png)
Here we can see another cycle. In this case, the node immediately after the root has two parents, which is a clue that a cycle exists. Another test 

- Two Roots
![Two Roots](/images/14/2Tree_TwoRoots.png)
Trees must have a single root. In this instance, it may look like we have a tree with two roots. Working through this, we also see that the node in the center has two parents. 

- Two Trees
![Double Tree](/images/14/2Tree_DoubleTree.png)
This example would be considered two trees, not a tree with two parts. In this figure, we have two fully connected components. Since they are not connected to each other, this is not a single tree. 

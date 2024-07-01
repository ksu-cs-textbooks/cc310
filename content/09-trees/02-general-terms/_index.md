---
title: "General Terms"
weight: 10
pre: "2. "
---

{{% notice warning %}}

The video incorrectly states the degree of a tree is equal to the degree of the root. The correct definition is that the degree of a tree is the **largest** degree of any node in the tree.

{{% /notice %}}

{{< youtube JvbXXm_KEDY  >}}

[Video Materials](video)


To get ourselves comfortable in working with trees, we will outline some standard vocabulary. Throughout this section, we will use the following tree as a guiding example for visualizing the definitions.  
![Blank](/images/14/2Tree_Blank.png)

## Definitions

- `Node` - the general term for a structure which contains an item, such as a character or even another data structure. 
- `Edge` - the connection between two nodes. In a tree, the edge will be pointing in a downward direction. 

![Nodes and Edges](/images/14/2Tree_NodeEdge.png)

This tree has five edges and six nodes. There is no limit to the number of nodes in a tree. The only stipulation is that the tree is `fully connected`. This means that there cannot be disjoint portions of the tree. We will look at examples in the next section. 

{{% notice info %}}

A rule of thumb for discerning trees is this: if you imagine holding the tree up by the root and gravity took effect, then all edges must be pointing downward. If an edge is pointing upward, we will have a `cycle` within our structure so it will not be a tree.

{{% / notice %}}

--- 

- `Root` - the topmost node of the tree

![Root](/images/14/2Tree_Root.png)

To be a tree, there must be exactly one root. Having multiple roots, will result in a `cycle` or a tree that is not `fully connected`. In short, a `cycle` is a loop in the tree. 

---

- `Parent` - a node with an edge that connects to another node further from the root. We can also define the root of a tree with respect to this definition; `Root`: a node with no parent.
- `Child` - a node with an edge that connects to another node closer to the root.
    - In a general tree, the children of a node are an unordered set. There is not a fixed or defined order for generic trees. 
![Parent and Child](/images/14/2Tree_ParentChild1.png)
![Parent and Child](/images/14/2Tree_ParentChild2.png)
In a tree, child nodes must have exactly one parent node. If a child node has more than one parent, then a `cycle` will occur. If there is a node without a parent node, then this is necessarily the root node. There is no limit to the number of child nodes a parent node can have, but to be a parent node, the node must have at least one child node. 

---

- `Leaf` - a node with no children.
![Leaf](/images/14/2Tree_Leaf.png)
This tree has four leaves. There is no limit to how many leaves can be in a tree. 

---

- `Degree`
    - `Degree of a node` - the number of children a node has. The degree of a leaf is zero. 
    - `Degree of a tree` - the degree of an entire tree is the **largest** degree of any node found in the tree.
![Degree](/images/14/2Tree_Degree.png)

The degree of the nodes are shown as the values on the nodes in this example. The degree of the tree is the largest degree of any node in the tree. Thus, the degree for this tree is 3.

--- 

- A `tree` is defined recursively. This means that each child of the root is the root of another tree and the children of those are roots to trees as well. Again, this is a recursive definition so it will continue to the leaves. The leaves are also trees with just a single node as the root.  
![Subtrees](/images/14/2Tree_SubTree.png)
In our example tree, we have six trees. Each tree is outlined in a red dashed circle:
    - the main tree, 
        - the tree off the left of the main root, 
            - the tree off the left of this root, 
            - the tree in the center of this root,
            - the tree off the right of this root, and
        - the tree off the right of the main root with a single node








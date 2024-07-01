---
title: "Tree Terms"
pre: "2. "
weight: 12
date: 2019-02-04T10:53:26-05:00
hidden: true
---

{{< youtube JvbXXm_KEDY >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

[Slide 1]

To be able to work with tree and really understand them, we will start with some vocabulary. We will use this tree as a guiding example for the terms. The first that we will cover are nodes and edges. 

[Slide 2]

Nodes, which we depict visually as circles, are the structures which contain the data. Here we have outlined them in a dashed line to emphasize them. The data can be characters, strings, files, or any data structure. We refer to this data as the item that the node contains. 

[Slide 3]

Edges, which we depict as arrows, connect two nodes together. These arrows will be 'directed' to show the relationship between two nodes. This relationship is referred to as a parent child relationship. For example, we would say that node `a` is a parent of nodes `b`, `c` and `d`. We can also say that node `b` is a child of node `a`.

Much like a family tree, the arrows will connect parents, the node at the flat end of the arrow, with their children, the pointed end of the arrow. Parents can have many children. However, each child must have at most one parent. In a later video, we will discuss counterexamples of trees to reinforce this idea.  

[Slide 4]

The root of a tree is a special type of node; it is a node with no parent. The root is also typically depicted as the topmost node, this is just a rule of thumb. Tree's will have exactly one root. In this tree, node `a` is the root.

[Slide 5]

Another special type of node that are present in trees are leaves. A leaf is defined as a node with no children. There can be any number leaves in a tree. Leaves will not necessarily be at the same level or distance from the root. In this tree, we have outlined the leaves in dashed lines. Nodes `d`, `e`, `f`, `h`, `i`, and `j` are all leaves.

[Slide 6]

Each node has a property called the degree. The degree of a node is simply the number of children. This means that leaves will always have degree zero as they have no children.

We can also talk about the degree of a tree. The degree of a tree is equal to the degree of the root. In this tree, the root is node `a` which has degree three. Thus, the degree of this tree is three. 

[Slide 7]

Trees are defined recursively. This means that a tree is made up of other trees. Outlined in purple dashed lines are each of the trees which make up the whole tree. In later sections, we will discuss how we use this fact to build trees in code. 

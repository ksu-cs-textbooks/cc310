---
title: "Tree Pseudocode"
pre: "4. "
weight: 14
date: 2019-02-04T10:53:26-05:00
hidden: true
---

{{< youtube y02_6lWMVnQ >}}

#### Resources
* <a href="slides" target="_blank">Slides</a>

#### Video Script

[Slide 1]

The goal in this course is not only to understand the data structure but to implement one of our own. For this next portion, we will cover how to implement trees. 

Here we have the UML diagram for our initial tree implementation. In this implementation, we are not yet able to prevent cycles. In a future module, we will introduce ways to determine cycles recursively. 

[Slide 2]

We have three attributes for our tree implementation. 

First we have `item` which is a protected object. This is the attribute which tracks the value of the item which is contained by the node. Recall that a nodes `item` can be essentially anything! It can be a character and even another data structure.

Then we have the `parentNode` which is an instance of a tree itself. In this implementation, we will have each node keep track of its parent and children. 

The third attribute is `children`. This is a list of trees. 

Let's look at an example of what a tree will look like in code to get more familiar with this implementation.

[Slide 3]

Looking at these two trees, we see that nodes `a` and `f` are both roots. We can verify this in code as the `parent` attribute is set to None. 

Visually, we see that nodes `b`, `d`, `e`, and `f` are leaves. Again, we can verify this in code as their `children` lists are empty. 

We can also examine the edges that appear in our tree. We see that node `a` is parent of node `b`. Node `b` is listed as a child of node `a` and the parent to node `b` is listed as node `a`.


[Slide 4]

Upon initialization, we will set `parentNode` to `NULL` and `children` to an empty list. The initialization takes a value as input and this value becomes the nodes `item`. Thus, we will end up with a single node which is the root and the leaf with item equal to the value we initialized it with. 


[Slide 5]

Our tree has three getter functions. We have a getItem function which will return the item of the node, getParent which will return the parent of the node, and getChildren which will return the children of the node.


[Slide 6]

For our tree, we will also implement functions to determine the type of node. We will have a function isRoot. To implement this, we can get the nodes parent attribute. If it is None, then we return true. Otherwise, we should return false. 

We also have the function isLeaf. This has a similar implementation. We first get the children attribute and if it is an empty list, then we have leaf. If it is not empty, then we return false as this node is not a leaf. 

[Slide 7]

The last two functions we will cover in this video are getDegree and findChild. 

Recall that the degree of a node is equal to the number of children. For this function, we can simply get the children attribute and count the number of children then return that number. 

The goal of the findChild function is to take a value and see if that value is an item for a child of the current node. To implement this, we can get the children attribute and check their items. If a child has their item equal to the value we are searching for, then we return true. 


[Slide 8]

This will conclude the pseudocode for this video. In the next videos, we address adding and removing children from the tree. 

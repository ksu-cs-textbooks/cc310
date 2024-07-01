---
title: "Binary Tree"
weight: 40
pre: "8. "
---

{{< youtube FugxsgsFu9I  >}}

![Binary Tree](images/14/4Tree_Binary.png)

A binary tree is a type of tree with some special conditions. First, it must follow the guidelines of being a tree: 
- There must be single root,
- each child node must have a single parent node,
- it must be fully connected (no disjoint parts), and
- there can be no cycles (no loops).

The special conditions that we impose on binary trees are the following:
- Each node has at most 2 children (nodes can have 0, 1, or 2 children), and
- unlike general trees, the children in a binary tree are not an unordered set. The children must be ordered such that:
    - all of the descendants in the left tree are less than the parent's value, and
    - all of the descendants in the right tree are greater than the parent's value
    
To reinforce these concepts, we will look at examples of binary trees and examples that are not binary trees. 
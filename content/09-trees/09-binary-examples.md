---
title: "Binary Tree Examples"
weight: 45
pre: "9. "
---

{{< youtube 8uSNprLBCpE  >}}

## Valid Binary Trees

![Single Node](images/14/4Binary_Single.png)

This is a valid binary tree. We have a single node, the root, with no children. As with general trees, binary trees are built recursively. Thus, each node and its child(ren) are trees themselves. 

![Unbalanced](images/14/4Binary_UnBal.png)

This is also a valid binary tree. All of the left children are less than their parent. The node with item '10' is also in the correct position as it is less than 12, 13, and 14 but greater than 9.

![Balanced](images/14/4Binary_Bal.png)

We have the same nodes but our root is now 12 whereas before it was 14. This is also a valid binary tree. 

![Alphabet Binary Tree](images/14/4Binary_Alpha.png)

Here we have an example of a binary tree with alphabetical items. As long as we have items which have a predefined order, we can organize them using a binary tree.

## Invalid Binary Trees

![Alphabet Non-Binary Tree](images/14/4Binary_NOTAlpha.png)

We may be inclined to say that this is a binary tree: each node has 0, 1, or 2 children and amongst children and parent nodes, the left child is smaller than the parent and the right child is greater than the parent. However, in binary trees, all of the nodes in the left tree must be smaller than the root and all of the nodes in the right tree must be larger than the root. In this tree, `D` is out of place. Node `D` is less than node `T` but it is also less than node `Q`. Thus, node `D` must be on the right of node `Q`.

![Too Many Children](images/14/4Binary_ManyChildren.png)

In this case, we do not have a binary tree. This does fit all of the criteria for being a tree but not the criteria for a binary tree. Nodes in binary trees can have at most 2 children. Node `30` has three children. 

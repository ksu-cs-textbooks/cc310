---
title: "Balance"
weight: 60
pre: "12. "
---

![Unbalanced](images/14/4Binary_UnBal.png)

While this is a valid binary tree, it is not balanced. Let's look at the following tree. 

![Balanced](images/14/4Binary_Bal.png)

We have the same nodes but our root is now 12 whereas before it was 14. This is a valid binary tree. We call this a `balanced` binary tree. A balanced binary tree looks visually even amongst the left and right trees in terms of number of nodes.

**Note:** Balancing is not necessary for a valid binary tree. It is, however, important in terms of time efficiency to have a balanced tree. For example, the number of actions when inserting an element is about the same as the number of levels in the tree. If we tried to add the value 11 into the unbalanced tree, we would traverse 5 nodes. If we tried to add the value 11 in to the balanced tree, we would traverse just 3 nodes.

We believe that balancing binary trees is out of the scope of this course. If you are interested in how we might balance a tree, feel free to check out these videos by Dr. Joshua Weese.

{{< youtube Em9-Rr6PEBc  >}}

{{< youtube N7g8vn5sJoI  >}}

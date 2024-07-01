---
title: "Not Trees"
pre: "3. "
weight: 13
date: 2019-02-04T10:53:26-05:00
hidden: true
---

{{< youtube zZ7vDmZEEIo >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

[Slide 1]

Now that we have outlined key tree terms, we will cover some examples of trees and not trees. To be a tree, four main criteria must be met.
1. There must be just a single root.
1. Each child can only have one parent.
1. They must be fully connected.
1. There must be no cycles.

[Slide 2]

In this figure, we have two key issues. Feel free to pause the video now if you would like determine them for yourself. One of the issues with this tree is that it has two roots. There are two nodes, `w` and `e`, which have no parents. The second issue in this tree is that node `d` has two parent nodes, `w` and `e`.

[Slide 3]

Here is a possible way that we can fix the tree. This solution ends up creating two trees rather than a single tree. This is okay but we must note that there are two trees. In our implementation of trees, this will be a possible situation and will happen regularly since we build trees recursively. 

These two trees offer a nice transition into another property of trees. Trees must be fully connected. This means that no part of the tree is disconnected. If we were to try and say that this whole figure was a tree, we would be incorrect. It is not fully connected.

[Slide 4]

Here is one way we can make a legal tree from what we started with. I have arbitrarily connected these two pieces. In practice, we will get input from the user or have stipulations on which nodes should be connected. 

Up to this point, we have seen three of the four criteria broken: having a single root, each child must have one parent, and a tree must be fully connected. We have not seen an example of a cycle as of yet. 

[Slide 5]

A rule of thumb for cycles is this: if there is more than one way to get a node then there exists a cycle. 

In this particular example, we have two issues again. One issue is that we don't have a true root. It may seem like node `w` is the root as it is the topmost node. However, node `b` is actually the parent of `w`. Remember that flat end of the arrow starts at the parent and the arrowhead ends at the child. 

The other issue is that we have a cycle in this attempted tree. There are multiple ways to get to node `w`, assuming `w` is a root. We could simply start at `w`, another path to get to `w` would be start at `w`, go to `g`, then `b`, and back to `w`. 

We can use the following rule of thumb as well for visually inspecting a tree: if we were to hold the tree by the root and let gravity take effect then all of the edges must be pointing downward. If there are any that point upward, then there exists a cycle. 

[Slide 6]

This example is rather straight forward to fix. We can simply remove the edge that connects node `b` and node `w`. We then have a legally tree. 

[Slide 7]

As we have seen, it is not uncommon to have more than one issue when we don't have a valid tree. 

Let's take a moment to recap what we have covered so far: 
1. There must be exactly one root. We have seen an example where we had multiple nodes without parents and we saw another example where there was no node without parents.
1. Each child can only have one parent, with the exception of the root. There must be one node which has no parents, that is the root. 
1. Trees must be fully connected. This means that there are no nodes or other trees disconnected from the tree. It is okay to have more than one tree at a time in code. 
1. There must be no cycles. The rule of thumb for cycles is that if there is more than one way to get to a node then there exists a cycle. In a later module, we will discuss better ways to determine if cycles exist in code rather than visual inspection. 

---
title: "Adding Child"
pre: "5. "
weight: 15
date: 2019-02-04T10:53:26-05:00
hidden: true
---

{{< youtube T5gy1Q7hx1w >}}

#### Resources
* <a href="slides" target="_blank">Slides</a>

#### Video Script

[Slide 1]

To be able to build trees, we must be able to add children. Again, trees are defined recursively so we are really adding trees to trees. Let's look at this example.

Here we have two trees and supposed we wanted to connect them by making node `x` a child of node `c`. Visually, we would simply add an edge from `c` to `x`. 

[Slide 2]

Let's look at these structures underlying code. We see that nodes `a` and `x` are both roots and `c`, `d`, `y`, and `z` are leaves. In principal, what we need to do is add the connection between `c` and `x`. To do this properly, there are two places that we need to update: the parent of `x` and the children of `c`. 

[Slide 3]

Doing those updates would result in the following. We have added `c` as the parent of `x` and `x` as a child of `c`. 

[Slide 4]

Now visually we have the connection from `c` to `x`. And thus, a single tree. 

[Slide 5]

Adding a child is rather straightforward on the surface but there are a few considerations we must make. First, we must make sure that the child does not already have a parent. Then we also should check that the child is not already a child of the parent. This is a form of redundancy to make sure that we have checked both reference to the relationship. 

[Slide 6]

Here we have the pseudocode for adding a child. The first two checks are for the considerations discussed in the last slide. If the child already has a parent, then we have an exception. If the child is already a child of the parent, then we return false. Then we update the parent's children and update the child's parent. After that, we return true so that the user can know it was successful.

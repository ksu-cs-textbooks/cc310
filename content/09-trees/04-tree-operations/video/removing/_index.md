---
title: "Removing Child"
pre: "6. "
weight: 16
date: 2019-02-04T10:53:26-05:00
hidden: true
---

{{< youtube QtfZIUMPrJY >}}

#### Resources
* <a href="slides" target="_blank">Slides</a>

#### Video Script

[Slide 1]

For full functionality of our tree, we need to be able to remove children as well as add them. Thinking of the example of a file tree, if we were to delete a file, that would remove it from our tree. In most cases, deleting a file just removes it from the current directory and into a trash or recycle folder. Meaning it is not removed from existence. This is very similar to how our tree will behave. 

[Slide 2]

Using this tree as an example again, suppose we wanted to remove child `x` from `c`. Similar to when we add a child, visually what we do is remove the edge between the two nodes. This will result in two separate trees.

[Slide 3]

In code, we have what we concluded with in the adding a child video. Node `a` is the root and `d`, `y`, and `z` are all leaves. To modify this to severe the edge between `x` and `c`, we will need to update their respective parent and children.

[Slide 4]

Now we have eliminated the edge completely and we have two distinct trees. Node `x` no longer has a parent and node `c` is now a leaf.

[Slide 5]

We can see this change visually and understand that both trees are still there. 

[Slide 6]

Removing children has one special condition and that is that the child we are trying to remove, must be a child of the parent. 

[Slide 7]

The pseudocode for removing a child is shown here. It is important that we return false if the child is not in the parent's children as we must notify the user that we did not remove the child. In the case where we can do the removal, we update the parent of the child and the children of the parent then return true. 

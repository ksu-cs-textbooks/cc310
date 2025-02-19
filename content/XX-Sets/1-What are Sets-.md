---
title: "What are Sets?"
weight: 5
pre: "1. "
disableMathJax: false
---
{{< youtube XJSPN3tx7As  >}}

A set is a collection of elements that are usually related to each other. They can be sets of numbers, letters, people, cars, or even sets themselves!  Thus, the elements stored in a stack, queue or list can all be considered as sets. When we define the elements in a set, we typically enclose them in curly brackets as follows. 

$$
\text{A} = \{ \text{Emily}, \text{Don}, \text{Mohammed}, \text{Huichen} \}
$$

Here, $\text{A}$ is the name of the set and Emily, Don, Mohammed, and Huichen are members of set $\text{A}$.

Sets do have a few key properties:

1. There are no duplicates allowed; we can't add another Emily to our set above, and
2. The elements in a set are unordered; Don doesn't come before or after Huichen in the set.

There are also a couple of important sets that we need to know.

1.	The universal set, $\mathbb U$, is the set of all elements in what we call the "universe of interest". However, this "universe of interest" is relative to the problem at hand; in our example above it could be the set of all people, the set of all students, etc.
2.	The empty set, usually written as $\emptyset$ or `{}` is the set that contains, well nothing! There is exactly one empty set across all "universes of interest".

## Visualizing Sets

If we want to visualize sets and the relationships between them, we can view them using a Venn Diagram as shown below.

![Set Venn Diagram](/images/10/10.1.set.svg)

The drawing is equivalent to saying the following.

$$
\text{A} = \{ 17, 9, 32, 15, 3, 5 \} \\ 
\text{B} = \{ 32, 1, 22, 15, 4, 6, 14 \}
$$

If we overlap the two sets so that the common elements (in this case, 15 and 32) are in the overlapping section, we see that we do not get two copies of 15 and 32, but that we have just one copy of each. Thus, we have preserved the property that sets do not have duplicates. This overlapping area is called the intersection of the two sets.

![Set Venn Diagram Overlap](/images/10/10.1.overlap.svg)
 
In the following operations on sets, we will use variants of the diagram below, which shows set $\text{A}$ and set $\text{B}$ overlapping. The yellow part of set $\text{A}$ denotes elements of set $\text{A}$ that are not in set $\text{B}$, while the green part of $\text{B}$ denotes elements of set $\text{B}$ that are not in set $\text{A}$. The orange part of the diagram denotes the intersection of $\text{A}$ and $\text{B}$, which includes elements of the sets that exist in both set $\text{A}$ and set $\text{B}$.

![Set Union Venn Diagram](/images/10/10.1.union.png)
 

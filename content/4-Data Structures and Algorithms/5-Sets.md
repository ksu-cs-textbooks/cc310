---
title: "Sets"
weight: 25
pre: "5. "
---
![Set Diagram](/images/4/4.5.set.png)

Another linear data structure is known as a _set_. A _set_ is very similar to a list, but with two major differences:

1. A set cannot contain duplicate elements. Each element must be unique in the set.
2. A set does not necessarily keep track of the ordering of the elements within the set.

In fact, the term _set_ comes from mathematics. We've probably seen sets already in a math class.

Beyond the typical operations to add and remove elements from a set, there are several operations unique to sets:

* **union** - find the elements that are contained in one or both of the sets given;
* **intersection** - find the elements only contained in both sets given;
* **set difference** - remove all elements from a set that are also contained in another set; and
* **subset** - test if all elements in one set are also contained in another set.

Again, many of these operations may be familiar from their use in various math classes. 

## Set Operations and Boolean Logic

In addition, we can easily think of set operations as boolean logic operators. For example, the set operation **union** is very similar to the boolean operator **or**, as seen in the diagram below.

![Set Union](/images/4/4.5.union.svg)^[File:Venn0111.svg. (2019, November 15). Wikimedia Commons, the free media repository. Retrieved 02:37, February 8, 2020 from https://commons.wikimedia.org/w/index.php?title=File:Venn0111.svg&oldid=375571745.]

As long as an item is contained in one set _or_ the other, it is included in the union of the sets. 

Similarly, the same comparison works for the set operation **intersection** and the boolean **and** operator.

![Set Intersection](/images/4/4.5.intersect.svg)^[File:Venn0001.svg. (2019, November 15). Wikimedia Commons, the free media repository. Retrieved 02:37, February 8, 2020 from https://commons.wikimedia.org/w/index.php?title=File:Venn0001.svg&oldid=375571733.]

Once again, if an item is contained in the first set _and_ the second set, it is contained in the intersection of those sets.

## When to Use a Set

A set is a great choice when we know that our program should prevent duplicate items from being added to a data structure. Likewise, if we know we'll be using some of the specific operations that are unique to sets, then a set is an excellent choice. 

Of course, if we aren't sure that our data structure will only store unique items, we won't be able to use a set. 


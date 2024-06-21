---
title: "Lists"
weight: 15
pre: "3. "
disableMathJax: false
---
The _list_ data structure is the simplest form of a linear data structure. As we can guess from the definition, a list is simply a grouping of data that is presented in a given order. With lists, not only do the elements in the list matter, but the order matters as well. It's not simply enough to state that elements $8$, $6$ and $7$ are in the list, but generally we also know that $8$ comes before $6$, which comes before $7$.

We've already learned about arrays, which are perfect examples of lists in programming. In fact, Python uses the data type `list` in the same way most other programming languages use arrays. Other programming languages, such as Java, provide a `list` data structure through their standard libraries.

## List Operations

One important way to classify data structures is by the operations they can perform on the data. Since a list is the simplest version of a linear data structure, it has several important operations it can perform:

* **insert** - inserts an element anywhere in the list, including at the beginning or the end;
* **remove** - removes an element from anywhere in the list, including at the beginning or the end;
* **find** - finds the location of the given element in the list, usually given as an _index_ just like an array index;
* **get** - returns the element at a given location, similar to using an array index to retrieve an element from an array; and
* **size** - returns the number of elements in the list.

For example, let's look at the **insert** operation. Assume we have the list shown in the following diagram:

![List Data Structure](/images/4/4.2.list.png)

Then, we decide we'd like to add the element $4$ at index $3$ in this list. So, we can think of this like trying to place the element in the list as shown below:

![List Before Insert](/images/4/4.3.before.png)

Once we insert that element, we then shift all of the other elements back one position, making the list one element larger. The final version is shown below:

![List After Insert](/images/4/4.3.after.png)

Lists are a very powerful data structure, and one of the most commonly used in a variety of programs. While arrays may seem very flexible, their static size and limited operations can sometimes make them more difficult to use than they are worth. Many programmers choose to use the more flexible list data structure instead. 

## When to Use a List

When deciding which data structure to use, lists are best when we might be adding or removing data from anywhere in the list, but we want to maintain the ordering between elements. As we'll see on the later pages, we can have more specific types of structures for particular ways we intend to add and remove data from our structure, but lists are a great choice if neither of those are a good fit.

---
title: "Types of Data"
weight: 10
pre: "2. "
---

{{< youtube pcFgY09EWmk  >}}

The first step toward determining which data structure to use relies heavily on the format of the data. By looking at the data and trying to understand what it contains and how it works, we can get a better idea of what data structure would work best to represent the data. Here, we will discuss some main types of data that we could encounter.

### Unique

Unique data is the type of data where each element in a group must be unique - there can be no duplicates. However, in many cases the data itself doesn't have a sequence or fixed ordering, we simply care if an element is present in the group or not. Some examples of unique data:
- car license plates
- personnel ID badge numbers

This data is best stored in the **set** data structure, usually built using a hash table as we learned previously. 

However, many times this data may be included along with other data (a person's ID number is part of the person's record), so sets are rarely used in practice. Instead, we can simply modify other data structures to enforce the uniqueness property we desire on those attributes. In addition, we see this concept come up again in relational databases, where particular attributes can be assigned a property to enforce the rule that each element must be unique. 

### Linear

Linear data refers to data that has a sequence or fixed ordering. This can include
- a series of characters
- a list of steps 
- a log of actions taken over time

This data is typically stored in the **array** or **linked list** data structure, depending on how we intend to use it and what algorithms will be performed on the data. 

We can think of this type of data as precisely one after another. This means that from one element there will be exactly one "next" element.

Finally, we can also adapt these data structures to represent FIFO (first-in, first-out) and LIFO (last-in, first-out) data structures using **queues** and **stacks**. As we saw previously, most implementations of queues and stacks are simply adaptations of existing linear data structures, usually the linked list. 

### Associative

Associative data is data where a key is associated with a value, usually in order to quickly find and retrieve the value based on its key. Some examples are:
- student records associated with a student ID
- tax forms stored with a social security number

We typically use a **hash table** to store this data in our programs.

However, in many cases this data could also be stored in a relational database just as easily, and in most industry programs that may also be a good choice here. Since we haven't yet learned about relational databases, we'll just continue to use hash tables for now. 

### Hierarchical

Hierarchical data refers to data where elements can be seen as above, below, or on the same level as other elements. This can include
- corporate ladders
- lineage 
- file systems

In contrast to linear data, hierarchical data can have multiple elements following a single element. In hierarchical data, each element has exactly one element prior to it. We typically use some form of a **tree** data structure to store hierarchical data. 

### Relational

Relational data refers to data where elements are 'close to' or 'far from' other elements. We can also think of this as 'more similar' and 'less similar' as well. This can include
- cities
- computer components
- social media posts
- graphics

In a relational data set, any element can be 'related' to any other element. We typically use a **graph** data structure to store relational data. 

### Prioritized

The last type of data we will discuss is prioritized data. Here, we want to store a data element along with a priority, and then be able to quickly retrieve the element with the highest or lowest priority, depending on use. This could include:
- process switching inside of a computer operating system
- delivery tasks to perform
- repairs needed on a device

For this data, we typically use an implementation of a **priority queue** based on a heap. It is important to remember that the heap does not store the data in sorted order - otherwise we would just use a linear data structure for this. Instead, it guarantees that the next element is always stored at the front of the structure for easy access, and it includes a process to quickly determine the new next element. We'll learn a bit more about why this is so helpful in the next chapter covering performance. 

{{% notice info %}}

It is important to note that when we are given a set of requirements for a project, the developer may not use the words to classify the types of data. Based on what a user tells us, we want to be able to infer what kind of shape the data could take. 

{{% / notice %}}

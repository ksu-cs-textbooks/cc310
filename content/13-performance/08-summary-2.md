---
title: "Summary 2"
weight: 40
pre: "8. "
disableMathJax: false
---

### Stacks

A stack is a data structure with two main operations that are simple in concept. One is the `push` operation that lets you put data into the data structure and the other is the `pop` operation that lets you get data out of the structure. 

A stack is what we call a Last In First Out (LIFO) data structure. That means that when we `pop` a piece of data off the stack, we get the last piece of data we put on the stack. 

### Queues

A queue data structure organizes data in a First In, First Out (FIFO) order: the first piece of data put into the queue is the first piece of data available to remove from the queue. 

### Lists

A list is a data structure that holds a sequence of data, such as the shopping list shown below. Each list has a head item and a tail item, with all other items placed linearly between the head and the tail.

### Sets

A set is a collection of elements that are usually related to each other.

### Hash Tables

A hash table is an unordered collection of key-value pairs, where each key is unique.

The following table compares the best- and worst-case processing time for many common data structures and operations, expressed in terms of $N$, the number of elements in the structure. 
| Data Structure | Insert Best | Insert Worst | Access Best | Access Worst | Find Best | Find Worst | Delete Best | Delete Worst |
|:--------------:|:-----------:|:------------:|:-----------:|:------------:|:---------:|:----------:|:-----------:|:------------:|
| Unsorted Array | $1$ | $1$ | $1$ | $1$ | $N$ | $N$ | $N$ | $N$ |
| Sorted Array | $\text{lg}(N)$ | $N$ | $1$ | $1$ | $\text{lg}(N)$ |$\text{lg}(N)$ | $\text{lg}(N)$ | $N$ |
| Array Stack (LIFO) |$1$ |$1$ |$1$ |$1$ | $N$ | $N$ | $1$ | $1$ |
| Array Queue (FIFO) |$1$ |$1$ |$1$ |$1$ | $N$ | $N$ | $1$ | $1$ |
| Unsorted Linked List |$1$ |$1$ | $N$ | $N$ | $N$ | $N$ | $N$ | $N$ |
| Sorted Linked List | $N$ | $N$ | $N$ | $N$ | $N$ | $N$ | $N$ | $N$ |
| Linked List Stack (LIFO) |$1$ |$1$ |$1$ |$1$ | $N$ | $N$ |$1$ | $1$
| Linked List Queue (FIFO) |$1$ |$1$ |$1$ |$1$ | $N$ | $N$ |$1$ | $1$
| Hash Table |$1$ | $N$ |$1$ | $N$ | $N$ | $N$ |$1$ | $N$ |

---
title: "Data Structure Performance"
weight: 10
pre: "2. "
---
Data structures that are used in our programs can be characterized in terms of two performance attributes: processing time and memory usage.

We will not worry about memory usage at this point, since most of the memory used in these data structures is consumed by the data that we are storing. More technically, we would say that the memory use of a data structure containing N elements is on the order of $N$ size. However, some structures, such as doubly linked lists, must maintain both the next and previous pointers along with each element, so there can be a significant amount of memory overhead. That is something we should keep in mind, but only in cases where we are dealing with a large amount of data and are worried about memory usage.

When evaluating the processing time of a data structure, we are most concerned with the algorithms used to add, remove, access, and find elements in the data structure itself. There are a couple of ways we can evaluate these operations.

* **Empirically** – we can simply measure the real-world time it takes to perform these actions on the data we are expecting our program to process, and then review the results in a spreadsheet or plot them on a graph to compare them. This gives us a good idea of how well the program will work, but it does not give us a very deep understanding of why the data structure performs that way. 
* **Mathematically** – the other option is to mathematically evaluate the algorithm by reviewing the code and determining the order of time it takes relative to the size of the input. While this does not give us an actual, real-world value for the time it takes to perform an operation, it allows us to easily compare different operations and data structures based on how they'd perform given the same size of input. We typically discuss both the best-case and worst-case processing times for each operation. 

Throughout this course, we have included mathematical descriptions of the processing time of most major operations on the data structures we have covered. 

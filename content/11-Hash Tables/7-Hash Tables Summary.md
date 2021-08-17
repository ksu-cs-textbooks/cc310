---
title: "Hash Tables Summary"
weight: 35
pre: "7. "
---
In this module, we introduced the concept of a hash table, which is a data structure that provides efficient insertion and retrieval operations. We introduced the three essential elements of hash tables:

1. An array that holds buckets where key-value pairs are stored,
1. A hash function that maps a key to a specific array index, and
1. A set of buckets that allow the hash table to store multiple key-value pairs whose keys map to the same index in the array. 

We then discussed how to implement a hash table class. In our implementation, we chose to use built-in, language-specific hash code functions to generate the indexes into our array. We also used doubly linked lists to implement our buckets as linked lists are very flexible and provide constant time insertion operations. 
To demonstrate the effectiveness of hash tables, we re-implemented our set class using hash tables instead of linked lists. In many ways, the re-implementation was almost identical to the linked list implementation since many of the operations found in hash tables are almost identical to those found in linked lists. We also noted that the biggest advantage of implementing sets with hash tables is the (almost!) constant time retrieval operations provided by hash tables.

---
title: "Data Structure Uses"
weight: 45
pre: "9. "
---
Throughout this course, we have looked at a few ways we can use the data structures we have already learned to do something useful. In this module, we will look at a few of those examples again, as well as a few more interesting uses of the data structures that we have built. 

## Arrays and Linked Lists as Stacks, Queues, and Sets

First and foremost, it is important to understand that we can implement many of the simpler data structures such as stacks, queues and sets using both arrays and linked lists. In fact, from a certain point of view, there are only two commonly used containers for data – the array and the linked list. Nearly all other data structures are a variant of one of those two approaches or a combination of both. 

Earlier in this chapter, we discussed some of the performance implications that arise when using arrays or linked lists to implement stacks and queues. In practice, we need to understand how we will be using our data in order to choose between the two approaches.

## Sets in Compilers and Interpreters

One unique use of sets appears in the code of compilers and interpreters. In each case, a programming language can only have one instance of a variable with a given name at any one time. So, we can think of the variables in a program as a set. In the code for a compiler or interpreter, we might find many instances of sets that are used to enforce rules that require each variable or function name to be unique. 

Of course, this same property becomes important in even larger data storage structures, such as a relational database. For example, a database may include a column for a username or identification number which must be unique, such that no two entries can be the same. Once again, we can use a set to help enforce that restriction.

## Hash Tables as Sets and Indexers

Hash tables are a great example of a data structure that effectively combines arrays and linked lists to increase performance. The best way to understand this is through the analysis of a set implemented using a hash table instead of a linked list.

When we determine if an element is already contained in a set based on a linked list, we must perform a linear search which runs on the order of $N$ time. The same operation performed on a set based on a hash table runs in constant time in the best case. This is because we can use the result of the hash function to jump directly to the bucket where the item should be stored, if it exists.

This same trick is used in large relational databases. If we have a database with a million rows, we can define an _index_ for a column that allows us to quickly jump to entries without searching the entire database. To look up a particular entry using an index, we can calculate its hash, find the entry in the index, and then use the link in that index element to find the record in the database. 

Finally, we can also use hash tables to build efficient indexes for large amounts of text data. Consider a textbook, for example. Most textbooks contain an index in the back that gives the page locations where particular terms are discussed. How can we create that index? We can iterate through each word in the textbook, but for each one we will have to search through the existing words in the index to see if that page is already listed for that word. That can be very slow if we must use a linear search through a linked list. However, if we use a hash table to store the index, the process of updating entries can be done in nearly constant time!

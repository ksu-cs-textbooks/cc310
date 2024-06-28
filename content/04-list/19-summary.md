---
title: "Lists Summary"
weight: 95
pre: "19. "
---

In this module we looked at the stack data structure. Stacks are a "last in first out" data structure that use two main operations, push and pop, to put data onto the stack and to remove data off of the stack. Stacks are useful in many applications including text editor "undo" and web browser "back" functions. 

We also saw the queue data structure. Queues are a "first in first out" data structure that use two main operations, enqueue and dequeue, to put data into the queue and to remove data from the queue. Queues are useful in many applications including the scheduling of tasks, sharing of resources, and processing of messages in the proper order. 

Finally, we introduced the concept of a linked list, discussing both singly and doubly linked lists. Both kinds of lists are made up of nodes that hold data as well as references (also known as pointers) to other nodes in the list. Singly linked lists use only a single pointer, `next`, to connect each node to the next node in the list. While simple, we saw that a singly linked list allowed us to efficiently implement a stack without any artificial bounds on the number of items in the list. 

With doubly linked lists, we added a `previous` pointer that points to the previous node. This makes the list more flexible and makes it easier to insert and remove nodes from the list. We also added a `tail` pointer to the class, which keeps track of the last node in the list. The `tail` pointer significantly increased the efficiency of working with nodes at the end of the list. Adding the `tail` pointer allowed us to implement all the major queue operations in constant time.

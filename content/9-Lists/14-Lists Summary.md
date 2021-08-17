---
title: "Lists Summary"
weight: 70
pre: "14. "
---
In this module, we introduced the concept of a linked list, discussing both singly and doubly linked lists. Both kinds of lists are made up of nodes that hold data as well as references (also known as pointers) to other nodes in the list. Singly linked lists use only a single pointer, `next`, to connect each node to the next node in the list. While simple, we saw that a singly linked list allowed us to efficiently implement a stack without any artificial bounds on the number of items in the list. 

With doubly linked lists, we added a `previous` pointer that points to the previous node. This makes the list more flexible and makes it easier to insert and remove nodes from the list. We also added a `tail` pointer to the class, which keeps track of the last node in the list. The `tail` pointer significantly increased the efficiency of working with nodes at the end of the list. Adding the `tail` pointer allowed us to implement all the major queue operations in constant time.

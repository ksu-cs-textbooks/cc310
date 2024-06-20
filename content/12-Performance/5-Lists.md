---
title: "Lists"
weight: 25
pre: "5. "
---
{{< youtube f8jtcC4p6BM  >}}

## Unsorted Linked List

![Unsorted Linked List](/images/12/12.5.ulist.png)
 
The next data structure we learned about is the linked list. Specifically, we will look at the doubly linked list in this example, but in most instances the performance of a singly linked list is comparable.

With a linked list, the process of inserting an element at either the beginning or the end is a constant time operation since we maintain both a head and a tail reference. All we must do is create a new node and update a few references and we are good to go. 

However, if we would like to access a specific element somewhere in the list, we will have to iterate through the list starting from either the head or the tail until we find the element we need. So, that operation runs in order $N$ time. This is the major difference between linked lists and arrays: with an array, we can directly access items using the array index, but with linked lists we must iterate to get to that element. This becomes important in the next section when we discuss the performance of a sorted linked list. 

Similarly, the process of finding an element also requires iterating through the list, which is an operation that runs in order $N$ time. 

Finally, if we want to find and delete an element, that also runs in order $N$ time since we must search through the list to find the element. Once we have found the element, the process of deleting that element is a constant time operation. So, if we use our list iterator methods in an efficient manner, the actual run time may be more efficient than this analysis would lead us to believe. 

## Sorted Linked List

![Sorted Linked List](/images/12/12.5.slinked.png)
 
We have not directly analyzed the performance of a sorted linked list in this course, but hopefully the analysis makes sense based on what we have learned before. Since the process of iterating through a linked list runs in order of $N$ time, every operation required to build a sorted linked list is limited by that fact.

For example, if we want to insert an element into a list in sorted order, we must simply iterate through the list to find the correct location to insert it. Once we've found it, the process of inserting is actually a constant time operation since we don't have to shift any elements around, but because we can't use binary search on a linked list, we don't have any way to take advantage of the fact that the list is sorted.

The same problem occurs when we want to search for a particular element. Since we cannot use binary search to jump around between various elements in the list, we are limited to a simple linear search process, which runs in order of $N$ time. 

Likewise, when we want to search and delete an element from the list, we must once again iterate through the entire list, resulting in an operation that runs in order $N$ time.

So, is there any benefit to sorting a linked list? Based on this analysis, not really! The purpose of sorting a collection is simply to make searching for a particular element faster. However, since we cannot use array indices to jump around a list like we can with an array, we do not see much of an improvement. 

However, in the real world, we can improve some of these linear algorithms by "short-circuiting" them. When we "short-circuit" an algorithm, we provide additional code that allows the algorithm to return early if it realizes that it will not succeed. 

For example, if we are searching for a particular element in a sorted list, we can add an if statement to check and see if the current element is greater than the element we are searching for. If the list is sorted in ascending order, we know that we have gone past the location where we expected to find our element, so we can just return without checking the rest of the list. While this does not change the mathematical analysis of the running time of this operation, it may improve the real-world empirical analysis of the operation. 

## Linked List Stack (LIFO) and Linked List Queue (FIFO)
 
 ![Unsorted Linked List](/images/12/12.5.ulist.png)
 
We already saw how to use the operations from a linked list to implement both a stack and a queue. Since those data structures restrict the operations we can perform a bit, it turns out that we can use a linked list to implement a stack and a queue with comparable performance to an array implementation. 

For example, inserting, accessing, and removing elements in a stack or a queue based on a doubly linked list are all constant time operations, since we can use the head and tail references in a doubly linked list to avoid the need to iterate through the entire list to perform those operations. In fact, the only time we would have to iterate through the entire list is when we want to find a particular element in the stack or the queue. However, since we cannot sort a stack or a queue, finding an element runs in order $N$ time, which is comparable to an array implementation. 

By limiting the actions we want to perform with our linked list, we can get a level of performance similar to an array implementation of a stack or a queue. It is a useful outcome that demonstrates the ability of different data structures to achieve similar outcomes.

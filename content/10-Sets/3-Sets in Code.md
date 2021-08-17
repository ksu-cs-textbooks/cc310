---
title: "Sets in Code"
weight: 15
pre: "3. "
---
{{% youtube qaO4iLtGo4o %}}

Different data structures can be used to represents sets and efficiently support their operations. Among the data structures considered so far, it is possible to use both lists and arrays to represent sets. Even though sets by definition are unordered, we could store the elements in order, which has its pros and cons. Storing elements in order will speed up the `contains` operation since we won't have to check each element in the set. However, it will also slow down insertions since we have to insert the elements in order. 

Further, storing elements in order will improve the efficiency of the union and intersection operations since we could compute both the union and the intersection in one pass (similar to merge sort). Likewise, we can speed up our searching for elements in the superset and subset operations by taking advantage of the ordering of elements.

Whether or not keeping the elements in order makes sense for your application depends on how many times you will actually insert data into the set, versus the number of times you will be using the other set operations.

## Arrays

We can use arrays to store sets, much like we did for array-based stacks or queues. In fact, if we implemented an array-based list, we could implement sets directly on top of that structure. Unfortunately, if we need to keep the set elements ordered for efficiency, we would compound the inefficiency of inserting or removing items from an array since we would have to move other elements in the array each time to keep it sorted. Even if we're not interested in sorting our set, we would still face the fixed-capacity issue and would have to manage the size of the set container using the `doubleCapacity` and `halveCapacity` operations. On the positive side, if we kept the set elements sorted in the array, we could use binary search to implement a very efficient `contains` operation.

## Linked Lists

We can also use linked lists to implement sets. Lists provide all of the operations we need to implement the basic set operations such as insert, remove, and list iterator.  The only property we need to implement is that sets do not include duplicate elements. This is easily taken care of by checking to see if the set contains an element before we insert it. Since linked lists are very flexible and don't require us to worry about capacity issues, we will use them as the basis for our set operations in this module.

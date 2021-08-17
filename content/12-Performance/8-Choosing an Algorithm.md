---
title: "Choosing an Algorithm"
weight: 40
pre: "8. "
---
There are many different algorithms we can use to sort our data, and some of them can be shown mathematically to be more efficient, even in the worst case. So, how should we choose which algorithm to use?

In practice, it really comes down to a variety of factors, based on the amount of data we expect our program to handle, the randomness of the data, and more. The only way to truly know which algorithm is the best is to empirically test all of them and choose the fastest one, but even that approach relies on us predicting the data that our program will be utilizing. 

Instead, here are some general guidelines we can use to help us select a sorting algorithm to use in our program.

* If we know that the data will be nearly sorted, with only a few elements out of place, we can use **bubble sort** to quickly fix those issues. Unlike many other sorting algorithms, it is very easy to modify the bubble sort code to terminate when the data is properly sorted after just a few iterations. While it is rare to find a data set that is nearly sorted, it is an interesting case to be aware of. 
* If we think our data will be truly random, or if we are not sure we have enough memory to store the data twice, we can use **quicksort** effectively. Since the data is random, we should avoid the worst case scenario that can happen when using quicksort. In most cases quicksort is one of the fastest sorting algorithms when used on real-world data.  In addition, quicksort does not have any additional memory requirements, so it can be used in place without creating a copy of the data. 
* If we are not sure what features our data will have, but we know we'll have enough memory to store the data twice, then **merge sort** is a good choice. Merge sort guarantees that the performance will be on the order of N lg(N) regardless of how the data is structured, but it typically requires more memory usage. 
* Interestingly, if we are dealing with a large set of data that will not fit in memory itself, **merge sort** is also a good choice. Merge sort was originally designed for sorting data stored on multiple removable disks or tapes. Each disk was sorted individually, and then two disks could be merged in sorted order on two more disks. Over time, the entire data set could be sorted by using just a few extra disks, even if it could not all be loaded into the computer at the same time.

Of course, the choice of which sorting algorithm to use is one of the most important decisions a programmer can make, and it is a great example of the fact that there are multiple ways to write a program that performs a particular task. Each possible program comes with various performance and memory considerations, and in many cases, there may not be a correct option. Instead, we must rely on our own knowledge and insight to choose the method that we feel would work best in any given situation.

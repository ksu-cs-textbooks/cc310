---
title: "Arrays"
weight: 20
pre: "4. "
disableMathJax: false
---

{{< youtube An_SzFppNJA  >}}

## Unsorted Array

![Unsorted Array](/images/12/12.4.uarray.png)
 
An unsorted array is the most basic data structure, and it is supported by nearly every programming language available. Inserting elements into the array is always a constant time operation since we can simply place it at the end of the array. Of course, this assumes that the array is large enough to hold all our data without needing to be resized. Since we are not worried about memory usage, this is a safe assumption. 

Likewise, since an array allows us to access elements directly by index, we can say that the time it takes to access any single element is also a constant time operation. 

Unfortunately, searching for an element is much more difficult. Since the array is unsorted, we would have to look through each element in the array to find a specific element, making the search operation run on the order of $N$ time.

Likewise, the process to find and delete a specific item from the list is also on the order of $N$ time, since we'd have to iterate through the list to find the element, remove it, and then shift all remaining elements forward one space in the array. 

Unsorted arrays work best when we simply need to store and access data quickly, but we are not really concerned with finding a specific element each time. Iterating across an entire array takes the same amount of time as finding a specific element, so arrays are great data structures to use when looping through data. As we saw in a previous module, we can probably search linearly through the array for a specific item as many as 7 times before it becomes more efficient to sort it first. 

## Sorted Array

![Sorted Array](/images/12/12.4.sarray.png)
 
We can improve on some aspects of the performance of an unsorted array by sorting it. Thankfully, we can make it easier by just sorting the data as we insert it into the array! However, by doing so, our insert operation now runs in the order of $\text{lg}(N)$ time in the best case.  This is because it must use a binary search process to figure out where to insert the data into the array. However, in the worst case, it must also shift all the elements after the inserted element back one space, which will make the insert operation run in the order of $N$ time. 

Thankfully, since the data is being stored in an array, we can still use array indexes to access single elements directly, making that operation constant time. In addition, now that the array is sorted, the process of finding a specific element is reduced to the order of $\text{lg}(N)$ time, a vast improvement over the performance of an unsorted array.

Finally, the process of finding and deleting a specific item can be improved to order of $\text{lg}(N)$ time in the best case, but the worst case once again involves shifting all of the elements in the array, which is on the order of $N$ time.

So, while having a sorted array allows us to improve the performance of finding specific elements, many of the other operations still have poor worst-case performance. Therefore, one of the important things we must consider when choosing whether to store data in a sorted or unsorted array is the number of times we'll be searching for specific elements vs. the number of times we'll just be inserting or iterating across the entire array. If we do more iterating, we may want to just use an unsorted array, but if we need to search for items repeatedly, a sorted array may be a better choice from a performance standpoint.

## Array Stack (LIFO) and Array Queue (FIFO)

![Stack](/images/12/12.4.stack.png)

![Queue](/images/12/12.4.queue.png)
 
Our array-based implementations of a stack and a queue are very performant examples of data structures based on arrays, simply because we can limit the operations that we perform to the most efficient ones possible.

For example, since we are only inserting in one position, the insert operation always runs in constant time. While the position may be different depending on the implementation, each data structure simply keeps track of the array index where the next one should be placed, eliminating the need to shift elements around.

Likewise, since we are only allowed to remove elements from one position in the array, we can once again avoid the need to shift elements around. Therefore, that operation also runs in constant time for both stacks and queues. 

We can also use the peek operation to access the next element in the stack or queue in constant time. Since it is array based, those operations only require the index of the element in the array to be known, which is a great advantage here. 

However, the find operation still runs in order $N$ time, since it must iterate through each element in the array to determine if the desired element exists in the structure. Thankfully, that operation is not used very often with stacks and queues since we are usually concerned only with the next element to be taken from the structure. 

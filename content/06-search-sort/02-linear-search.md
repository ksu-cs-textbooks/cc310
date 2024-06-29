---
title: "Linear Search"
weight: 10
pre: "2. "
---

{{< youtube -V75q4CnlXw  >}}

When searching for a number in an unordered array, our search algorithms are typically designed as functions that take two parameters:

1. the number to find, and
2. the array to search. 

Our search functions then return an index to the number within the array. 

In this module, we will develop a couple of examples of searching an array for a specific number. 

Finding the first occurrence of a number in an unordered array is a fairly straightforward process. A black box depiction of this function is shown below. There are two inputs, `array` and `number`, and a single output, the `index` of the first occurrence of the `number` in `array`. 

![Function Diagram](/images/7/7.2.function.png)
 
We can also include the search function as a method inside of the container itself. In that case, we don’t have to accept the container as a parameter, since the method will know to refer to the object it is part of. 

Of course, when we begin designing an algorithm for our function we should think about two items immediately: the preconditions and the postconditions of the function. For this function, they are fairly simple. 

The precondition for `find` is that the `number` provided as input is compatible with the type of data held by the provided `array`. In this case, we have no real stipulations on `array`. It does not need to actually have any data in it, nor does it have to be ordered or unordered. 

Our postcondition is also straightforward. The function should return the index of `number` if it exists in the array. However, if `number` is not found in the array, then `-1` is returned. Depending on how we wish to implement this function, it could also return another default index or throw an exception if the desired value is not found. However, most searching algorithms follow the convention of returning an invalid index of `-1` when the value is not found in the array, so that's what we'll use in our examples.

**Preconditions:**

* The number to be searched for is compatible with data in the array

**Postconditions:**

* The function returns the index of number in the array
* The function returns -1 if the number to be searched for is not found in the array

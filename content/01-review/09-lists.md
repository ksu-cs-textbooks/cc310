---
title: "Lists"
weight: 50
pre: "9. "
---

{{< youtube 9rzcp1hw_kg  >}}

![Post Office Boxes](/images/1/1.3.x.8.postofficeboxes.wikimedia.jpg)^[File:USPS Post office boxes 1.jpg. (2017, May 17). Wikimedia Commons, the free media repository. Retrieved 18:17, November 5, 2018 from https://commons.wikimedia.org/w/index.php?title=File:USPS_Post_office_boxes_1.jpg&oldid=244476438.]

Arrays allow us to store multiple values in the same variable, using an _index_ to determine which value we wish to store or retrieve from the array. We can think of arrays like a set of post office boxes. Each one has the same physical address, the post office, but within the post office we can find an individual box based on its own box number. 

Some programming languages, such as Java, use arrays that are statically sized when they are first created, and those arrays cannot be resized later. In addition, many languages that require variables to be declared with a type only allow a single variable type to be stored in an array. 

Other languages, such as Python, use _lists_ in place of arrays. List can be resized, and in untyped languages such as Python they can store different data types within the same list. 

## Arrays in Flowcharts & Pseudocode

The table below lists the flowchart blocks used to represent arrays, as well as the corresponding pseudocode:

| Operation | Flowchart | Pseudocode |
|:---------:|:---------:|:-----------|
| Declare Array | ![Declare Array Flowchart Block](/images/1/1.3.x.8.array1.png) | <pre><code>ARR = new array[5]</code></pre> |
| Store Item | ![Store Item in Array Flowchart Block](/images/1/1.3.x.8.array2.png) | <pre><code>ARR[0] = 5 </code></pre> |
| Retrieve Item | ![Retrieve Item from Array Flowchart Block](/images/1/1.3.x.8.array3.png) | <pre><code>X = ARR[0]</code></pre> |

## Lists in Python

Let's review the syntax for working with lists in Python.

### List Creation

To define a list in Python, we can simply place values inside of a set of square brackets `[]`, separated by commas `,`:

```python
arr = [1, 2]
arr2 = [1.2, 3.4]
```

We can also create an empty list by simply omitting any items inside the square brackets

```python
arr3 = []
```

### Adding Items

Once we've created a list in Python, we can add items to the end of the list using the `append()` method:

```python
arr4 = []
arr4.append(1)
arr4.append(2)
arr4.append(3)
```

### Accessing List Elements

Once the list is created, we can access individual items in the list by placing the _index_ in square brackets `[]` after the list's variable name:

```python
x = arr[2]
arr[1] = 5
```

### Multidimensional List

Python lists can also be created with multiple dimensions, simply by appending lists as elements in a base list. 

```python
two_dim_arr = []
two_dim_arr.append([1, 2, 3])
two_dim_arr.append([4, 5, 6])
```

They can also be created through the use of lists as individual elements in a list when it is defined:

```python
another_arr = [[1, 2, 3], [4, 5, 6]]
```

To access elements in a multidimensional list, simply include additional sets of square brackets containing an index `[]` for each dimenison:

```python
another_arr = [[1, 2, 3], [4, 5, 6]]
x = another_arr[1, 2]
another_arr[0, 1] = 5
```

### List Operations

There are several operations that can be performed on lists in Python as well:

```python
arr = [1, 2, 3, 4, 5]

# list length
length = len(arr)

# concatenation
arr2 = [6, 7]
arr3 = arr + arr2  # [1, 2, 3, 4, 5, 6, 7]

# slicing
b = arr[2:4]   # [3, 4]
```

### List Loops

Finally, we can use a special form of loop, called a **For Each** loop, to iterate through items in a list in Python:

```python
arr = [1, 2, 3, 4 5]

for i in arr:
    print(i)
```

Once important thing to note is that lists accessed within a **For Each** loop are read only. So, we cannot change the values stored in the list using this loop, but we can access them. If we want to change them, we should use a standard **For** loop to iterate through the indices of the list:

```python
arr = [1, 2, 3, 4, 5]

for i in range(0, len(arr)):
    arr[i] = arr[i] + 5
```

## References

* [An Informal Introduction to Python: Lists](https://docs.python.org/3/tutorial/introduction.html#lists)
* [Data Structures: More on Lists](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)

---
title: "Bubble Sort Pseudocode"
weight: 65
pre: "13. "
---
To describe our bubble algorithm, we can start with these basic preconditions and postconditions.

**Preconditions:**

* The array stores a type of elements which can be ordered.  

**Postconditions:**

* The array will be sorted in ascending order.

We can then represent this algorithm using the following pseudocode.

```tex
function BUBBLESORT(ARRAY)							            (1)
    # loop through the array multiple times
    loop INDEX from 0 to size of ARRAY – 1					    (2)
        # consider every pair of elements except the sorted ones
        loop INDEX2 from 0 to size of ARRAY – 2 – INDEX			(3)
            if ARRAY[INDEX2] > ARRAY[INDEX2 + 1] then			(4)
                # swap elements if they are out of order
                TEMP = ARRAY[INDEX2]						    (5)
                ARRAY[INDEX2] = ARRAY[INDEX2 + 1]				(6)
                ARRAY[INDEX2 + 1] = TEMP					    (7)
            end if
        end loop
    end loop
end function
```

In this code, we begin by looping through every element in the array, as seen on line 2. Each time we run this outer loop, we'll lock one additional element in place at the end of the array. Therefore, we need to run it once for each element in the array. 

On line 3, we'll start at the beginning of the array and loop to the place where the sorted portion of the array begins. We know that after each iteration of the outer loop, the value `index` will represent the number of locked elements at the end of the array. We can subtract that value from the end of the array to find where we want to stop. 

Line 4 is a comparison between two adjacent elements in the array starting at the index `index2`. If they are out of order, we use lines 5 through 7 to swap them. That's really all it takes to do a bubble sort!

Looking at this code, we can describe the invariant of our outer loop as follows:

* The last `index` elements in the array are in sorted order, and
* The elements in the array have not changed, only their positions.

Notice how this differs from selection sort, since it places the sorted elements at the beginning of the array instead of the end. However, the result is the same, and by the end of the program we can show that each algorithm has fully sorted the array. 

---
title: "Quicksort Pseudocode"
weight: 95
pre: "19. "
---
Now that we've seen an example of how quicksort works, let's walk through the pseudocode of a quicksort function. The function itself is very simple, as shown below.

```tex
function QUICKSORT(ARRAY, START, END)			(1)
    # base case size <= 1		
    if START >= END then					    (2)		
        return						            (3)
    end if							            (4)
    PIVOTINDEX = PARTITION(ARRAY, START, END)	(5)
    QUICKSORT(ARRAY, START, PIVOTINDEX – 1)		(6)
    QUICKSORT(ARRAY, PIVOTINDEX + 1, END)		(7)
end function							        (8)
```

This implementation of quicksort uses a simple base case on lines 2 through 4 to check if the array is either empty, or contains one element. It does so by checking if the `START` index is greater than or equal to the `END` index. If so, it can assume the array is sorted and just return it without any additional changes.

The recursive case is shown on lines 5 – 7. It simply uses a helper function called `partition` on line 5 to partition the array based on a pivot value. That function returns the location of the pivot value, which is stored in `pivotIndex`. Then, on lines 6 and 7, the quicksort function is called recursively on the two partitions of the array, before and after the `pivotIndex`. That's really all there is to it!

Let's look at one way we could implement the `partition` function, shown below in pseudocode.

```tex
function PARTITION(ARRAY, START, END)			(1)
    PIVOTVALUE = ARRAY[END]				        (2)
    PIVOTINDEX = START					        (3)
    loop INDEX from START to END				(4)
        if ARRAY[INDEX] <= PIVOTVALUE			(5)
            TEMP = ARRAY[INDEX]        		    (6)
            ARRAY[INDEX] = ARRAY[PIVOTINDEX]	(7)
            ARRAY[PIVOTINDEX] = TEMP			(8)
            PIVOTINDEX = PIVOTINDEX + 1		    (9)
        end if						            (10)
    end loop							        (11)
    return PIVOTINDEX – 1					    (12)
```

This function begins on lines 2 and 3 by setting initial values for the `pivotValue` by choosing the last element in the array, and then setting the `pivotIndex` to 0. Then, the loop on lines 4 through 11 will look at each element in the array, determine if it is less than or equal to `pivotValue`, and swap that element with the element at `pivotIndex` if so, incrementing `pivotIndex` after each swap. 

At the end, the value that was originally at the end of the array will be at location `pivotIndex – 1`, so we will return that value back to the `quicksort` function so it can split the array into two parts based on that value. 

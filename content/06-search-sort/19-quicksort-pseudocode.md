---
title: "Quicksort Pseudocode"
weight: 95
pre: "19. "
---

Now that we've seen an example of how quicksort works, let's walk through the pseudocode of a quicksort function. The function itself is very simple, as shown below.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function QUICKSORT(ARRAY, START, END)
    # base case size <= 1
    if START >= END then
        return
    end if
    PIVOTINDEX = PARTITION(ARRAY, START, END)
    QUICKSORT(ARRAY, START, PIVOTINDEX – 1)
    QUICKSORT(ARRAY, PIVOTINDEX + 1, END)
end function
{{< /highlight >}}

This implementation of quicksort uses a simple base case on lines 3 through 5 to check if the array is either empty, or contains one element. It does so by checking if the `START` index is greater than or equal to the `END` index. If so, it can assume the array is sorted and just return it without any additional changes.

The recursive case is shown on lines 6 - 8. It simply uses a helper function called `partition` on line 6 to partition the array based on a pivot value. That function returns the location of the pivot value, which is stored in `pivotIndex`. Then, on lines 7 and 8, the quicksort function is called recursively on the two partitions of the array, before and after the `pivotIndex`. That's really all there is to it!

Let's look at one way we could implement the `partition` function, shown below in pseudocode.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function PARTITION(ARRAY, START, END)
    PIVOTVALUE = ARRAY[END]
    PIVOTINDEX = START
    loop INDEX from START to END
        if ARRAY[INDEX] <= PIVOTVALUE
            TEMP = ARRAY[INDEX]
            ARRAY[INDEX] = ARRAY[PIVOTINDEX]
            ARRAY[PIVOTINDEX] = TEMP
            PIVOTINDEX = PIVOTINDEX + 1
        end if
    end loop
    return PIVOTINDEX – 1
{{< /highlight >}}

This function begins on lines 2 and 3 by setting initial values for the `pivotValue` by choosing the last element in the array, and then setting the `pivotIndex` to 0. Then, the loop on lines 4 through 11 will look at each element in the array, determine if it is less than or equal to `pivotValue`, and swap that element with the element at `pivotIndex` if so, incrementing `pivotIndex` after each swap. 

At the end, the value that was originally at the end of the array will be at location `pivotIndex – 1`, so we will return that value back to the `quicksort` function so it can split the array into two parts based on that value. 

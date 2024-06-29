---
title: "Merge Sort Pseudocode"
weight: 80
pre: "16. "
---
Now that we've seen how merge sort works by going through an example, let's look at the pseudocode of a merge sort function.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function MERGESORT(ARRAY, START, END)
    # base case size == 1
    if END - START + 1 == 1 then
        return
    end if
    # base case size == 2
    if END - START + 1 == 2 then
        # check if elements are out of order
        if ARRAY[START] > ARRAY[END] then
            # swap if so
            TEMP = ARRAY[START]
            ARRAY[START] = ARRAY[END]
            ARRAY[END] = TEMP
        end if
        return
    end if
    # find midpoint
    HALF = int((START + END) / 2)
    # sort first half
    MERGESORT(ARRAY, START, HALF)
    # sort second half
    MERGESORT(ARRAY, HALF + 1, END)
    # merge halves
    MERGE(ARRAY, START, HALF, END)
end function
{{< /highlight >}}

This function is a recursive function which has two base cases. The first base case is shown in lines 3 through 5, where the size of the array is exactly 1. In that case, the array is already sorted, so we just return on line 4 without doing anything.

The other base case is shown in lines 7 through 15. In this case, the element contains just two elements. We can use the if statement on line 9 to check  if those two elements are in the correct order. If not, we can use lines 11 through 13 to swap them, before returning on line 15.

If neither of the base cases occurs, then we reach the recursive case starting on line 18. First, we'll need to determine the midpoint of the array, which is just the average of the `start` and `end` variables. We'll need to remember to make sure that value is an integer by truncating it if needed. 

Then, on lines 20 and 22 we make two recursive calls, each one focusing on a different half of the array. Once each of those calls returns, we can assume that each half of the array is now sorted. 

Finally, in line 24 we call a helper function known as `merge` to merge the two halves together. The pseudocode for that process is below. 

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function MERGE(ARRAY, START, HALF, END)
    TEMPARRAY = new array[END – START + 1]
    INDEX1 = START
    INDEX2 = HALF + 1
    NEWINDEX = 0
    loop while INDEX1 <= HALF and INDEX2 <= END
        if ARRAY[INDEX1] < ARRAY[INDEX2] then
            TEMPARRAY[NEWINDEX] = ARRAY[INDEX1]
            INDEX1 = INDEX1 + 1
        else
            TEMPARRAY[NEWINDEX] = ARRAY[INDEX2]
            INDEX2 = INDEX2 + 1
        end if
        NEWINDEX = NEWINDEX + 1
    end loop
    loop while INDEX1 <= HALF
        TEMPARRAY[NEWINDEX] = ARRAY[INDEX1]
        INDEX1 = INDEX1 + 1
        NEWINDEX = NEWINDEX + 1
    end loop
    loop while INDEX2 <= END
        TEMPARRAY[NEWINDEX] = ARRAY[INDEX2]
        INDEX2 = INDEX2 + 1
        NEWINDEX = NEWINDEX + 1
    end loop
    loop INDEX from 0 to size of TEMPARRAY – 1
        ARRAY[START + INDEX] = TEMPARRAY[INDEX]
    end loop
end function
{{< /highlight >}}

The `merge` function begins by creating some variables. The `tempArray` will hold the newly merged array. `Index1` refers to the element in the first half that is being considered, while `index2` refers to the element in the second half. Finally, `newIndex` keeps track of our position in the new array. 

The first loop starting on line 6 will continue operating until one half or the other has been completely added to the temporary array. It starts by comparing the first element in each half of the array. Then, depending on which one is smaller, it will place the smaller of the two in the new array and increment the indexes. 

Once the first loop has completed, there are two more loops starting on lines 16 and 21. However, only one of those loops will actually execute, since only one half of the array will have any elements left in it to be considered. These loops will simply copy the remaining elements to the end of the temporary array.

Finally, the last loop starting on line 26 will copy the elements from the temporary array back into the source array. At this point, they will be properly merged in sorted order.  

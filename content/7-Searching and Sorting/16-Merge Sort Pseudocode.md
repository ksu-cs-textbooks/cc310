---
title: "Merge Sort Pseudocode"
weight: 80
pre: "16. "
---
Now that we've seen how merge sort works by going through an example, let's look at the pseudocode of a merge sort function.

```tex
function MERGESORT(ARRAY, START, END)			(1)
    # base case size == 1		
    if END - START + 1 == 1 then				(2)		
        return						            (3)
    end if							            (4)
    # base case size == 2
    if END - START + 1 == 2 then				(5)
        # check if elements are out of order
        if ARRAY[START] > ARRAY[END] then		(6)
            # swap if so
            TEMP = ARRAY[START]				    (7)
            ARRAY[START] = ARRAY[END]			(8)
            ARRAY[END] = TEMP				    (9)
        end if						            (10)
        return						            (11)
    end if							            (12)
    # find midpoint
    HALF = int((START + END) / 2)			    (13)
    # sort first half
    MERGESORT(ARRAY, START, HALF)			    (14)
    # sort second half
    MERGESORT(ARRAY, HALF + 1, END)			    (15)
    # merge halves
    MERGE(ARRAY, START, HALF, END)			    (16)
end function							        (17)
```

This function is a recursive function which has two base cases. The first base case is shown in lines 2 through 4, where the size of the array is exactly 1. In that case, the array is already sorted, so we just return on line 3 without doing anything.

The other base case is shown in lines 5 through 11. In this case, the element contains just two elements. We can use the if statement on line 6 to check  if those two elements are in the correct order. If not, we can use lines 7 through 9 to swap them, before returning on line 11.

If neither of the base cases occurs, then we reach the recursive case starting on line 13. First, we'll need to determine the midpoint of the array , which is just the average of the `start` and `end` variables. We'll need to remember to make sure that value is an integer by truncating it if needed. 

Then, on lines 14 and 15 we make two recursive calls, each one focusing on a different half of the array. Once each of those calls returns, we can assume that each half of the array is now sorted. 

Finally, in line 16 we call a helper function known as `merge` to merge the two halves together. The pseudocode for that process is below. 

```tex
function MERGE(ARRAY, START, HALF, END)			    (1)
    TEMPARRAY = new array[END – START + 1]			(2)
    INDEX1 = START							        (3)
    INDEX2 = HALF + 1						        (4)
    NEWINDEX = 0							        (5)
    loop while INDEX1 <= HALF and INDEX2 <= END		(6)
        if ARRAY[INDEX1] < ARRAY[INDEX2] then		(7)
            TEMPARRAY[NEWINDEX] = ARRAY[INDEX1]		(8)
            INDEX1 = INDEX1 + 1					    (9)
        else								        (10)
            TEMPARRAY[NEWINDEX] = ARRAY[INDEX2]		(11)
            INDEX2 = INDEX2 + 1					    (12)
        end if							            (13)
        NEWINDEX = NEWINDEX + 1					    (14)
    end loop								        (15)
    loop while INDEX1 <= HALF					    (16)
        TEMPARRAY[NEWINDEX] = ARRAY[INDEX1]			(17)
        INDEX1 = INDEX1 + 1					        (18)
        NEWINDEX = NEWINDEX + 1					    (19)
    end loop								        (20)
    loop while INDEX2 <= END					    (21)
        TEMPARRAY[NEWINDEX] = ARRAY[INDEX2]			(22)
        INDEX2 = INDEX2 + 1					        (23)
        NEWINDEX = NEWINDEX + 1					    (24)
    end loop								        (25)
    loop INDEX from 0 to size of TEMPARRAY – 1		(26)
        ARRAY[START + INDEX] = TEMPARRAY[INDEX]		(27)
    end loop								        (28)
end function								        (29)
```

The `merge` function begins by creating some variables. The `tempArray` will hold the newly merged array. `Index1` refers to the element in the first half that is being considered, while `index2` refers to the element in the second half. Finally, `newIndex` keeps track of our position in the new array. 

The first loop starting on line 6 will continue operating until one half or the other has been completely added to the temporary array. It starts by comparing the first element in each half of the array. Then, depending on which one is smaller, it will place the smaller of the two in the new array and increment the indexes. 

Once the first loop has completed, there are two more loops starting on lines 16 and 21. However, only one of those loops will actually execute, since only one half of the array will have any elements left in it to be considered. These loops will simply copy the remaining elements to the end of the temporary array.

Finally, the last loop starting on line 26 will copy the elements from the temporary array back into the source array. At this point, they will be properly merged in sorted order.  

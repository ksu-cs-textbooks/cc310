---
title: "Iterative Binary Search"
weight: 115
pre: "23. "
---
The binary search algorithm is easily implemented in both an iterative and recursive function. We'll look at both versions and see how they compare.

The pseudocode for an iterative version of binary search is shown below.

```tex
function BINARYSEARCH(ARRAY, VALUE)			    (1)
    START = 0						            (2)
    END = size of ARRAY - 1				        (3)
    loop while START <= END				        (4)
        MIDDLE = INT((START + END) / 2)		    (5)
        if ARRAY[MIDDLE] == VALUE then			(6)
            return MIDDLE					    (7)
        else if ARRAY[MIDDLE] > VALUE then		(8)
            END = MIDDLE – 1				    (9)
        else if ARRAY[MIDDLE] < VALUE then		(10)
            START = MIDDLE + 1				    (11)
        end if						            (12)
    end loop							        (13)
    return -1						            (14)
end function							        (15)
```

This function starts by setting the initial values of `start` and `end` on lines 2 and 3 to the first and last indexes in the array, respectively. Then, the loop starting on line 4 will repeat while the `start` index is less than or equal to the `end` index. If we reach an instance where `start` is greater than `end`, then we have searched the entire array and haven't found our desired value. At that point the loop will end and we will return -1 on line 14.

Inside of the loop, we first calculate the `middle` index on line 5. Then on line 6 we check to see if the middle element is our desired value. If so, we should just return the `middle` index and stop. It is important to note that this function will return the index to an instance of `value` in the array, but it may not be the first instance. If we wanted to find the first instance, we'd add a loop at line 7 to move forward in the array until we were sure we were at the first instance of `value` before returning. 

If we didn't find our element, then the if statements on lines 8 and 10 determine which half of the array we should look at. Those statements update either `end` or `start` as needed, and then the loop repeats. 

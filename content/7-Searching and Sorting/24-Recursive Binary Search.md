---
title: "Recursive Binary Search"
weight: 120
pre: "24. "
---
The recursive implementation of binary search is very similar to the iterative approach. However, this time we also include both `start` and `end` as parameters, which we update at each recursive call. The pseudocode for a recursive binary search is shown below.

```tex
function BINARYSEARCHRECURSE(ARRAY, VALUE, START, END)			       (1)
    # base case
    if START > END then								                   (2)
        return -1									                   (3)
    end if										                       (4)
    MIDDLE = INT((START + END) / 2)						               (5)
    if ARRAY[MIDDLE] == VALUE then						               (6)
        return MIDDLE								                   (7)
    else if ARRAY[MIDDLE] > VALUE then						           (8)
        return BINARYSEARCHRECURSE(ARRAY, VALUE, START, MIDDLE – 1)	   (9)		
    else if ARRAY[MIDDLE] < VALUE then						           (10)
        return BINARYSEARCHRECURSE(ARRAY, VALUE, MIDDLE + 1, END)	   (11)
    end if										                       (12)
end function										                   (13)
```

The recursive version moves the loop's termination condition to the base case, ensuring that it returns -1 if the `start` index is greater than the `end` index. Otherwise, it performs the same process of calculating the `middle` index and checking to see if it contains the desired `value`. If not, it uses the recursive calls on lines 9 and 11 to search the first half or second half of the array, whichever is appropriate. 

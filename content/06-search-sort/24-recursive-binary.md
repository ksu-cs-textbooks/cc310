---
title: "Recursive Binary Search"
weight: 120
pre: "24. "
---

The recursive implementation of binary search is very similar to the iterative approach. However, this time we also include both `start` and `end` as parameters, which we update at each recursive call. The pseudocode for a recursive binary search is shown below.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function BINARYSEARCHRECURSE(ARRAY, VALUE, START, END)
    # base case
    if START > END then
        return -1
    end if
    MIDDLE = INT((START + END) / 2)
    if ARRAY[MIDDLE] == VALUE then
        return MIDDLE
    else if ARRAY[MIDDLE] > VALUE then
        return BINARYSEARCHRECURSE(ARRAY, VALUE, START, MIDDLE – 1)	
    else if ARRAY[MIDDLE] < VALUE then
        return BINARYSEARCHRECURSE(ARRAY, VALUE, MIDDLE + 1, END)
    end if
end function
{{< /highlight >}}

The recursive version moves the loop's termination condition to the base case, ensuring that it returns -1 if the `start` index is greater than the `end` index. Otherwise, it performs the same process of calculating the `middle` index and checking to see if it contains the desired `value`. If not, it uses the recursive calls on lines 10 and 12 to search the first half or second half of the array, whichever is appropriate. 

---
title: "Selection Sort Pseudocode"
weight: 50
pre: "10. "
---

To describe our selection sort algorithm, we can start with these basic preconditions and postconditions.

**Preconditions:**

* The array stores a type of elements which can be ordered.

**Postconditions:**

* The array will be sorted in ascending order.

We can then represent this algorithm using the following pseudocode.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function SELECTIONSORT(ARRAY)
    loop INDEX from 0 to size of ARRAY – 2
      MININDEX = 0
        # find minimum index
        loop INDEX2 from INDEX to size of ARRAY – 1
            if ARRAY[INDEX2] < ARRAY[MININDEX] then
                MININDEX = INDEX
            end if
        end loop
        # swap elements
        TEMP = ARRAY[MININDEX]
        ARRAY[MININDEX] = ARRAY[INDEX]
        ARRAY[INDEX] = TEMP
    end loop
end function
{{< /highlight >}}

In this code, we begin by looping through every element in the array except the last one, as seen on line 2. We don't include this one because if the rest of the array is sorted properly, then the last element must be the maximum value. 

Lines 3 through 9 are basically the same as what we saw in our `findMin` function earlier. It will find the index of the minimum value starting at `INDEX` through the end of the array. Notice that we are starting at `INDEX` instead of the beginning. As the outer loop moves through the array, the inner loop will consider fewer and fewer elements. This is because the front of the array contains our sorted elements, and we don't want to change them once they are in place. 

Lines 11 through 13 will then swap the elements at `INDEX` and `MININDEX`, putting the smallest element left in the array at the position pointed to by index. 

We can describe the invariant of our outer loop as follows:

* The array from index 0 through `index` is sorted in ascending order.
* The elements in the array have not changed, only their positions.

The second part of the loop invariant is very important. Without that distinction, we could simply place new values into the array before `index` and satisfy the first part of the invariant. It is always important to specify that the array itself still contains the same elements as before. 

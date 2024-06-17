---
title: "Searching for a Minimum"
weight: 30
pre: "6. "
---
We may also want to search through a data structure to find an item with a specific property. For example, we could search for the student with the maximum age, or the minimum GPA. For this example, let's consider the case where we'd like to find the minimum value in an array of integers.

Searching for the minimum number in an unordered array is a different problem than searching for a specific number. First of all, we do not know what number we are searching for. And, since the array is not ordered, we will have to check each and every number in the array. 

The input parameters of our new function will be different from the `find` function above, since we do not have a number to search for. In this case, we only have an array of numbers as an input parameter. The output parameter, however, is the same. We still want to return the index of the minimum number in the array. In this case, we will return `-1` if there is no minimum number, which can only happen if there is no data in the array when we begin.

**Preconditions:**

* The data in the array can be sorted 

**Postconditions:**

* The function returns the minimum number of the data in the array
* The function returns -1 if the array is empty

Our preconditions and postconditions are also simple. Our precondition is simply that we have an array whose data can be sorted. This is important, because it means that we can compare two elements in the array and determine which one has a smaller value. Otherwise, we couldn't determine the minimum value at all!

Our postcondition is that we return the minimum number of the data in the array, or `-1` if the array is empty. 

The function `findMin` is shown below. First, we check to see if the array is empty. If it is, we simply return `-1` in line 3. If not, we assume the location `0` contains the minimum number in the array, and set `min` equal to 0 in line 5. Then we loop through each location in the array (starting with 1) in line 6 and set `min` equal to the minimum of the array data at the current `index`  and the data at `min`. (Note: if the array only has a single number in it, the for loop will not actually execute since `index` will be initialized to 1, which is already larger than the size of the `array – 1`, which is 0.) Once we complete the loop, we will be guaranteed that we have the index of the minimum number in the array. 

```tex
function FINDMIN(ARRAY) 						(1)
    if ARRAY is empty then						(2)
        return -1								(3)
    end if									    (4)
    MIN = 0									    (5)
    loop INDEX from 1 to size of ARRAY - 1	    (6)
        if ARRAY[INDEX] < ARRAY[MIN] 			(7)
            MIN = INDEX							(8)
        end if								    (9)
    end for									    (10)
    return MIN								    (11)
end function									(12)
```

Next, we will walk through the algorithm using our example array in the figure below. Step 1 shows the initial time through the loop. In line 5, `min` is set to `0` by default and in line 6, `index` is set equal to `1`. Line 7 then computes whether `array[1] < array[0]`. In this case, it is and we set `min = 1` (which is reflected in the next step where `min` has the value `1`). 

![Finding Minimum Diagram](/images/7/7.6.minimum.png)
 
Step 2 will end up comparing `array[2] < array[1]`, since `min` is now 1 and `index` has been incremented to 2 via the `for` loop. In this case, `array[2]` is less than `array[1]` so we update `min` again, this time to 2.

Step 3 follows the same process; however, this time the value in `array[3]` is 55, which is greater than the current minimum of 3 in `array[2]`. Therefore, `min` is not updated. Step 4 finds the minimum value in the array of `-3` at index 4 and so updates `min` to 4. However, steps 5, 6, and 7 do not find new minimum values. Thus, when the loop exits after Step 6, `min` is set to 4 and this value is returned to the calling program in line 11.

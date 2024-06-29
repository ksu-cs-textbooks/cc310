---
title: "Searching for the Last Value"
weight: 20
pre: "4. "
---

Our `find` algorithm above will find the first instance of `number` in the `array` and return the index of that instance. However, we might also be interested in finding the last instance of `number` in `array`. Looking at our original `find` algorithm, it should be easy to find the last value by simply searching the array in reverse order, as shown in the following figure.

![Linear Search Last Value](/images/7/7.4.linearreverse.png)
 
We will use the same example as above, except we will start searching backwards from the end of the array. In Step 1, we see that `index` is initialized to 7 and we compare `array[7]` against `number`, which are not the same. Thus, we continue to Step 2, where we decrement `index` to 6. Here `array[6]` is still not equal to `number`, so we continue in the loop. Finally, in Step 3, we decrement `index` to 5. Now `array[5]` contains the number `3`, which is equal to our `number` and we return the current `index` value.

Luckily for us, we can change our `for` loop index to decrement from the end of the array (`size of array - 1`) to the beginning (`0`). Thus, by simply changing line 3 in our original function, we can create a new function that searches for the last instance of `number` in `array`. The new function is shown below.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function REVERSEFIND(NUMBER, ARRAY)
    loop INDEX from size of ARRAY – 1 to 0 step -1
        if ARRAY[INDEX] == NUMBER
            return INDEX
        end if
    end for
    return -1
end function
{{< /highlight >}}

Obviously, the `for` loop in line 2 holds the key to searching our array in reverse order. We start at the end of the array by using the index `size of array - 1` and then decrement the value of `index` (via the `step -1` qualifier) each time through the loop until we reach 0. The remainder of the function works exactly like the `find` function.

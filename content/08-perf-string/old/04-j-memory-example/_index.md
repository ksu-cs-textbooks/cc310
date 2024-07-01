---
title: "Limitations Java"
weight: 20
pre: "4. "
---
{{< youtube mHOqqh-M2us  >}}

[Video Materials](video)


As a result of being immutable, strings can be cumbersome to work with in certain applications. When long strings or strings that we are continually appending to, such as in the memory example, we end up creating a lot of sizable copies. 

Recall from the memory example the block of pseudocode. 

```tex
1. function APPENDER(NUMBER, BASE)
2.     RESULT = ""
3.     loop I from 1 to NUMBER
4.         RESULT = RESULT + BASE
5.         if I MOD 2 = 0
6.             RESULT = RESULT + " "
7.         else
8.             RESULT = RESULT + ", " 
9.     end loop
10.    return RESULT
11. end function
```

In this example, what if we changed `RESULT` to a mutable type, say a list of strings for Python or a StringBuilder in Java. Once the loop is done, we can cast `RESULT` to a string. By changing just the one aspect of the code, we would make only one copy of `RESULT` and have far less character copies.

{{% notice info %}}

Java specifically has a [StringBuilder class](https://docs.oracle.com/javase/7/docs/api/java/lang/StringBuilder.html) which was created for this precise reason.

{{% / notice %}}

Consider the following, and note the slight changes on lines 2, 4, 6, 8 and the additional line 10.  

```tex
1. function APPENDER_LIST(NUMBER, BASE)
2.     RESULT = []
3.     loop I from 1 to NUMBER
4.         RESULT.APPEND(BASE) 
5.         if I MOD 2 = 0
6.             RESULT.APPEND(" ") 
7.         else
8.             RESULT.APPEND(", ")  
9.     end loop
10.    RESULT = "".JOIN(RESULT)
11.    return RESULT
12. end function
```

Now consider APPENDER_LIST(4,'abc')

- Initialization: We start by initializing the empty array. `RESULT` will hold the pointer `0x1`.
![Initialize](/images/13/1SB_mem_map1.png)

- I = 1: Now we have entered the loop and on line 4, we add more characters to our array. At this point, we would have only entry `0x1` in our heap and our variable `RESULT` would have the pointer `0x1`. Continuing through the code, line 5 determines if `I` is divisible by 2. In this iteration `I = 1`, so we take the else branch. We again add characters to our array.  In total, we have written 5 characters. We then increment I and move to the next iteration.  
![After 1st Loop](/images/13/1SB_mem_map3.png)

- I = 2: We continue the loop and on line 4, we add more characters to our array. We still have just one entry in memory and our pointer is still `0x1`. In this iteration, we have written 4 characters. We then increment `I` and move to the next iteration of the loop.
![After 2nd Loop](/images/13/1SB_mem_map5.png)

- I = 3: We continue the loop and on line 4, we add more characters to our array.  In this iteration, we have written 5 characters. We then increment `I` and thus `I = 4` breaking out of the loop. 
![After 3rd Loop](/images/13/1SB_mem_map7.png)

- Post-Loop: Once the loop breaks, we join the array to create the final string. This creates a new place in memory and changes RESULT to contain the pointer `0x2`.
![After Loop Breaks](/images/13/1SB_mem_map8.png)




We can do some further analysis of the memory that is required for this particular block. 
| Iteration | Memory Entries| Character Copies |
| ----------| --------------| -----------------|
| 1 | 2 | 8 |
| 2 | 2 | 17 |
| 3 | 2 | 26 |
| 4 | 2 | 35 |
| . | . | . |
| n | 2 | 9n - 1|


Again, you need not worry about creating these equations for this course. To illustrate the improvement even more explicitly, let's consider our previous example with 100K iterations. For APPENDER there were (2x100,000 - 1) = 200,001 memory entries and (9x100,000<sup>2</sup> + 7x100,000)/2 = 45 billion character copies. For APPENDER_LIST we now have just 2 memory entries and (9x100,000 - 1) = 899,999 character copies. This dramatic improvement was a result of changing our data structure ever so slightly. 


Reference: http://people.cs.ksu.edu/~rhowell/DataStructures/strings/stringbuilders.html

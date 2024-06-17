---
title: "Code Complexity"
weight: 60
pre: "12. "
---
Lastly, when analyzing a program, we must also consider the complexity of the code used to write the program. Code complexity can refer to many things, but in general we use it to describe how many lines of code are included the program, as well as how easy it is to understand what the program does.

## Lines of Code

One of the most common ways to measure the size of a program is the number of lines of code, or _LOC_, of the program. This can be a very rough estimate of the size of the program, since, in general, a longer program with more lines of code may be more complex than a shorter program with fewer lines.

So, if we can find a solution to a problem that requires many fewer lines of code than another solution, that is one factor to consider. Of course, the solution with fewer lines of code may be more complex in terms of time or space!

## Understandability

The other important measure of code complexity deals with how easy it is to understand what the program does. Sometimes we can write a program that only takes a few lines of code, but it is so complex that it is difficult to really understand how it works. 

For example, consider this line of pseudocode - can you determine what it does?

```
return (X > 0) and ((X % 10) + (INT((X % 100) / 10))) < 5
```

It is pretty difficult to understand. Can we rewrite this program to make it easier to understand? Consider the following code:

```
if X <= 0
    return FALSE
else
    ONES_PLACE = X % 10
    TENS_PLACE = X % 100
    SUM_LAST_TWO_DIGITS = TENS_PLACE + ONES_PLACE
    if SUM_LAST_TWO_DIGITS < 5
        return TRUE
    else
        return FALSE
    end if
end if
```

This program is pretty easy to follow. First, it will determine if `X` is 0 or a negative number, and return `FALSE` if so. Then, it will find the last two digits of the number, corresponding to the ones and the tens place, and sum them. Finally, if the sum of the last two digits is less than $5$, it will return `TRUE`. Otherwise, it will return `FALSE`. 

As it turns out, these two programs do the exact same thing! However, from the single line of code in the first program, it is very difficult to decipher exactly what it does. The second program, even though it is much longer, is much easier to understand. In addition, when run on a real computer, both of these programs will take nearly the same amount of time to run.

## Complexity Triad

As we've seen, we can describe the complexity of a program in terms of three values: the time it takes to run, the space it requires in memory, and the size and understandability of the code. However, how do we know which of those measures is the most important?

Unfortunately, that is a difficult question to answer. In general, we want to reduce each of these levels of complexity, but sometimes there are trade-offs. For example, a program that runs quickly may require lots of extra memory, or it could even require really complex code.

The world of business uses a simple triad to understand these trade-offs, as shown in the diagram below:

![Business Triad Diagram](/images/3/3.13.triad_wiki.svg)^[File:Project-triangle.svg. (2020, January 12). Wikimedia Commons, the free media repository. Retrieved 02:41, January 28, 2020 from https://commons.wikimedia.org/w/index.php?title=File:Project-triangle.svg&oldid=386979544.]

Along with this diagram comes the saying: "Fast. Good. Cheap. Pick any two." It helps express the difficulty in finding a perfect program that does not contain at least one level of complexity. 

Thankfully, most modern computers have a sufficiently fast processor and ample memory that most programs can run easily, even without worrying about reducing the space and time complexity of the program. So, it may seem that the most important measure to focus on is code complexity: we should strive to write readable and understandable code.

However, as we build larger programs and deal with more input data, time and space complexity quickly become more important. So, it is important to consider each measure independently, and do the best we can to build programs that run quickly, use a minimal amount of memory, and aren't so complex that they are difficult to understand. 

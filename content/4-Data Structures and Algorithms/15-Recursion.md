---
title: "Recursion"
weight: 75
pre: "15. "
---
![Google Recursion](/images/4/4.16.google.png)

The next algorithmic technique we'll discuss is _recursion_. Recursion is closely related to the divide and conquer method we discussed earlier. However, _recursion_ itself is a very complicated term to understand. It usually presents one of the most difficult challenges for a novice programmer to overcome when learning to write more advanced programs. Don't worry! We'll spend an entire module on recursion later in this course.

## What is Recursion?

There are many different ways to define recursion. In one sense, recursion is a problem solving technique where the solution to a problem depends on solutions to smaller versions of the problem, very similar to the divide and conquer approach.

However, to most programmers, the term _recursion_ is used to describe a function or method that calls itself inside of its own code. It may seem strange at first, but there are many instances in programming where a method can actually call itself again to help solve a difficult problem. However, writing recursive programs can be tricky at first, since there are many ways to make simple errors using recursion that cause our programs to break. 

Mastering recursion takes quite a bit of time and practice, and nearly every programmer has a strong memory of the first time recursion made sense in their minds. So, it is important to make sure we understand it! In fact, it is so notable, that when we search for "recursion" on Google, it helpfully prompts us if we want to search for "recursion" instead, as seen at the top of this page. 

## Example - Factorial

A great example of a recursive method is calculating the _factorial_ of a number. We may recall from mathematics that the factorial of a number is the product of each integer from 1 up to and including that number. For example, the factorial of $5$, written as $5!$, is calculated as $5 * 4 * 3 * 2 * 1  = 120$

We can easily write a traditional method to calculate the factorial of a number as follows.

```tex
function ITERATIVE_FACTORIAL(N)
    RESULT = 1
    loop I from 1 to N:
        RESULT = RESULT * I
    end loop
    return RESULT
end function
```

However, we may also realize that the value of $5!$ is the same as $4! * 5$. If we already know how to find the factorial of $4$, we can just multiply that result by $5$ to find the factorial of $5$. As it turns out, there are many problems in the real world that work just like this, and, in fact, many of the data structures we'll learn about are built in a similar way.

We can rewrite this iterative function to be a recursive function instead.

```tex
function RECURSIVE_FACTORIAL(N)
    if N == 1
        return 1
    else
        return N * RECURSIVE_FACTORIAL(N - 1)
    end if
end function
```

As we can see, a recursive function includes two important elements, the _base case_ and a _recursive case_. We need to include the base case so we can stop calling our recursive function over and over again, and actually reach a solution. This is similar to the termination condition of a **for loop** or **while loop**. If we forget to include the base case, our program will recurse infinitely!

The second part, the recursive case, is used to reduce the problem to a smaller version of the same problem. In this case, we reduce $N!$ to $N * (N - 1)!$. Then, we can just call our function again to solve the problem $(N - 1)!$, and multiply the result by $N$ to find the solution to $N!$. 

So, if we have a problem that can be reduced to a smaller instance of itself, we may be able to use recursion to solve it!


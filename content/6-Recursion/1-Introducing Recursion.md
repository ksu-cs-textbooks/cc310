---
title: "Introducing Recursion"
weight: 5
pre: "1. "
---
{{% youtube GALIjmSovzM %}}

We are now used to using functions in our programs that allow us to decompose complex problems into smaller problems that are easier to solve. Now, we will look at a slight wrinkle in how we use functions. Instead of simply having functions call other functions, we now allow for the fact that a function can actually call itself! When a function calls itself, we call it _recursion_.

Using recursion often allows us to solve complex problems elegantly---with only a few lines of code. Recursion is an alternative to using loops and, theoretically, any function that can be solved with loops can be solved with recursion and vice versa.

## Example: Palindromes

So why would a function want to call itself? When we use recursive functions, we are typically trying to break the problem down into smaller versions of itself. For example, suppose we want to check to see if a word is a palindrome (i.e., it is spelled the same way forwards and backwards). How would we do this recursively? Typically, we would check to see if the first and last characters were the same. If so, we would check the rest of the word between the first and last characters. We would do this over and over until we got down to the 0 or 1 characters in the middle of the word. Let's look at what this might look like in pseudocode.

```tex
function isPalindrome (String S) returns Boolean
    if length of S < 2 then
        return true
    else
        return (first character in S == last character in S) and 
                isPalindrome(substring of S without first and last character)
    end if
end function
```

First, we'll look at the `else` part of the `if` statement. Essentially, this statement determines if the first and last characters of `S` match, and then calls itself recursively to check the rest of the word `S`. Of course, if the first and last characters of `S` match and the rest of the string is a palindrome, the function will return `true`. However, we can't keep calling `isPalindrome` recursively forever. At some point we have to stop. That is what the `if` part of the statement does. We call this our base case. When we get to the point where the length of the string we are checking is `0` or `1` (i.e., `< 2`), we know we have reached the middle of the word. Since all strings of length 0 or 1 are, by definition, palindromes, we return `true`. 

## Key Idea: Break Up the Problem

The key idea of recursion is to break the problem into simpler subproblems until you get to the point where the solution to the problem is trivial and can be solved directly; this is the base case. The algorithm design technique is a form of divide-and-conquer called _decrease-and-conquer_. In decrease-and-conquer, we reduce our problem into smaller versions of the larger problem. 

A recursive program is broken into two parts:

* a **base case**---a simple version of the problem that can be solved directly, and
* a **recursive case**---a general solution to the problem that uses smaller versions of the problem to compute the solution to the larger problem.

The base case is generally the final case we consider in a recursive function and serves to both end the recursive calls and to start the process of returning the final answer to our problem. To avoid endless cycles of recursive calls, it is imperative that we check to ensure that:

1. a base case exists where no further recursive calls are made, and
2. it is possible to reach the base case; the recursive case must ensure that we are moving closer to the base case with each recursive call.

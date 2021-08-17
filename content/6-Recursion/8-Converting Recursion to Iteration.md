---
title: "Converting Recursion to Iteration"
weight: 40
pre: "8. "
---
Iteration and recursion have the same expressive power, which means that any problem that has a recursive solution also has an iterative solution and vice versa. There are also standard techniques that allow you to transform a recursive program into an equivalent iterative version. The simplest case is for tail recursion, where the recursive call is the last step in the function. There are two cases of tail recursion to consider when converting to an iterative version.

1. If the recursive function does not have any parameters or the parameters are passed by reference, the conversion is very simple. We just use a simple while loop.
2. If the recursive function uses parameters passed by value, the conversion is a little more complicated. In general, if the last statement a function `f(x)` executes is a call to itself, `f(y)` with parameter `y`, the recursive call can be replaced by an assignment statement, `x = y`, and by looping back to the beginning of function `f`. 

The approach above only solves the conversion problem in the case of tail recursion. However, as an example, consider our original `FACT` function and its iterative version `FACT2`. Notice that in `FACT2` we had to add a variable `fact` to keep track of the actual computation.

```tex
function FACT(N)
    if N == 1
        return 1
    else
        return N * FACT(N-1)
    end if
end function
```

```tex
function FACT2(N)
   fact = 1 
   while N > 0
       fact = fact * N
       N = N - 1
   end while
   return fact
end function
```

The conversion of non-tail recursive functions typically uses two loops to iterate through the process, effectively replacing recursive calls. The first loop executes statements before the original recursive call, while the second loop executes the statements after the original recursive call. The process also requires that we use a stack to save the parameter and local variable values each time through the loop. Within the first loop, all the statements that precede the recursive call are executed, and then, before the loop terminates, the values of interest are pushed onto the stack. The second loop starts by popping the values saved on the stack and then executing the remaining statements that come after the original recursive call. This is typically much more difficult than the conversion process for tail recursion.

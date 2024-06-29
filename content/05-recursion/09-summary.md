---
title: "Recursion Summary"
weight: 45
pre: "9. "
---
In this module, we explored the use of _recursion_ to write concise solutions for a variety of problems. Recursion allows us to call a function from within itself, using either _head recursion_, _tail recursion_ or _tree recursion_ to solve smaller instances of the original problem.

Recursion requires a _base case_, which tells our function when to stop calling itself and start returning values, and a _recursive case_ to handle reducing the problem's size and calling the function again, sometimes multiple times. 

We can use recursion in many different ways, and any problem that can be solved iteratively can also be solved recursively. The power in recursion comes from its simplicity in code---some problems are much easier to solve recursively than iteratively.

Unfortunately, in general a recursive solution requires more computation time and memory than an iterative solution. We can use techniques such as _memoization_ to greatly improve the time it takes for a recursive function to execute, especially in the case of calculating Fibonacci numbers where subproblems are overlapped. 

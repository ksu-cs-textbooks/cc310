---
title: "Performance of Algorithms"
weight: 35
pre: "7. "
---
The performance of our algorithms is very important, since the difference between good algorithms and bad algorithms on very large data sets can often be measured in terms of days of execution time. Thus, efficiency will be one of the key issues we will look at when designing algorithms.

For example, one simple problem involves finding the largest sum of contiguous elements in an array. So, if we have the array:

```tex
[−2, 1, −3, 4, −1, 2, 1, −5, 4]
```

we could find that the contiguous sequence of:

```tex
[4, −1, 2, 1]
```

sums to $6$, which is the largest sum of any contiguous subsequences of this array. 

A simple solution to this problem might involve finding all possible subsequences of the array and adding them, which could take a very long time. In fact, if the array contains $n$ elements, it might take $n^3$ steps to solve it. However, with a little ingenuity, we can actually solve this problem using many fewer steps, even as few as $n$ steps itself.  

When we try to solve a problem, it is often helpful to look at multiple solutions to the problem and compare them before choosing our final design.  Just the act of trying to find multiple ways to solve the same problem stimulates creativity and promotes mental elasticity and speed of thought. Selecting a solution from several different choices following rigorous and objective criteria enables us to improve fundamental life skills such as simply knowing how to make decisions! In fact, the very attempt at solving a problem in a variety of ways forces us to look our problems from different perspectives, which is the catalyst of all scientific discoveries.

Throughout this section, we will develop two solutions to the problem of finding the maximum `max` and minimum `min` of a list of `N` numbers (defined as `list[N]`) as an example. We will develop both solutions and then evaluate their performances in terms of both execution time and memory space. 

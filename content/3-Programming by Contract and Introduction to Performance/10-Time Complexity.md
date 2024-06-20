---
title: "Time Complexity"
weight: 50
pre: "10. "
---
{{< youtube J_o9ud01yHU  >}}

It is very useful to compare the two solutions to choose one. In general, you can compare the two solutions by considering:

1. The time required to execute it
2. The amount of memory it requires
3. The number of instructions used, and also the understandability of the code

## Time Complexity

To compare programs in terms of the time we can estimate the running time, or time it takes to complete its work. If the program performs operations on a large set of data, you can also check the run time by using the timer available in your programming language. This type of algorithm profiling is called experimental algorithm evaluation.

You can also estimate the time by counting the number of comparisons and assignments performed by the two programs since comparison and assignments are the fundamental operations that allow you to find the smallest and the largest element.

Let's do this analysis for both the linear and pairs solution to the problem of finding the minimum and maximum values in a list of numbers. For this analysis, we'll just look at the code inside the loop, and ignore any code before the loop that initializes variables, since both programs have the same code there. 

### Comparisons

The linear program performs two comparisons, `x > max` and `x < min` each time a new number is considered. If the algorithm considers `N` numbers, the total number of comparisons is $N * 2$ or $2N$ comparisons. 

The pairs program makes three comparisons every time it considers two elements: `x > y`, `lastmax > max` and `lastmin < min` If the algorithm considers `N` numbers, the total number of comparison is $N/2 * 3$ or $3/2 N$ comparisons. 

If we assume that our list is holding a large number of values, then we can see a major difference in the time required to complete the program. Put another way, we can observe that the difference in efficiency between the two programs increases as `N` increases. Assuming `N` is $1,000$, the linear program makes $2,000$ comparisons, while the pairs program makes $1,500$ comparisons. 

Of course, data sizes in real programs can be much larger. For example, Google currently indexes around 50 billion web pages! So, a list that contains $1,000$ numbers looks pretty small by comparison.

### Assignments

For the assignments, you can count them. For the linear solution, the following situations could occur:

1. The new number updates the maximum. If the new number is the maximum it will be greater than the minimum, so no update is required for the minimum
2. The new number update the minimum. If the new number is the minimum it will be lower than the maximum so no updated are required for the maximum
3. If the new number is between the minimum and the maximum value no updates are required

So, in the _worst-case_, the algorithm performs $N$ assignments. For example, consider a situation where the list is already sorted in increasing order. In that case, we'll have to update the maximum value each time, resulting in $N$ assignments. 

In the pairs solution, for every two numbers considered causes the following assignments to be computed:
1. Two assignments for updating the `lastmax` and `lastmin`. These two assignments are done in any case.
2. From zero to two assignments to update the `min` and the `max`, depending on the results of the comparisons.

Therefore, the number of assignments is $2$ in the _best case_, $4$ in the _worst case_, and $3$ in the _average case_. Hence, with $N$ numbers, the number of assignments is $N/2 * 2$ or $N$ in the best case, $2N$ in the worst case and $3/2N$ in the average case. The number of assignments is greater with the second algorithm. But, could we do better in this last case?

## Which is Better?

So, how can we determine which is better? Let's look at a couple of situations.

For example, if we have a list of 1000 numbers, we can find the following number of steps for each program. First, let's consider the **worst case** performance, taking the largest values for each. 

1. Linear: $2N$ or $2000$ comparisons + $N$ or $1000$ assignments, so $3000$ total steps
1. Pairs: $3/2 * N$ or $1500$ comparisons + $2N$ or $2000$ assignments, to $3500$ total steps

As we can see, the pairs program requires more steps in total than the linear program. So, it appears that it might be the best choice.

However, not every program will be a worst case. So, let's look at the **best case** performance for each one:

1. Linear: $2N$ or $2000$ comparisons + $0$ assignments (ignoring the small number of initial assignments), so $2000$ total steps
1. Pairs: $3/2 * N$ or $1500$ comparisons + $N$ or $1000$ assignments, to $2500$ total steps

Again, we see that the pairs program still requires more steps than the linear program, though both programs run faster in the best case than the worst case.

Finally, we can do the same for the **average case** performance:

1. Linear: $2N$ or $2000$ comparisons + $N/2$ assignments, so $2500$ total steps
1. Pairs: $3/2 * N$ or $1500$ comparisons + $3/2 * N$ or $1500$ assignments, to $3000$ total steps

There we go! As we can see, in each case the linear program actually performs better than the pairs program, even though we know that the pairs program will only run the loop half as many times as the linear program. The extra comparisons and assignments make the program take more time!

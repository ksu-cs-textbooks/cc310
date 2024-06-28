---
title: "Example: Factorials"
weight: 20
pre: "4. "
disableMathJax: false
---
The most popular example of using recursion is calculating the factorial of a positive integer $N$. The factorial of a positive integer $N$ is just the product of all the integers from $1$ to $N$. For example, the factorial of $5$, written as $5!$, is calculated as $5 * 4 * 3 * 2 * 1 = 120$. The definition of the factorial function itself is recursive.
$$
\text{fact}(N) = N  *  \text{fact}(N - 1)
$$
The corresponding pseudocode is shown below.

```tex
function FACT(N)
    if N == 1
        return 1
    else
        return N * FACT(N-1)
    end if
end function
```

The recursive version of the factorial is slower than the iterative version, especially for high values of $N$. However, the recursive version is simpler to program and more elegant, which typically results in programs that are easier to maintain over their lifetimes.

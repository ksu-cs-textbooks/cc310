---
title: "Loops"
weight: 40
pre: "8. "
disableMathJax: false
---

{{< youtube yLPFAGYV1Kw  >}}

Loops are another way we can control the flow of our program, this time by repeating steps based on a given criteria.  A computer is able to repeat the same instructions many times. There are several ways to tell a computer to repeat a sequence of instructions:

* Repeat an infinite number of times, e.g. `while true`. This construct is useful in software applications such as servers that will offer a service. The service is supposed to be available forever. 
* Repeat a specific number of times, e.g. `Repeat 10 times` or `for i = 1 to 10`. This loop can be used when you know the number of repetitions. There are also loops that allow you to repeat as many times as there are elements of a collection, such as `for each item in list` 
* Repeat according to a condition. The number of repetitions depends on the condition. Most programming languages support the `while` loop, which repeats while the condition is true. 

In repeat while loops, the number of repetitions depends on the occurrence of a condition: the cycle repeats if the condition is true. Loops can also be nested, just like conditional statements. 

## Loops in Flowcharts & Pseudocode

The table below lists the flowchart blocks used to represent loop statements, as well as the corresponding pseudocode:

| Operation | Flowchart | Pseudocode |
|:---------:|:---------:|:-----------|
| While Loop | ![While Loop Flowchart Block](/images/1/1.3.x.6.loop1.png) | <pre><code>loop while A &lt; 5<br>    A = A + 1<br>end loop</code></pre> |
| For Loop | ![For Loop Flowchart Block](/images/1/1.3.x.6.loop2.png) | <pre><code>loop I from 1 to 10<br>    A = A + I<br>end loop</code></pre> |
| For Loop with Step | ![For Loop with Step Flowchart Block](/images/1/1.3.x.6.loop3.png) | <pre><code>loop I from 1 to 10 step by 2<br>    A = A + I<br>end loop</code></pre> |
| For Each Loop | ![For Each Loop Flowchart Block](/images/1/1.3.x.6.loop4.png) | <pre><code>loop each I in LIST<br>    A = A + I<br>end loop</code></pre> |

## Loops in Python

To see how loops look in Python, let's recreate them from the flowcharts shown above.

![While Loop Flowchart Block](/images/1/1.3.x.6.loop1.png)

```python
while a < 5:
    a = a + 1
```

![For Loop Flowchart Block](/images/1/1.3.x.6.loop2.png)

```python
for i in range(1, 11):
    a = a + i
```

![For Loop with Step Flowchart Block](/images/1/1.3.x.6.loop3.png)

```python
for i in range(1, 11, 2):
    a = a + i
```

![For Each Loop Flowchart Block](/images/1/1.3.x.6.loop4.png)

```python
for i in list:
    a = a + i
```

As we can see in the examples above, we must carefully indent each block of code to help set it apart from the other parts of the program. In addition, each line containing `for` and `while` must end in a colon `:`. Finally, notice that the `range()` function in Python does not include the second parameter in the output. So, to get the numbers $1$ through $10$, inclusive, we must use `range(1, 11)` in our code. 

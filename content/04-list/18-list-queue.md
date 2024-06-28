---
title: "List-Based Queues"
weight: 90
pre: "18. "
disableMathJax: false
---
{{< youtube abQW7BnD4_c  >}}

Implementing a queue with a doubly linked list is straightforward and efficient. The core queue operations (`enqueue`, `dequeue`, `isEmpty`, and `peek`) can all be implemented by directly calling list operations that run in constant time. The only other major operation is the `toString` operation, which is also implemented by directly calling the list `toString` operation; however, it runs in order $N$ time due to the fact that the list `toString` operation must iterate through each item in the list.

The key queue operations and their list-based implementations are shown below.

| Operation | Implementation |
|:---------:|:---------------|
| `enqueue` | <pre><code>function enqueue (data)<br>    list.append(data)<br>end function</code></pre>
| `dequeue` | <pre><code>function dequeue() returns data<br>    return removeFirst()<br>end function</code></pre>
| `isEmpty` | <pre><code>function isEmpty() returns Boolean<br>    return list.isEmpty()<br>end function</code></pre>
| `peek` | <pre><code>function peek() returns data<br>    return list.peek()<br>end function</code></pre>
| `toString` | <pre><code>function toString() returns data<br>    return list.toString()<br>end function</code></pre>

Stacks can be implemented using a similar method - namely adding and removing from the end of the list. This can even be done using a singly-linked list, and is very efficient. 
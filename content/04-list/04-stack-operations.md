---
title: "Stack Operations"
weight: 20
pre: "4. "
disableMathJax: false
---

The following table shows an example of how to use the above operations to create and manipulate a stack. It assumes the steps are performed sequentially and the result of the operation is shown. 

| Step | Operation | Effect |
|:----:|:---------:|:---------:|
| 1 | Constructor | Creates an empty stack.  ![Empty Stack](/images/5/5.5.stack0.png) |
| 2 | `isFull()` | Returns `false` since `top` is not equal to the capacity of the stack. ![Empty Stack](/images/5/5.5.stack0.png) |
| 3 | `isEmpty()` | Returns `true` since `top` is equal to -1 ![Empty Stack](/images/5/5.5.stack0.png) |
| 4 | `push(1)` | Increments `top` by 1 and then places item $1$ onto the top of the stack ![Stack 1](/images/5/5.5.stack1.png) |
| 5 | `push(2)` | Increments `top` by 1 and then places item $2$ onto the top of the stack ![Stack 2](/images/5/5.5.stack2.png) |
| 6 | `push(3)` | Increments `top` by 1 and then places item $3$ onto the top of the stack ![Stack 3](/images/5/5.5.stack3.png) |
| 7 | `peek()` | Returns the item $3$ on the top of the stack but does not remove the item from the stack. `top` is unaffected by peek ![Stack 3](/images/5/5.5.stack3.png) |
| 8 | `pop()` | Returns the item $3$ from the top of the stack and removes the item from the stack. `top` is decremented by 1. ![Stack 2](/images/5/5.5.stack2.png) |
| 9 | `pop()` | Returns the item $2$ from the top of the stack and removes the item from the stack. `top` is decremented by 1. ![Stack 1](/images/5/5.5.stack1.png) |
| 10 | `pop()` | Returns the item $1$ from the top of the stack and removes the item from the stack. `top` is decremented by 1. ![Stack 0](/images/5/5.5.stack0.png) |
| 11 | `isEmpty()` | Returns `true` since `top` is equal to -1 ![Empty Stack](/images/5/5.5.stack0.png) |

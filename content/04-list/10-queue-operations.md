---
title: "Using Operations"
weight: 50
pre: "10. "
---
The following table shows an example of how to use the above operations to create and manipulate a queue. It assumes the steps are performed sequentially and the result of the operation is shown. 

| Step | Operation | Effect |
|:----:|:---------:|:---------:|
| 1 | Constructor | Creates an empty queue of capacity 3.  ![Empty Queue](/images/8/8.5.queue0.png) |
| 2 | `isFull()` | Returns `false` since `start` is not equal to `end`  ![Empty Queue](/images/8/8.5.queue0.png) |
| 3 | `isEmpty()` | Returns `true` since `start` is equal to `-1`.   ![Empty Queue](/images/8/8.5.queue0.png) |
| 4 | `enqueue(1)` | Places item `1` onto queue at the end and increments `end` by 1.  ![Queue with 1 Element](/images/8/8.5.queue1.png) |
| 5 | `enqueue(2)` | Places item `2` onto queue at the end and increments `end` by 1.  ![Queue with 2 Elements](/images/8/8.5.queue2.png) |
| 6 | `enqueue(3)` | Places item `3` onto queue at the end and sets `end` to `end+1` modulo the size of the array (3). The result of the operation is `0`, thus `end` is set to `0`.  ![Queue with 3 Elements](/images/8/8.5.queue3a.png) |
| 7 | `peek()` | Returns the item `1` on the `start` of the queue but does not remove the item from the queue. `start` and `end` are  unaffected by peek.  ![Queue with 3 Elements](/images/8/8.5.queue3a.png) |
| 8 | `isFull()` | Returns `true` since `start` is equal to `end`  ![Queue with 3 Elements](/images/8/8.5.queue3a.png) |
| 9 | `dequeue()` | Returns the item `1` from the start of the queue. `start` is incremented by 1, effectively removing `1` from the queue.  ![Queue with 2 Elements](/images/8/8.5.queue3.png) |
| 10 | `dequeue()` | Returns the item `2` from the start of the queue. `start` is incremented by 1, effectively removing `2` from the queue.  ![Queue with 1 Element](/images/8/8.5.queue4.png) |
| 11 | `enqueue(4)` | Places item `4` onto queue at the end and increments `end`.   ![Queue with 2 Elements](/images/8/8.5.queue5.png) |
| 12 | `dequeue()` | Returns the item `3` from the start of the queue. `start` is set to `start+1` modulo the size of the array (3). The result of the operation is `0`, thus `start` is set to `0`.   ![Queue with 1 Elements](/images/8/8.5.queue7.png) |
| 13 | `dequeue()` | Returns the item `4` from the start of the queue. `start` is incremented by 1, and since `start == end`, they are both reset to `-1` and `0` respectively.   ![Queue with 0 Elements](/images/8/8.5.queue0.png) |
| 14 | `isEmpty()` | Returns `true` since `start` is equal to -1.   ![Queue with 0 Elements](/images/8/8.5.queue0.png) |

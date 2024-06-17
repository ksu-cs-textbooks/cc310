---
title: "Windshield Station Example"
weight: 35
pre: "7. "
---
The following example shows how the `Controller` class would work, given specific calls to `receiveCar` and `getCar`.

| Step | Operation | Effect |
|:----:|:---------:|:---------:|
| 1 | Constructor | Creates 3 priority queues.  ![Empty Queue](/images/8/8.8.controller1.png) |
| 2 | `getCar()` | Raises an exception since all three queues will be empty.  ![Empty Queue](/images/8/8.8.controller1.png) |
| 3 | `receiveCar(a, low)` | Places car `a` into the `low` queue.  ![Queue with 1 car](/images/8/8.8.controller1.1.png) |
| 4 | `receiveCar(b, low)` | Places car `b` into the `low` queue.  ![Queue with 2 cars](/images/8/8.8.controller2.png) |
| 5 | `receiveCar(f, high)` | Places car `f` into the `high` queue.  ![Queue with 3 cars](/images/8/8.8.controller3.png) |
| 6 | `receiveCar(d, medium)` | Places car `d` into the `medium` queue.  ![Queue with 4 cars](/images/8/8.8.controller4.png) |
| 7 | `receiveCar(g, high)` | Raises an exception since the `high` queue is already full.  ![Queue with 4 cars](/images/8/8.8.controller4.png) |
| 8 | `receiveCar(e, medium)` | Places car `e` into the `medium` queue.  ![Queue with 5 cars](/images/8/8.8.controller4.1.png) |
| 9 | `getCar()` | Returns car `f` from the `high` queue.  ![Queue with 4 cars](/images/8/8.8.controller5.png) |
| 10 | `getCar()` | Returns car `d` from the `medium` queue.  ![Queue with 3 cars](/images/8/8.8.controller6.png) |
| 11 | `getCar()` | Returns car `e` from the `medium` queue.  ![Queue with 2 cars](/images/8/8.8.controller9.png) |
| 12 | `getCar()` | Returns car `a` from the `low` queue.  ![Queue with 1 car](/images/8/8.8.controller10.png) |
| 13 | `getCar()` | Returns car `b` from the `low` queue.  ![Queue with 0 cars](/images/8/8.8.controller1.png) |
| 14 | `getCar()` | Raises an exception since there are no more cars available in any of the three queues.  ![Queue with 0 cars](/images/8/8.8.controller1.png) |
| 15 | `isEmpty()` | Returns `true` since all three queues are empty.  ![Queue with 0 cars](/images/8/8.8.controller1.png) |

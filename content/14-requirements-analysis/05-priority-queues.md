---
title: "Priority Queues"
weight: 25
pre: "5. "
---

The last structure we covered were priority queues. On their own, these are good for hierarchical data. We discussed using priority queues for ticketing systems where the priority is the cost or urgency. In the project, we utilized priority queues in conjunction with Dijkstra's algorithm.

### Priority Queues

A priority queue is a data structure which contains elements and each element has an associated priority value. The priority for an element corresponds to its importance. For this course, we implemented priority queues using heaps. 

A key point of priority queues is that the priority for a value can change. This is reflected by nodes moving up (via push up) or down (via push down) through the priority queue. 

In contrast, a tree has a generally fixed order. Consider the file tree as a conceptual example, it is not practical for a parent folder to switch places with a child folder. 


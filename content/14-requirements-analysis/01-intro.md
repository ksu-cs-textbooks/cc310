---
title: "Intro"
weight: 5
pre: "1. "
---

{{< youtube ZSC3F4OdGg0  >}}

In this module, we will discuss how we can determine which data structure we should choose when storing real-world data. We'll typically make this decision based on the characteristics of the data we would like to store. In general, the data structures we've learned often work together well and complement each other, as we saw in Dijkstra's algorithm. In some cases, one structure can be utilized to implement another, such as using a linked list to implement a stack or a queue. 

When selecting a data structure for a particular data set, there are a few considerations we should keep in mind. 

### Does it Work?

The first consideration is: does this data structure work for our data? To answer this, we would want to the characteristics in the data and then determine if our chosen data structure:
- maintains relationships between elements?
- translates well to the real world data?
- efficiently stores the data without extra overhead?
- can store all aspects of the data clearly and concisely?

### Will Someone Else Understand?

Once we have chosen a possible data structure, we also must consider if the choice clearly makes sense to another person who reviews our work. Some questions we may want to ask: 
- is this a natural choice?
- if I look back at this 6 months from now, would I understand it?
- do I need to provide extra comments or documentation to explain this choice?

### Does it Perform Well?

Finally, we should always consider the performance of our program when selecting a data structure. In some cases, the most straightforward data structure may not always be the most efficient, so at times there is a trade off between performance and simplicity. Consider the hash table structure - it may seem like a more complicated array or linked list. But, if we need to find a specific item in the structure, a hash table is typically **much** faster due to the use of hashes. That increase in complexity pays off in faster performance. So, when analyzing data structures for performance, we typically look at these things:
- performance time for tasks
- space requirements
- complexity of the code

We will address this particular facet in the next chapter. For now, we will focus on the first two portions. 

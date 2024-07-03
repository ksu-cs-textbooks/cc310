---
title: "Weighted Graphs"
weight: 20
pre: "4. "
---

{{< youtube x4_myCOtFnk  >}}

A **weighted** graph is a graph which has weights associated with the edges. These weights quantify the relationships, so they can represent dollars, minutes, miles, and many other factors which our data may depend upon. 

Weights are not limited to physical quantities; they can also be our own defined similarity in text, product types, and anything for which we can create a similarity measure for. Let's look at concrete weights using the Amtrak example.

We are able to expand the Amtrak graph from the previous page to include approximate distances in miles between cities. 

![Amtrak Train Graph with Weights](images/15/amtrak_dist.svg)[^1]

[^1]: Generated using the Amtrak system map from 2018. This graph does not include all stations or connections. Distance was calculated approximately 'as the crow flies'.

Now that we have weights defined on our edges, we can compare paths in a different way. When we discussed trees, we just looked at the number of edges it took to get to another node. We can also determine the shortest path between nodes with respect to distance. If we wanted to travel from San Antonio to Kansas City, we may be tempted to travel `San Antonio -> Los Angeles -> Albuquerque -> Kansas City` as it has the fewest stops. This trip would take us 2,531 miles (1201+640+690). With the edge weights in mind, a much better route would be `San Antonio -> Fort Worth -> Little Rock -> St. Louis -> Kansas City` with a total of 1,089 miles(238+320+293+238) traveled.

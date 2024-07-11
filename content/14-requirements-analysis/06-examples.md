---
title: "Examples"
weight: 30
pre: "6. "
---

{{< youtube eCa3TreKdqU  >}}

In real world applications, it won't always be a straightforward choice to use one structure over another. Users may come to us with unclear ideas of what they are looking for and we will need to be able to infer what structure is best suited for their needs based on what we can learn from them. Typically, those describing applications to us may not be familiar with the nomenclature we use as programmers. Instead, we have to look for clues about how the data is structured and used to help us choose the most appropriate data structures

Below we have some examples with possible solutions. We say possible solutions because there may be other ways that we could implement things. It is important that no matter what structure or algorithm we use, we should always document why we chose our answer. If someone else were to join on the project at a later time, it is important that they understand our reasoning. 

### Costume Shop 

A manager at a costume shop has requested that we do some data management for their online catalog. They say:
- Users should be able to refine their search first based on who the costumes are for (adults, children, dogs), then on the part of the costume (tops, bottoms, shoes, props) and then display those options for the user.
- I would like if we could recommend costumes to customers based on their searches. 

Take a moment to think on how you might go about this. Remember, there can be multiple ways of solving these problems. We need to be sure that we can articulate and justify our answers. 

This is a situation where we could potentially use all three data structures! 

First, we could use a tree to represent the search refinement. Thinking along the lines of a data structure, each category and subsequently each product will have exactly one parent. While something like 'wigs' shows up in all three categories, you wouldn't want dog wigs showing up in a search for adult wigs. Thus, there is a unique ancestry for each category and product. 

![Tree for Search](images/18/11_costume_trie.svg)

In this scenario we had a fixed ordering of our hierarchy. If the manager wanted users to be able to sort by costume part and then who it was for, our tree would not hold up. 

The second portion that was requested was a recommendation system. We could implement this in two parts. The first would be a graph in which the nodes are the products and they are connected based on the similarity of the products. 

For example, a purple children's wig will be very similar to a children's blue wig but it would be very different from an adults clown shoes. Thus, our graph would have a heavily weighted connection between the children's purple and blue wig and there would be an edge with a very small weight between the purple wig and adult clown shoes. We can obtain this information from the manager. Since each product will be connected to every other product, a matrix graph would be best suited here. 

Then once we have the graph, we could implement a priority queue. The priority queue would be built based off of the users search. When a user searches for a product, we would refer to our graph and get other similar products and enqueue them. The priority would be similarity to the searched products and the item would be the recommended product. As they continue to search, we would dequeue an element if the user selects it and we would change the priority of elements based on commonalities in the searches. 

### Video Game 

A friend approaches you about their idea for a video game and ask how they could use different data structures to produce the game. They tell us about their game which is a sandbox game with no defined goals. Users can do tasks at their own chosen speed and there is no real "completion" of the game. They say:
- I want users to be able to see the tasks that are available to them and what the payout of the task is. It would be really awesome if we could display around 4 tasks that would earn them the most points. 
- I have a set of "shortcuts" that users can use to streamline basic functions like switching tools. It would make sense that all of the shortcuts for switching tools start with the same button clicks. So switching to a shovel would be similar to switching to a hammer. 
- I have this world in mind that is a lot like our world in terms of terrain and what not. I want players to be able to dig in the dirt and then move that dirt as they like! They could build dirt piles or houses from the trees. 

Take a moment to think on how you might go about this. Remember, there can be multiple ways of solving these problems. We need to be sure that we can articulate and justify our answers. 

Again, this is a situation where we could potentially use three data structures! 

We can use a priority queue to suggest tasks for the players to do. In this priority queue, the priority would be the payout and the item would be the task itself. As tasks get completed, we would dequeue them. 

We can use a trie to represent the set of shortcuts. Below is a small sample of how we can implement our trie. 

![Trie for Shortcuts](images/18/11_videogame_trie.svg)

Since our friend mentioned that similar tasks should have similar combinations, a trie will fit well. These key combinations will have similar prefixes, so we can save ourselves space to store them by using a trie. 

Finally, for the world layout we could use a graph. Similar to the maze project or weather station project, we can have nodes represent points on a plot and the edges will represent connections. The nodes will now have three coordinates, (x,y,z), rather than two, (x,y) or (latitude, longitude) and they will have an associated type (dirt, tree, rock, etc.). 

![Graph for world blocks](images/18/11_videogame_graph.svg)

Two nodes will be connected if they directly adjacent. Players can harvest cubes such as soil or limestone, and it would be removed from the world. We would utilize our remove node function to reflect this kind of action. Similarly, players can build up the world in spaces that allow, such as the dirt pile in an open area, and for that we can use our add node function as well as the appropriate add edge functions.  

In our implementation of a graph, it would be better to use a list graph. Each block will be connected to at most six other blocks. 

![Cubes neighbors](images/18/11_videogame_cubes.svg)







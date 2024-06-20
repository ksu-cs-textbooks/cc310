---
title: "Using a Queue"
weight: 30
pre: "6. "
---
{{< youtube 05zPOJ8B5cA  >}}

Queues are useful in many applications. Classic real-world software which uses queues includes the scheduling of tasks, sharing of resources, and processing of messages in the proper order. A common need is to schedule tasks to be executed based on their priority. This type of scheduling can be done in a computer or on an assembly line floor, but the basic concept is the same. 

Let's assume that we are putting windshields onto new cars in a production line. In addition, there are some cars that we want to rush through production faster than others. There are actually three different priorities:

1. High priority: these cars have been ordered by customers who are waiting for them.
1. Medium priority: these cars have been ordered as "fleet cars" for specific companies.
1. Low priority: these cars are cars used to fill dealer inventories.

Ideally, as cars come to the windshield station, we would be able to put their windshields in and send them to the next station before we received the next car. However, this is rarely the case. Since putting on windshields often requires special attention, cars tend to line up to get their windows installed. This is when their priority comes into account. Instead of using a simple queue to line cars up first-come, first-served in FIFO order, we would like to jump high priority cars to the head of the line. 

While we could build a sophisticated queueing mechanism that would automatically insert cars in the appropriate order based on priority and then arrival time, we could also use a queue to handle each set of car priorities. A figure illustrating this situation is shown below. As cars come in, they are put in one of three queues: high priority, medium priority, or low priority. When the windshield station completes a car it then takes the next car from the highest priority queue.

![Car Windshield Installation Model](/images/8/8.7.model.png)

The interesting part of the problem is the controller at the windshield station that determines which car will be selected to be worked on next. The controller will need to have the following interface:

```tex
function receiveCar(car, priority)
 // receives a car from the previous station and places into a specific queue

function bool isEmpty()
 // returns true if there are no more cars in the queue

function getCar() returns car
 // retrieves the next car based on priority
```

Using this simple interface, we will define a class to act as the windshield station controller. It will receive cars from the previous station and get cars for the windshield station.

We start by defining the internal attributes and constructor for the `Controller` class as follows, using the Queue functions defined earlier in this module. We first declare three separate queues, one each for `high`, `medium`, and `low` priority cars. Next, we create the constructor for the `Controller` class. The constructor simply initializes our three queues with varying capacities based on the expected usage of each of the queues. Notice, that the `high` priority queue has the smallest capacity while the `low` priority queue has the largest capacity.

```tex
class Controller
    declare HIGH as a Queue
    declare MEDIUM as a Queue
    declare LOW as a Queue

    function Controller()
        HIGH = new Queue(4)
        MEDIUM = new Queue(6)
        LOW = new Queue(8)
    end function
```

Next, we need to define the interface function as defined above. We start with the `receiveCar` function. There are three cases based on the `priority` of the `car`. If we look at the first case for `priority == high`, we check to see if the `high` queue is full before calling the `enqueue` function to place the `car` into the `high` queue. If the queue is full, we raise an exception. We follow the exact same logic for the `medium` and `low` priority cars as well. Finally, there is a final `else` that captures the case where the user did not specific either `high`, `medium`, or `low` priority. In this case, an exception is raised.

```tex
function receiveCar(CAR, PRIORITY)
    if PRIORITY == high
        if HIGH.isFull()
            raise exception
        else
            HIGH.enqueue(CAR)
        end if
    else PRIORITY == medium
        if MEDIUM.isFull()
            raise exception
        else
            MEDIUM.enqueue(CAR)
        end if
    else PRIORITY == low
        if LOW.isFull()
            raise exception
        else
            LOW.enqueue(CAR)
        end if
    else
        raise exception
    end if
end function
```

Now we will define the `isEmpty` function. While we do not include an `isFull` function due to the ambiguity of what that would mean and how it might be useful, the `isEmpty` function will be useful for the windshield station to check before they request another call via the `getCar` function. 

As you can see below, the `isEmpty` function simply returns the logical AND of each of the individual queue's `isEmpty` status. Thus, the function will return true if, and only if, each of the `high`, `medium`, and `low` queues are empty.

```tex
function isEmpty()
    return HIGH.isEmpty() and MEDIUM.isEmpty() and LOW.isEmpty()
end function
```

Finally, we are able to define the `getCar` function. It is similar in structure to the `receiveCar` function in that it checks each queue individually. In the case of `getCar`, the key to the priority mechanism we are developing is in the order we check the queues. In this case, we check them in the expected order from high to low. If the `high` queue is not empty, we get the car from that queue and return it to the calling function. If the `high` queue is empty, then we check the `medium` queue. Likewise, if the `medium` queue is empty, we check the low `queue`. Finally, if all of the queues are empty, we raise an exception.

```tex
function getCar()
    if not HIGH.isEmpty()
        return HIGH.dequeue()
    else not MEDIUM.isEmpty()
        return MEDIUM.dequeue()
    else not LOW.isEmpty()
        return LOW.dequeue()
    else
        raise exception
    end if
end function
```


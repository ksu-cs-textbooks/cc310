---
title: "Basic Operations"
weight: 20
pre: "4. "
disableMathJax: false
---

{{< youtube _VILq37deuY  >}}

We have already seen two basic stack operations: `push` and `pop`. However, there are others that make the stack much easier to use. These basic operations are:

* `push`: places an item on top of the stack,
* `pop`: removes the item on the top of the stack and returns it,
* `peek`: returns the item on the top of the stack without removing it from the stack,
* `isEmpty`: returns true if there are no items on the stack, and
* `isFull`: returns true if our stack array is full.

We will discuss each of these operations. But first, let's talk about the constructor for the `stack` class and what it must do to properly set up a `stack` object.

## Constructor

The main responsibility of the constructor is to initialize our attributes in the `stack` class. As we discussed above, the attributes include the `myStack` array and the `top` attribute that keeps track of the top of the stack. 

Since we are using an array for our stack, we will need to know how big to make the array in our constructor. There are two options. We could just use a default size for the array. Or, we could allow the user to pass in a positive integer to set the size. In this module we assume the caller must provide a `capacity` value, which must be greater than `0`.

```tex
function STACKCONSTRUCTOR(CAPACITY)
    if CAPACITY not an integer then
        throw exception
    else if CAPACITY <= 0 then
        throw exception
    end if
    MYSTACK = new array[CAPACITY]
    TOP = -1
end function
```

The first thing we do in the code is to check to make sure that `capacity` is actually an integer that is greater than `0`. Essentially, this is our precondition for the method. If our precondition is not met, we throw an exception. (If we are using a  typed language such as Java, we can enforce our precondition by requiring that `capacity` be of type `integer` instead of explicitly checking it in the code.) Once we've validated our precondition, we create a new array of size `capacity` for the `myStack` array and set the attribute `top` to `-1`.

## Push
We have already discussed the `push` operation and seen it in operation earlier in this module. In the pseudocode below, we see that we must first check to ensure that the stack is not already full. Again, this is our precondition. You may be picking up on the fact that the first thing we do in our methods is to check our precondition and throw an exception if it is not met. This is good coding practice. 

```tex
function PUSH(ITEM)
    if MYSTACK is full then
        throw exception
    end if
    TOP = TOP + 1
    MYSTACK[TOP] = ITEM
end function
```

Once our precondition is validated, we simply increment `top` by `1` and store the `item` into the array at index `top`. We do not return anything from the `push` function. Also, notice that there are no loops in the `push` operation and thus the time it takes to execute the operation will always be the same regardless of the size of the `myStack` array. We call this constant time performance, which is typically very fast.

## Pop

Like `push`, we have already seen the `pop` operation. It simply takes the top item off of the stack and returns it. However, once again we need to validate our precondition before getting into the body of the operation. For the `pop` operation, our precondition is that the stack must not already be empty, which is detected when `top` equals `-1`.

```tex
function POP
    if TOP == -1 then
        throw exception
    end if
    TOP = TOP - 1
    return MYSTACK[TOP + 1]
end function
```

Once we have validated our precondition, we simply decrement `top` by `1` and then return the previous item at the top of the stack (`myStack[top + 1]`). Like the `push` operation, the `pop` operation takes a constant time to execute.

## IsFull

To allow the calling program to detect when the stack is full, we define an `isFull` operation. Notice that code external to the `stack` class cannot access the value of `top` and so it cannot simply check if `top + 1 == length of myStack` on its own. In this case, the operation is very simple as we only need to return the Boolean value of `top + 1 == length of myStack` as shown below. There is no precondition for `isFull` and `isFull` operates in constant time.

```tex
function ISFULL()
	return TOP + 1 == length of MYSTACK
end function
```

## IsEmpty

The `isEmpty` operation is very similar to the `isFull` operation except that we return the Boolean value of the condition  `top == -1` instead of `top + 1 == length of myStack`.

## Peek

The `peek` operation returns the top item on the stack, without removing it from the stack. Like the `pop` operation it has the precondition that the stack must not be empty. The pseudocode for the `peek` operation is shown below. It is also a constant time operation.

```tex
function PEEK()
	if ISEMTPY() then
		throw exception
	end if
    return MYSTACK[TOP]
end function
```

Notice that we replaced the precondition check of `top == -1` with a call to `isEmpty`, which produces the same result. The real benefit here is the readability of the code and the fact that we only have to code the `top == -1` check in the `isEmpty` operation. This will make it easier to maintain the code in the future if we change the way we implement the stack.

## DoubleCapacity

The `doubleCapacity` operation doubles the size of the array holding our stack. So, if we started with an array of size `4`, the `doubleCapacity` operation will result in an array of size `8` with the contents of our original array stored in it. Unfortunately, most programming languages (like Java) do not simply let you double the size of the array. A noted exception to this is Python, which does allow you to directly extend an array. 

In a traditional programming language, the easiest way to accomplish the `doubleCapacity` operation is to complete the following steps:

1. Create a new array with twice the capacity of the existing array, 
2. Copy the contents of original array into the new array, then
3. Point the `myStack` array at the new array. 

The pseudocode for the `doubleCapacity` operation is shown below. 

```tex
function DOUBLECAPACITY()
    NEWSTACK = new array[length of MYSTACK * 2]
    loop I from 0 to TOP
        NEWSTACK[i] = MYSTACK[i]
    end for
    MYSTACK = NEWSTACK
end function
```

The `doubleCapacity` operation is not a constant time operation.  This is due to the fact that copying the contents of the original array into the new array requires us to copy each item in the stack into the new array individually. This requires N steps. Thus, we would say that `doubleCapacity` runs in the order of $N$ time.

## HalveCapacity

The `halveCapacity` operation is like the `doubleCapacity` operation except that we now have a precondition. We must make sure that when we cut the space for storing the stack that we still have enough space to store all the items currently in the stack. For example, if we have 10 items in a stack with a capacity of 16, we can't successfully perform `halveCapacity`. Doing so would only leave us a stack with a capacity of 8 and we would not be able to fit all 10 items in the new stack.

```tex
function HALVECAPACITY()
	if TOP + 1 > length of MYSTACK / 2 then
		throw exception
	end if
    NEWSTACK = new array[length of MYSTACK / 2]
    loop I from 0 to TOP
        NEWSTACK[i] = MYSTACK[i]
    end for
    MYSTACK = NEWSTACK
end function
```

## ToString

The `toString` operation returns a string that concatenates the strings representing all the items stored in an array. In most programming languages, each object class must implement the `toString` operation. For instance, in the stack below where each item is a character, if we called `myStack.toString()`, we would expect to be returned the string `"K-State"`.
 
Notice that we must read the stack array from top (right) to bottom (left) to get the proper output string. 
In the pseudocode below we first create an empty string and then loop through the stack from top to bottom (0) using the item's own `toString` operation to create the appropriate output string. Notice that there are no preconditions for the operation. This is because if the stack is empty, the `for` loop is not executed and we simply return an empty string. However, because of the loop the `toString` operation runs in order N time. 

```tex
function TOSTRING()
    OUTPUT = ""
    loop I from TOP to 0
        OUTPUT = OUTPUT + MYSTACK[I].TOSTRING()
    end for
    return OUTPUT
end function
```

---
title: "Path Finding Algorithm"
weight: 30
pre: "6. "
---

![Maze Step 3](/images/5/5.7.maze4.png)

The pseudocode for finding the initial path using the stack is shown below. We assume the enclosing class has already defined a stack called `myStack` and the datatype called `Cell`, which represents the squares in the maze. The algorithm also uses three helper functions as described below:

* `getNextCell(maze, topCell)`: computes the next cell based on our current cell's location and direction; 
* `incrementDirection(topCell)`: increments a cell's direction attribute following the clockwise sequence of up, right, down, left, and then finally done, which means that we've tried all directions; and
* `valid(nextCell)`: determines if a cell is valid. A cell is invalid if it is "blocked", is outside the boundaries of the maze, or is in the current path (i.e., if it exists in the stack).

The parameters of `findPath` are a 2-dimensional array called `maze`, the `startCell` and the `endCell`. The algorithm begins by pushing the `startCell` onto `myStack`. The cell at the top of the stack will always represent our current cell, while the remaining cells in the stack represent the path of cells taken to reach the current cell.

Next, we enter a loop, where we will do the bulk of the work. We peek at the cell on the top of the stack in order to use it in our computations. If the `topCell` is equal to our `goalCell`, then we are done and return `true` indicating that we have found a path to the goal.

If we are not at our goal, we check to see if we have searched all directions from the current cell. If that is the case, then the `direction` attribute of the `topCell` will have been set to `done`. If the `direction` attribute of `topCell` is equal to `done`, then we pop the `topCell` of the stack, effectively leaving that cell and returning to the next cell in the stack. This is an algorithmic technique called backtracking.

```tex
function FINDPATH(MAZE, STARTCELL, GOALCELL)
    MYSTACK.PUSH(STARTCELL);
	loop while !MYSTACK.ISEMPTY()
        TOPCELL = MYSTACK.PEEK()
		if TOPCELL equals GOALCELL
			return true
		if TOPCELL.GETDIRECTION() = done then
            MYSTACK.POP()
		else
            NEXTCELL = GETNEXTCELL(MAZE, TOPCELL)
            INCREMENTDIRECTION(TOPCELL)	
			if VALID(MAZE, NEXTCELL) then
				if MYSTACK.ISFULL() then
                    MYSTACK.DOUBLECAPACITY();
				end if
                MYSTACK.PUSH(NEXTCELL)
			end if 
		end if
	end while 
	return false
end function
```

However, if we have not searched in all directions from `topCell`, we will try to explore a new cell (`nextCell`) adjacent to the `topCell`. Specifically, `nextCell` will be the adjacent cell in the direction stored by the `direction` attribute. We then increment the direction attribute of the `topCell` so if we end up backtracking, we will know which direction to try next.

Before we push the `nextCell` onto the stack, we must first check to see if it's a valid cell by calling the helper function `valid`. A cell is valid if it is open to be explored. A cell is invalid if it is "blocked," is outside the boundaries of the maze, or is in the current path (i.e., if it exists in the stack). To help us determine if a cell is in the stack, we will need to extend our stack operations to include a `find` operation that searches the stack while leaving its contents intact. You will get to implement this operation in your project.

If `nextCell` is valid, we then check to make sure that the stack is not already full. If it is, we simply call `doubleCapacity` and continue on our way. Then we push `nextCell` onto `myStack` so it will become our next `topCell` on the next pass through the loop.

After we have explored all possible paths through the maze, the loop will eventually end, and the operation will return `false` indicating no path was found. While this is not the most efficient path finding algorithm, it is a good example of using stacks for backtracking. Also, if we do find a path and return, the path will be saved in the stack. We can then use the previous pseudocode for retracing our steps and going back to the `startCell`.

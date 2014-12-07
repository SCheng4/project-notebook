# Design notebook for week ending December 7, 2014

## Description

This week, I added to my previous implementation to support 2D functions in addition to 1D functions.

I found a way to give an upper bound of the asymptotic running time it would take to fill out the DP table for a given function: in a previous architectural decision, I decided to encode a cell's dependency as a tuple of begin and end indices. These indices can either be absolute ("cell(9)") or relative ("cell 2 row above this one"). I noticed that if for a given 1D dependency, if both indices are absolute or both indices are relative, then there must be only constant number of cells between the begin and end indices. On the other hand, if one of the indices is absolute, and the other one is relative, then there are O(n) number of cells between the indices. A similar logic applies to 2D dependencies. Since a dependency is simply how many cells the program potentially has to look in to fill out a cell, this gives me a way to upper-bound the running time of filling out one cell in the table.

After implementing support for 2D tables, I discovered two issues:

* The topological sort I used outputs one valid order to evaluate the cells in the DP table, but it does not necessarily output the one that's the most helpful. For example, if any of the cells in the first row can be evaluated, the algorithm will randomly number them. This becomes more of an issue in 2D tables, because the numbering turns out looking very random and it's not intuitive for the user to interpret.

* I currently evaluate the base cases by calculating a list of all cells in the DP table that satisfies the base case criteria. However, it is possible for a DP cell in the table to depend on a base case cell that is outside the bounds of the DP table. For example, a 2D function can have the base case "i == 0", where the first row is free to fill out. The cell (1, 9) can depend on cell (0, 10), which is a base case cell. Currently the program will not recognize that (0, 10) is a valid cell and return an error telling the user that the DP table cannot be filled out.

I'm tackling the first of these issues by writing my own topological sort function. I decided that the best way is to label the cells in groups: we find all cells that can currently be evaluated and label them with 1, then add them all to the list of evaluated cell, and repeat. (It's somewhat a combination of a topological sort and a BFS.) The algorithm is unsavory because unlike the previous function I used, it's not optimized and has a terrible asymptotic runtime. However, for the relatively small DP tables my DSL is designed to handle, this won't slow down the program in any detectible way.

The second issue involves a refactoring of the functions that evaluates the base cases. I think this is the most important issue for me to work on next week.

In addition, I've begun to add support for user specified DP table size. This would be very helpful if the user is interested to see larger DP tables, and it's especially important if the user wants to use the DSL for a function with base cases that cover most of the cells in the default-sized DP table. The parser component of the feature is complete, but the interpreter end is not yet done.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

For the next week, I will try to finish implementation for custom user table sizes. 

**What questions do you have for your critique partners? How can they best help
you?**

* Does the way I'm estimating the runtime of the DP table make sense? Do you see any problems with it?

* I'm in the middle of some major refactoring and many parts has not yet been fully tested. Can you try out some 2D functions and see if anything breaks? (they probably will) Is the output easy to interpret?

* Is there any features you think the DSL needs?

**How much time did you spend on the project this week?**

1.5 hr - critique
2.5 hr - Implemented 2D DP tables
2 hr - Implemented estimation of running time
0.5 hr - better error handling (many messages, especially the one when DP table cannot be filled out)
1 hr - Added code to parse optional user input table size
1.5 hr - refactored topo sort and bug fixes
1 hr - project notebook, post critique

## Post-critique summary

Emily continued testing my DSL, and from testing 1D functions, she gave some advice and warnings as to difficulties that a 2D function might face. The most important thing for me to keep in mind is that a 2D function will have more than one argument and the program must be careful to check all edge cases.

## Post-critique reflection

Many error handling can be difficult to predict. My program may also undergo a lot of changes as I add support 2D functions. I will have to largely rely on testing to catch all the problems in my program.

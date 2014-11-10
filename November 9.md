# Design notebook for week ending November 9, 2014

## Description

I've decided on my abstract syntax. It's clearly easily extendible to accomodate DP tables of higher dimensions. I've done major work in the interpreter. Given a program encoded in the IR, it can produce the order in which the DP cells should be filled in. It also has some error handling if the user enters a set of dependencies that cannot be fulfilled or includes a circular dependency.

Some examples:
```
Program(OneD(), BaseCases(List(OneDCell(0))), Dependencies(List(OneDDep(-1))))
```
The above IR denotes a recursive function of one dimension, where cell 0 can be filled out for free. All other cells depend on the cell right before it, denoted by the (-1) offset.

Evaluating the program produces:
```
List(OneDCell(0), OneDCell(1), OneDCell(2), OneDCell(3), OneDCell(4), OneDCell(5), OneDCell(6), OneDCell(7), OneDCell(8), OneDCell(9))
```
The results indicates that, of course, we should begin with cell 0, then fill the table from left to right in order.

I've also made a first design of the syntax for my DSL, the rough specification is on [my project wiki](https://github.com/SCheng4/DSL-Project-Sisi-Cheng/wiki). The most important decision I've made on the concrete syntax is that I will not be parsing an arbitrary function name or variable names, but provide defaults (the function must be named foo(), and the variables must be i, j, and k, in that order). This is because the code required to keep track of the function and variable names is complex, yet this adds next to nothing to the functionality of the DSL. Both are completely arbitrary, and at best serves as more intuitive naming convention for the problem the user is working on. I will make this tradeoff in order to focus on other more critical functionalities of the language.

I've begun setting up the parser for this language, though I have not yet implemented any parts I have questions about (see below).

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The important issue I have not yet handled in any of my code is how to support a DP problem is each cell is dependent on a non-constant number of cells (i.e. each cell depends on every cell before it.). This requires a new mechanism and may alter existing code, especially the existing error-handling mechanisms. My best idea is to implement its own Dependency subclasses that encapsulate the meaning of "depending on every cell before it" or "depending on every cell after it". I will obviously need to add to the concrete syntax to support it as well.

**What questions do you have for your critique partners? How can they best help
you?**

* What do you think of the decision I made to not support custom function and variable names? 
* Any idea how else to represent non-constant number of dependencies? Is it enough to have just the 2 extra cases?

**How much time did you spend on the project this week?**

* 1 hr - critique
* 0.5 hr - post-critique
* 1 hr - abstract syntax
* 4.5 hr - evaluator
* 1 hr - added error handling to evaluator
* 1.5 hr - syntax
* 1 hr - project notebook

## Post-critique summary

Emily, my critic this week, warned that error-handling will be challenging and determining the syntax for the language may be difficult even after the abstract syntax is decided. She also suggested an additional feature of outputting the dependencies of each cell and recommended that I work in small increments so that I can test along with way.

## Post-critique reflection

I'm glad to have someone who may have been a potential user of my DSL as my critic. As I develop my syntax and output, I will definitely ask Emily for her opinion.

The most important feedback I got this week was the suggestion that I also output the dependecy of each cell. I have not thought about this before, since I thought outputting the order in which the DP table should be filled out would be enough. But for each DP table, there are frequently multiple different orders it can be filled out, and it may be helpful to include the dependency of each cell in a digestable format (i.e. "Each cell depends on every cell above it"). Frequently it's a little difficult to picture each cell's dependency from the code, especially as the DP table gains more dimensions. I'm considering adding this as an additional output, which may involve slight changes as I design my abstract syntax; I already all the information I need to add this output, but a different ways to represent the information may make it easier to output it in a readable format.



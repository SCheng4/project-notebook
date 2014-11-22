# Design notebook for week ending November 23, 2014

## Description

The biggest change I made this week was modifying and implementing the base case syntax and implementation. The current syntax for base cases is a comma-separated list, where each item is one or more clauses connected by &&. To implement this, I had to add many new classes representing different components of base case clauses to the AST.

I also implemented output for 1D programs. For example, the user input for a recursive Fibonacci function is:

```
def function(i):
	if (i == 0, i == 1):
		return
	else consider:
		function(i-1),
		function (i-2)
```

When this program runs, it produces:

```
The DP table has dimension 1 x n.
These cells labelled with 0 are the base cases and can be filled in for free.
The other numbers indicate one order in which the remaining cells can be filled in.
(Note that there are frequently more than one order to fill the DP table.)
+---+---+---+---+---+---+---+---+---+---+
| 0 | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
+---+---+---+---+---+---+---+---+---+---+
```

Finally, I caught a few off-by-one bugs in my program and added more error messages throughout the program.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I have two pressing issues: I'd like to make sure that 1D programs are intuitive and as perfect as they can be before expanding the program to handle 2D programs next week and after Thanksgiving. Catching all errors in a way that makes sense is also difficult. The best way I've found to test for error is to simply come up with lots of slightly-incorrect programs, especially ones that users are likely to produce by accident, and see how the program reacts to it.

**What questions do you have for your critique partners? How can they best help
you?**

Do you have any feedback on how 1D programs are handled currently, from parsing to evaluating to output? Do you foresee any difficulty when I expand my project to inlude 2D programs?

If you have the chance, could you download my project and try out a few examples? (I can help with setting it up if we have time Monday in class.) If not, could you help think of any cases of incorrect programs that I may have missed? A list of the errors I've come up with and handled is on the [project wiki](https://github.com/SCheng4/DSL-Project-Sisi-Cheng/wiki)

**How much time did you spend on the project this week?**
1 hr - critique
1 hr - added parser and AST for base cases
1.5 hr - added interpreter for 1D base cases (a lot of things are working!)
1.5 hr - printing DP table
2 hr - testing parser, catching more errors, debugging program
0.5 hr - updated project wiki
1 hr - post critique, project notebook

## Post-critique summary

My critique partner, Emily, thinks my new base case syntax makes sense and is less confusing than statements that could have arbitrary nesting using both && and ||.

Emily is also concerned about error-checking in my program. Since the user can input any text they like, there are many possibilities for errors.

## Post-critique reflection

Based on Emily's feedback, I went ahead and implemented the base case syntax. It involved significant additions to the AST and evaluator. I also spent more time on error-checking. Error-checking is quite difficult because errors can occur both in the parser and evaluator. A correctly-parsed program may still fail during evaluation.



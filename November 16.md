# Design notebook for week ending November 16, 2014

## Description

The major design decision I made this week was the syntax and IR for the dependencies of each DP cell. In my initial design, I encoded the dependencies as simply a list of cells in the matrix, but that was insufficient to encode dependencies like "the DP cell depend on every cell in the row before it". Changing each dependency to a range of cells (with some major refactoring) fixed this issue.

I designed more of the concrete syntax and implemented most of the parser. The parser can now parse recursive functions with both 1 and 2 arguments, except for the base cases. As I worked on the parser, I added some basic error-handling, such as checking for keyword misspellings and missing function parts. The error-handling is not perfect and does not always return the most helpful message, but I hope it will be enough to  help a user debug their program

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The next most important decision I need to decide is how to encode the base cases of a recursive function. I previously designed this to be a nested && and || cases, but I quickly realized that the syntax can appear ambiguous and difficult for the user (and difficult to parse).

**What questions do you have for your critique partners? How can they best help
you?**

Help me decide my concrete syntax for encoding base cases for a function? My current alternative idea is encode it as a list of logical && statements. I eliminate a lot of ambiguity by replacing the || in the original design with commas. So a complex base case example may be: i == 0 && j == 0, i == j, i > 3 && j < 2.

I would obviously have to somehow reject base case clauses that are unsatisfiable (i < 3 && i > 5).

The logic to handle these base cases may be complicated enough that I need to do some refactoring and move this logic from the parser to the interpreter.

**How much time did you spend on the project this week?**

1 hr - critique Emily's project
2 hr - refactored code to include more general dependency handling
0.5 hr - post critique, modify syntax design
2.5 hr - wrote parser
1.5 hr - added more error handling to parser
1 hr - added language implementation and design
0.5 - project notebook

## Post-critique summary

Emily supports my decision to make the function name hard-coded and not customizable. She thinks customizable variable name is a fairer trade-off and I should keep it in mind if the implementment is not too difficult. Emily found some problems with my syntax's encoding of dependencies. Otherwise, she believes my DSL design and implementation is at a good position.

## Post-critique reflection

Emily and other members of my critique group came up with a design for encoding dependencies as a "range" of cells instead of just one single index. I think this is much more general than my previous design and a great improvement. 

Based on this decision, I see how I need to modify my syntax design to reflect the change in implementation design.

This suggestion has pushed my project forward a lot, and opened possibilities for implementing a large portion of one of my extension goals.




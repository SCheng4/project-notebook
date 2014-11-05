# Design notebook for week ending November 9, 2014

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

**What questions do you have for your critique partners? How can they best help
you?**

**How much time did you spend on the project this week?**

1 hr - critique
0.5 hr - post-critique

## Post-critique summary

Emily, my critic this week, warned that error-handling will be challenging and determining the syntax for the language may be difficult even after the abstract syntax is decided. She also suggested an additional feature of outputting the dependencies of each cell and recommended that I work in small increments so that I can test along with way.

## Post-critique reflection

I'm glad to have someone who may have been a potential user of my DSL as my critic. As I develop my syntax and output, I will definitely ask Emily for her opinion.

The most important feedback I got this week was the suggestion that I also output the dependecy of each cell. I have not thought about this before, since I thought outputting the order in which the DP table should be filled out would be enough. But for each DP table, there are frequently multiple different orders it can be filled out, and it may be helpful to include the dependency of each cell in a digestable format (i.e. "Each cell depends on every cell above it"). Frequently it's a little difficult to picture each cell's dependency from the code, especially as the DP table gains more dimensions. I'm considering adding this as an additional output, which may involve slight changes as I design my abstract syntax; I already all the information I need to add this output, but a different ways to represent the information may make it easier to output it in a readable format.



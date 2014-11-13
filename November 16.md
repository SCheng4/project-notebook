# Design notebook for week ending November 16, 2014

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

1 hr - critique Emily's project
2 hr - refactored code to include more general dependency handling
0.5 hr - post critique, modify syntax design

## Post-critique summary

Emily supports my decision to make the function name hard-coded and not customizable. She thinks customizable variable name is a fairer trade-off and I should keep it in mind if the implementment is not too difficult. Emily found some problems with my syntax's encoding of dependencies. Otherwise, she believes my DSL design and implementation is at a good position.

## Post-critique reflection

Emily and other members of my critique group came up with a design for encoding dependencies as a "range" of cells instead of just one single index. I think this is much more general than my previous design and a great improvement. 

Based on this decision, I see how I need to modify my syntax design to reflect the change in implementation design.

This suggestion has pushed my project forward a lot, and opened possibilities for implementing a large portion of one of my extension goals.




# Design notebook for week ending November 2, 2014

## Description

The most important decisions I made this week involved finalizing my project ideas and initial decisions on host languages and project tools.

I thought more thoroughly about what may make a reasonable-sized project for the time frame of this final project, and designed my project to have a reachable base goal with a variety of features I can add in as time allows.

After researching various parser tols for Python such as PyPEG and PyPy, I decided to implement the DSL in Scala with the Packrat Parser we previously used. The Python parsers all have much less customizable syntax error messages that leaves very little room for producing helpful error messages. The overhead of learning a new parsing library may also not make up for the ease of Python over Scala in the evaluator phase of the project.

I did some preliminary brain-storming for what's needed to evaluate a program and sketched out what a DP table representation may look like. I left some quick notes in the [project wiki](https://github.com/SCheng4/DSL-Project-Sisi-Cheng/wiki).

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most important design decision for the upcoming week is the abstract syntax for the language. This step is crucial because the intermediate representation must be relatively easy to implement so I can make a prototype which supports basic programs in my DSL, and at the same time, the IR must be extensible to allow additions without too much efforts.

**What questions do you have for your critique partners? How can they best help
you?**

* Do you see the timeline and scope of my project as reasonable?
* Do you foresee any step taking much longer or shorter than I anticipate, or any significant difficulty with any part of the project?
* Do you have any suggestions for parsing libraries I can look into?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

1 hour - brainstorming projects and talking to potential users
2 hours - writing project design and plan
2 hours - exploring alternative host languages
0.5 hours - setting up project files in Scala 
0.5 hours - project notebook
1.5 hour - brainstorming design and implementation ideas; researched topo sort in Scala; added project wiki.

## Post-critique summary

Emily, my critic this week, warned that error-handling will be challenging and determining the syntax for the language may be difficult even after the abstract syntax is decided. She also suggested an additional feature of outputting the dependencies of each cell and recommended that I work in small increments so that I can test along with way.

## Post-critique reflection

I'm glad to have someone who may have been a potential user of my DSL as my critic. As I develop my syntax and output, I will definitely ask Emily for her opinion.

The most important feedback I got this week was the suggestion that I also output the dependecy of each cell. I have not thought about this before, since I thought outputting the order in which the DP table should be filled out would be enough. But for each DP table, there are frequently multiple different orders it can be filled out, and it may be helpful to include the dependency of each cell in a digestable format (i.e. "Each cell depends on every cell above it"). Frequently it's a little difficult to picture each cell's dependency from the code, especially as the DP table gains more dimensions. I'm considering adding this as an additional output, which may involve slight changes as I design my abstract syntax; I already all the information I need to add this output, but a different ways to represent the information may make it easier to output it in a readable format.



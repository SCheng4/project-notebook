# Design notebook for week ending November 2, 2014

## Description

The most important decisions I made this week involved finalizing my project ideas and initial decisions on host languages and project tools.

I thought more thoroughly about what may make a reasonable-sized project for the time frame of this final project, and designed my project to have a reachable base goal with a variety of features I can add in as time allows.

After researching various parser tools for Python such as PyPEG and PyPy, I decided to implement the DSL in Scala with the Packrat Parser we previously used. The Python parsers all have much less customizable syntax error messages that leaves very little room for producing helpful error messages. The overhead of learning a new parsing library may also not make up for the ease of Python over Scala in the evaluator phase of the project.

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

## Post-critique summary

## Post-critique reflection

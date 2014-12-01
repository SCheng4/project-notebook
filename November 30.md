# Design notebook for week ending November 30, 2014

## Description

Monday's user experience testing was very helpful and gave me a chance to demo my work-in-progress program to a new user. I discovered a minor bug during the demo and fixed it. Then I continued to add some more tests to my test suite. I asked my critique partner for help with error reporting in my program, and made some improvements. Overall, I solidified and cleaned up my code before embarking on the adventure next week to add in support for 2D DP tables.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The next major component of the project is to implement support for 2D programs. Hopefully this stage will involve less architectural changes, since I implemented support for 1D programs while keeping extensibility in mind.

**What questions do you have for your critique partners? How can they best help
you?**

While testing my program so far, was there any error handling that you ran into that may need to be different for 2D and 1D programs? For instance, the issue you mentioned with using a letter in a recursive case but was not in the base case could be a problem that may need to be handled differently for programs of different dimensions (and I will definitely look into it!).

**How much time did you spend on the project this week?**

1 hr - critique
1.5 hr - debugging, added tests, updated wiki (and talked to Prof. Ben!)
1 hr - preliminary evaluation
0.5 hr - project notebook

## Post-critique summary

Emily suggested that I place the directions for interpreting the program's output into the documentation. She also got my program running on her machine and made suggestions for error-catching and different error message outputs.

## Post-critique reflection

Emily was very thorough with testing my program and caught several errors I haven't thought of! Some of them may be out of my scope: the error messages printing only the first letter of a misspelled keyword seems to be a product of the PackratParser's failure(). But other suggestions and errors are definitely ones I will look into and hopefully fix as I implement more functionalities.

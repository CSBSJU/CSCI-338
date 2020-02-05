---
title: "Programming assignment 2"
---

# Introduction

The purpose of this assignment is to implement an algorithm and experimentally
validate its theoretical analysis.

## Efficient closest pair

You need to write a program that will take as input, a single file containing a
list of pairs of points, and output to stdout the closest pair of points among
all of the points, along with the distance between them and the time required to
find them. The input file will be a text representation of the list. For *n*
points, the file will consist of *n+1* lines. The first line will give the
number of points in the file and the following *n* lines will correspond to the
points, each with two space-separated values, representing the coordinates for
the point.

For example, four points would would be stored in a file as:

```
4
0.120000 0.230000
0.340000 0.450000
0.560000 0.670000
0.780000 0.890000
```

Your output file MUST output the values to exactly four decimal points of
precision using at least ten characters. Here is a C language function you
could use for outputting your results:

```c
/**
* @brief Output necessary information for the experiment.
*
* @param p1       The zero based index of point 1.
* @param p2       The zero based index of point 2.
* @param dist     The Euclidean distance between point 1 and point2.
* @param elapsed  The elapsed time to find the distance between the two points.
*/
void
print_results(size_t const p1, size_t const p2,
              double const dist, double const elapsed)
{
  printf("%zu %zu %10.4f %10.4f", p1, p2, dist, elapsed);
}
```

**When you are reporting time, only report the time to actual compute the
closest pair, not the time to read the file.**

## Testing

Test files are provided at /usr/people/classes/CS338/data/pa1. There are
currently files containing 256 up to 65536 points by powers of two.

The tests file are only provided to get you started. Remember, you will likely
want to run each experiment on more than one input of the same size so that your
results are not skewed by the coordinate distribution in the files that I
provided. Your solution will be evaluated with a different set of files than
those provided for testing.

## What you need to turn in

1. The source code of your programs.
1. A short report (PDF format) including the following:
   * A description of anything that I should know about your program. This could
     be limitations like, it only works for XXX files, but not YYY file, or
     challenges that prevented you from completing the assignment.
   * An analysis comparing and contrasting the theoretical analysis of
     *EfficientClosestPair* (from the book), with your experimental analysis.
     Does your experimental analysis support the theoretical analysis from the
     book? Why or why not? *You should include plots to support your
     conclusions.*

**Do NOT include the test files. You will lose points for including test
files.**

### Additional specifications related to assignment submission

A makefile must be provided to build the program. And an executable file named
`ecp` must be included to execute the program. The program should take as an
argument, the input file name. The following sequence of commands should work
for your program:

```sh
:> make
:> ./ecp 256.pts
```

If you choose to use an interpreted language, like Java or Python for this, then
the executable file mentioned above will just be a Bash script that invokes the
correct interpreter for your chosen language. For example, a Java programmer
might have a `ecp` file that looks like the following:

```bash
#!/bin/bash

# The $@ will pass any command-line arguments to this script, to the Java
# program. This of course assumes your Java class was called ECP.
java ECP "$@"
```

and a makefile that looks like:

```
ECP.class: ECP.java
	javac ECP.java
```

The point here being that the evaluator can build and run all programs in a
consistent way, i.e., without considering what programming language each program
was written in.

### Packaging your submission

All files (code + report) MUST be in a single directory and the directory's name
MUST be your university student ID. Your submission directory MUST include at
least the following files (named accordingly) as well as the source code for you
program:

```
<Student ID>/Makefile
<Student ID>/report.pdf
```

Submission MUST be in .tgz

The following sequence of commands should work (*read: complete with no error
messages reported)* on your submission file:

```sh
:> tar xzvf <Student ID>.tgz
:> cd <Student ID>
:> make
:> test -x ecp || echo "You have not named your executable correctly or it is not executable"
```

This ensures that your submission is packaged correctly, your directory is named
correctly, your makefile works correctly, and your output executable file is
named correctly. It does not ensure that your program works correctly or gives
the correct solution! If any of these does not work, modify it so that you do
not lose points. I can answer questions about correctly formatting your
submission BEFORE the assignment is due. Do not expect questions to be answered
the night it is due.

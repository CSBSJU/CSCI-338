---
title: "Programming assignment 1"
---

# Introduction

The purpose of this assignment is to implement an algorithm and get familiar
with the processes related to programming assignments for this course.

## Topological sorting

You need to write a program that will take as input, a single file containing
the edges of a directed graph, and output to *stdout* the vertices sorted in
topological order, and the time required to sort them. The input file will be a
text representation of the graph. For a graph with *n* vertices and *m* edges,
the file will consist of *m* lines. Each line will contain two space-separated
values, representing the starting and ending vertices for an edge. The vertex
values will be indexed starting from 1 and no line will contain any value
greater than *n*.

For example, a complete graph with four vertices would would be stored in a file
as:

```
1 2
1 3
1 4
2 1
2 3
2 4
3 1
3 2
3 4
4 1
4 2
4 3
```

You may assume that the file is sorted first by the start vertex, then by the
end vertex. If you want to be sure, Linux has a nice utility called `sort` to
help you out:

```
:> sort -c -n -k1,2 graph.ij
```

will check a file to see if it is sorted according to the specifications above,
and

```
:> sort -n -k1,2 graph.ij > graph.ij.sorted
```

will give you the correctly sorted version of graph.ij, stored in a file called
graph.ij.sorted.

Your output file MUST output the vertices as whole numbers (read: no decimal
point or places). Here is a C language function you could use for outputting
your results:

```c
/**
* @brief Output necessary information for the experiment.
*
* @param order    An array containing the topologically sorted vertex ids.
* @param n        The number of vertices in the graph.
* @param elapsed  The elapsed time to sort the vertices of the graph.
*/
void print_results(size_t const *order, size_t const n, double const elapsed) {
  for (size_t i = 0; i < n; i++)
    printf("%zu\n", order[i]);
  printf("%010.4f", elapsed);
}
```

**When you are reporting time, only report the time to actually compute the
sorted order, not the time to read the file.**

## Testing

Test files are provided at /usr/people/classes/CS338/data/pa1. There are
currently several graphs there of varying sizes and densities.

The tests file are only provided to get you started. Your solution will be
evaluated with a different set of files than those provided for testing.

## What you need to turn in

1. The source code of your programs.
1. A short report (PDF format) including the following:
   * The approach that you took to implementing this algorithm, i.e., were you
     able to implement the algorithm exactly as described in the book, did you
     need to make any modifications to it, etc?
   * A description of anything that I should know about your program. This could
     be limitations like, it only works for XXX files, but not YYY file, or
     challenges that prevented you from completing the assignment.
   * A real-world problem that this algorithm could help to solve and a brief
     description of how this algorithm will be useful for solving it.

**Do NOT include the test files. You will lose points for including test
files.**

### Additional specifications related to assignment submission

A makefile must be provided to build the program. And an executable file named
`tsort` must be included to execute the program. The program should take as an
argument, the input file name. The following sequence of commands should work
for your program:

```sh
:> make
:> ./tsort wiki.ij
```

If you choose to use an interpreted language, like Java or Python for this, then
the executable file mentioned above will just be a Bash script that invokes the
correct interpreter for your chosen language. For example, a Java programmer
might have an executable `tsort` file that looks like the following:

```bash
#!/bin/bash

# The $@ will pass any command-line arguments to this script, to the Java
# program. This of course assumes your Java class was called TSort.
java TSort "$@"
```

and a makefile that looks like:

```
TSort.class: TSort.java
	javac TSort.java
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
:> test -x tsort || echo "You have not named your executable correctly or it is not executable"
```

This ensures that your submission is packaged correctly, your directory is named
correctly, your makefile works correctly, and your output executable file is
named correctly. It does not ensure that your program works correctly or gives
the correct solution! If any of these does not work, modify it so that you do
not lose points. I can answer questions about correctly formatting your
submission BEFORE the assignment is due. Do not expect questions to be answered
the night it is due.

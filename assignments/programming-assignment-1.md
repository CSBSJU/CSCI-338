---
title: "Programming assignment 1"
---

The purpose of this assignment is to implement a relatively simple algorithm
and experimentally validate our theoretical analysis.

To time a computation in Java, call System.nanotime() at the beginning and end
of the computation; the difference is the number of nanoseconds between the two
calls. The actual resolution of the method is probably somewhere between a
microsecond and a millisecond, so you may need to run the same test 1000 times
(or more) in a loop and divide the total time by the number of test runs to get
an accurate running time.

1. Implement the *BruteForceClosestPair* algorithm on page 109 of the textbook
   using the optimization of only computing the square root for the minimum
   distance pair. Generate random sets of points: 100 points, 1000 points and
   10000 points; run and time the algorithm based on those test cases. Determine
   whether your measured run times are consistent with the expected big-Oh
   complexity of the algorithm.

---
title: "Assignment 1"
---

### Part 1
Solve the following problems from the text book:

1. Chapter 1.2, problem 1
1. Chapter 1.2, problem 2
1. Chapter 1.4, problem 4
1. Chapter 1.4, problem 10
1. Chapter 2.2, problem 2
1. Chapter 2.2, problem 3
1. Chapter 2.3, problem 4(abcd)
1. Chapter 2.3, problem 5(abcd)

### Part 2
Solve the following problem:

1. Consider the following recursive algorithm

   ```
   ALGORITHM Min2(A[l..r])
     if l = r
       return A[l]
     else
       temp1 := Min2(A[l..(l+r)/2])
       temp2 := Min2(A[(l+r)/2+1..r])
       if temp1 < temp2
         return temp1
       else
         return temp2
   ```

   a. Set up a recurrence relation for the algorithm's basic operation count and
      solve it.

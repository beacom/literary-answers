# Chapter 1 Introduction
## 1.1 Algorithms
### 1.1-1 
Using figure 1.2 as a model, illustrate the operation of `INSERTION-SORT` on the array A = (31, 41, 59, 26, 41, 58).
![Insertion sort solution diagram for 31, 41, 59, 26, 41, 58](intro-to-algorithms-1.1-1.svg)
### 1.1-2 
Rewrite the `INSERTION-SORT` procedure to sort into nonincreasing instead of nondecreasing order.

This is largely a matter of changing the logic from greater than to less than.

```
INSERTION-SORT(A)
 for j <- 2 to length[A]
  do key <- A[j]
    > Insert A[j] into the sorted sequence A[1..j-1].
    i <- j - 1
    while i > 0 and A[i] < key
     do A[i + 1] <- A[i]
      i <- i - 1
    A[i + 1] <- key
```
# 1.1-3
Consider the **searching problem**:
 **Input:** A sequence of n numbers A = (a<sub>1</sub>, a<sub>2</sub>,....a<sub>n</sub>) and a value _v_.

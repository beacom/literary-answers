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
### 1.1-3
Consider the **searching problem**:
 **Input:** A sequence of n numbers A = (a<sub>1</sub>, a<sub>2</sub>,....a<sub>n</sub>) and a value _v_.
 **Output:** An index i such that _v_ = A[i] or tthe special value `NIL` if _v_ does not appear in A.
 Write pseudocode for **linear search**, which scans through the sequence, looking for _v_.

 This is a matter of iterating over the sequence and performing an equals comprison operation.

 ```
 LINEAR-SEARCH(A, v)
  for i <- 1 to length[A}
   if A[i] = v
    return A[i]
  return NIL
 ```
### 1.1-4
Consider the problem of adding two n-bit binary integers, stored in two n-element arrays A and B. The sum of the two integers should be stored in binary form in an (n + 1)-element array C. State the problem formally and write pseudocode for adding the two integers.

That seems like an adequately formal statement of the problem. The solution is to iterate over the binary arrays A and B from least to greatest place and adjust bits in the current and next place in array C appropriately. Importantly, this involves calculating an intermediate value for the next place in array C when two bits have a value of 1 to account for base 2 carry during addition and account for a potential 1 value already in the C array from previous bit additions.
```
BINARY-ADDITION(A, B)
 C <- arrayOfLength[length[A]]
 for i <- 1 to length[A]
  if A[i] = 0 and B[i] = 0
   C[i] <- ADD-BINARY-DIGITS(C[i], 0)
  else if A[i] = 0 and B[i] = 1
   if C[i] = 1
    C[i + 1] <- ADD-BINARY-DIGITS( C[i + 1], 1)
   C[i] <- ADD-BINARY-DIGITS(C[i], 1)
  else if A[i] = 1 and B[i] = 1
   C[i + 1] <- ADD-BINARY-DIGITS( C[i + 1], 1)
   C[i] <- 0
 return C

ADD-BINARY-DIGITS(v1, v2)
 if v1 = 0 and v2 = 0
  return 0
 else if v1 = 1 and v2 = 1
  return 0
 else
  return 1
```

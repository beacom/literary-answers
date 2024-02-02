# Chapter 1 Introduction
## 1.1 Algorithms
### 1.1-1 
Using figure 1.2 as a model, illustrate the operation of `INSERTION-SORT` on the array A = (31, 41, 59, 26, 41, 58).
![Insertion sort solution diagram for 31, 41, 59, 26, 41, 58](intro-to-algorithms-1.1-1.svg)
### 1.1-2 
Rewrite the `INSERTION-SORT` procedure to sort into nonincreasing instead of nondecreasing order.

This is a matter of changing the comparison logic from greater than to less than.

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

 This is a matter of iterating over the sequence and performing an equals comprison operation and returning NIL if no value was found.

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
### 1.2-1
Consider sorting _n_ numbers stored in array A by first finding the smallest element of A and putting it in the first entry of another array B. Then find the second smallest element of A and put it in the second entry of B. Continue in this manner for the _n_ elements of A. Write pseduocode for the algorithm, which is known as selection sort. Give the best-case and worst-case running times of selection sort in Θ-notation.

The pseudocode below loops over array B and for each element in B loops over A to find the lowest remaining value in A. The values in A are replaced by NIL as they are copied to B. The worst case running time is Θ(n<sup>2</sup>).

```
SELECTION-SORT(A)
 B <- arrayOfLength[length[A]]
 for j <- 1 to length[B]
  for i <- 1 to length[A]
   if currentValue = NIL and A[i] != NIL
    currentValue <- A[i]
    currentIndex <- i
   else if currentValue > A[i]
    currentValue <- A[i]
    currentIndex <- i
  B[j] <- currentValue;
  A[currentIndex] <- NIL
```
### 1.2-2
Consider linear search again (see exercise 1.1-3). How many elements of the input sequence need to be checked on the average, assumming that the element being searched for is equally likely to be any element in the array? How about in the worst case? What are the average-case and worst-case running times of linear search in Θ-notation? Justify your answers.

Half of the elements will need to be compared on average with an equal distribution of searched for elements in the array. In the worst case, meaning the searched for element is the last one in the array, all elements will need to be compared. The average case scenario is Θ(n/2) and the worst case scenario is Θ(n).

### 1.2-3
Consider the problem of determining whether an arbitrary sequence (x<sub>1</sub>,x<sub>2</sub>,...,x<sub>n</sub>) of _n_ numbers contains repeated occurrences of some number. Show that this can be done in Θ(_n_ lg _n_) time, wher lg _n_ stands for log<sub>2</sub> _n_.

A repeated occurance is finding the same value more than once. So starting with the first element, search through the rest of the sequence looking for that value. Repeat on the second element, but it is not necessary to compare to the previous element because those two elements have already been compared. So as we continue through the sequence there are fewer elements to compare to each time. The value log<sub>2</sub> _n_ represents the decreasing number of comparisons necessary in addition to each element of the sequence, hence Θ(_n_ lg _n_). 

### 1.2-4
Consider the problem of evaluating a polynomial at a point. Given n coefficients a<sub>0</sub>, a<sub>1</sub>,...,a<sub>n-1</sub> and a real number _x_, we wish to compute $`\displaystyle\sum_{i=0}^{n-1} a_i x_i `$. Describe a straightforwaard Θ(n<sup>2</sup>)-time algorithm for this problem. Describe a Θ(n)-time algorithm that uses the following method (called Horner's rule) for rewriting the polynomial:
$`\displaystyle\sum_{i=0}^{n-1} a_i x_i `$ = (...(a<sub>n-1</sub>x + a<sub>n-2</sub>)x + ... + a<sub>1</sub>)x + a<sub>0</sub>.

### 1.2-5
Express the function n<sup>3</sup>/1000 - 100n<sup>2</sup> - 100n + 3 in terms of Θ-notation.

### 1.2-6
How can we modify almost any algorithm to have a good best-case running time?

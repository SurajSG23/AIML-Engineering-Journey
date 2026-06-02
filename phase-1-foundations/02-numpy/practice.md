# NumPy Complete Guide

> NumPy (Numerical Python) is the foundation of scientific computing in Python.
>
> Most Data Science, Machine Learning, Deep Learning, and AI libraries are built on top of NumPy.
>
> If Pandas is used to work with datasets, NumPy is used to work with numbers efficiently.

---

# What is NumPy?

NumPy is a Python library used for:

* Fast numerical computations
* Working with arrays
* Mathematical operations
* Linear Algebra
* Statistics
* Machine Learning

Import NumPy:

```python
import numpy as np
```

The alias `np` is the standard convention used worldwide.

---

# Why NumPy Exists

Suppose we have a list:

```python
numbers = [1, 2, 3, 4, 5]
```

Python lists are flexible but not optimized for numerical computations.

NumPy arrays are:

* Faster
* More memory efficient
* Easier to perform mathematical operations on

---

# Creating Arrays

## 1D Array

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

print(arr)
```

Output:

```python
[1 2 3 4 5]
```

Think of this as:

```text
[1 2 3 4 5]
```

---

## 2D Array

```python
arr = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print(arr)
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

Think of it as a table:

```text
1 2 3
4 5 6
```

---

## 3D Array

```python
arr = np.array([
    [
        [1,2],
        [3,4]
    ],
    [
        [5,6],
        [7,8]
    ]
])
```

Used in:

* Images
* Videos
* Deep Learning

---

# Understanding Dimensions

Check dimensions:

```python
arr.ndim
```

Example:

```python
np.array([1,2,3]).ndim
```

Output:

```python
1
```

---

Check shape:

```python
arr.shape
```

Example:

```python
(2,3)
```

Meaning:

```text
2 rows
3 columns
```

---

Check total elements:

```python
arr.size
```

---

Check data type:

```python
arr.dtype
```

Output:

```python
int64
```

---

# Creating Special Arrays

## Zeros

```python
np.zeros((3,3))
```

Output:

```text
[[0. 0. 0.]
 [0. 0. 0.]
 [0. 0. 0.]]
```

---

## Ones

```python
np.ones((2,2))
```

---

## Full

```python
np.full((3,3), 5)
```

Output:

```text
[[5 5 5]
 [5 5 5]
 [5 5 5]]
```

---

## Identity Matrix

```python
np.eye(3)
```

Output:

```text
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
```

Used heavily in Linear Algebra.

---

# Creating Sequences

## arange()

Works like Python range.

```python
np.arange(0,10)
```

Output:

```text
[0 1 2 3 4 5 6 7 8 9]
```

---

Step size:

```python
np.arange(0,20,2)
```

Output:

```text
[0 2 4 6 8 10 12 14 16 18]
```

---

## linspace()

Creates evenly spaced numbers.

```python
np.linspace(0,10,5)
```

Output:

```text
[0. 2.5 5. 7.5 10.]
```

Useful for plotting graphs.

---

# Array Indexing

```python
arr = np.array([10,20,30,40])
```

First element:

```python
arr[0]
```

Output:

```python
10
```

---

Last element:

```python
arr[-1]
```

Output:

```python
40
```

---

# Slicing

```python
arr[1:4]
```

Output:

```python
[20 30 40]
```

---

# Indexing 2D Arrays

```python
arr = np.array([
    [1,2,3],
    [4,5,6]
])
```

Access:

```python
arr[0,1]
```

Output:

```python
2
```

Meaning:

```text
Row 0
Column 1
```

---

# Array Operations

NumPy supports vectorized operations.

---

Addition

```python
arr + 10
```

Output:

```python
[11 12 13]
```

---

Multiplication

```python
arr * 2
```

Output:

```python
[2 4 6]
```

---

Division

```python
arr / 2
```

---

Power

```python
arr ** 2
```

Output:

```python
[1 4 9]
```

---

# Why NumPy is Powerful

Without NumPy:

```python
result = []

for x in numbers:
    result.append(x * 2)
```

With NumPy:

```python
arr * 2
```

Cleaner and much faster.

---

# Mathematical Functions

## Sum

```python
np.sum(arr)
```

---

## Mean

```python
np.mean(arr)
```

---

## Median

```python
np.median(arr)
```

---

## Standard Deviation

```python
np.std(arr)
```

---

## Variance

```python
np.var(arr)
```

---

## Minimum

```python
np.min(arr)
```

---

## Maximum

```python
np.max(arr)
```

---

# Reshaping Arrays

Original:

```python
arr = np.array([1,2,3,4,5,6])
```

Shape:

```text
(6,)
```

---

Convert to matrix:

```python
arr.reshape(2,3)
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

---

Convert to:

```python
arr.reshape(3,2)
```

Output:

```text
[[1 2]
 [3 4]
 [5 6]]
```

---

# Flattening Arrays

Convert matrix into one row.

```python
arr.flatten()
```

Output:

```text
[1 2 3 4 5 6]
```

---

# Combining Arrays

## Horizontal Stack

```python
a = np.array([1,2,3])
b = np.array([4,5,6])

np.hstack((a,b))
```

Output:

```text
[1 2 3 4 5 6]
```

---

## Vertical Stack

```python
np.vstack((a,b))
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

---

# Random Numbers

Random numbers are heavily used in Machine Learning.

---

Random float:

```python
np.random.rand()
```

---

Random array:

```python
np.random.rand(3,3)
```

---

Random integer:

```python
np.random.randint(1,10)
```

---

Set seed:

```python
np.random.seed(42)
```

Ensures reproducible results.

---

# Boolean Indexing

Very useful for filtering.

```python
arr = np.array([10,20,30,40,50])
```

Select values greater than 25:

```python
arr[arr > 25]
```

Output:

```python
[30 40 50]
```

---

# Broadcasting

One of NumPy's most powerful features.

```python
arr = np.array([1,2,3])

arr + 5
```

Output:

```python
[6 7 8]
```

NumPy automatically applies the operation to every element.

---

# Linear Algebra

Machine Learning relies heavily on Linear Algebra.

---

## Dot Product

```python
a = np.array([1,2,3])
b = np.array([4,5,6])

np.dot(a,b)
```

Output:

```python
32
```

Calculation:

```text
1×4 + 2×5 + 3×6
```

---

## Matrix Multiplication

```python
A @ B
```

or

```python
np.matmul(A,B)
```

---

## Transpose

Rows become columns.

```python
A.T
```

Example:

```text
1 2 3
4 5 6
```

becomes

```text
1 4
2 5
3 6
```

---

# NumPy in Machine Learning

Almost every ML workflow uses NumPy.

Examples:

* Feature matrices
* Mathematical calculations
* Neural network computations
* Data preprocessing
* Linear Algebra operations

Scikit-Learn models often expect NumPy arrays as input.

Example:

```python
X = np.array([
    [1200,2],
    [1500,3],
    [1800,4]
])

y = np.array([
    200000,
    250000,
    300000
])
```

Here:

```text
X → Features
y → Target
```

---

# Common Interview Questions

## Difference Between List and NumPy Array

List:

* Slower
* Flexible
* General purpose

NumPy Array:

* Faster
* Memory efficient
* Numerical computations

---

## What is Broadcasting?

Automatic expansion of arrays during operations.

---

## What is Vectorization?

Performing operations on entire arrays without loops.

---

## Why is NumPy Fast?

Because most operations are implemented in optimized C code.

---

# Common Beginner Mistakes

## Forgetting to Import

```python
import numpy as np
```

---

## Shape Mismatch

```python
A + B
```

fails if shapes are incompatible.

Always check:

```python
A.shape
B.shape
```

---

## Confusing Lists with Arrays

```python
[1,2,3] * 2
```

Output:

```python
[1,2,3,1,2,3]
```

But:

```python
np.array([1,2,3]) * 2
```

Output:

```python
[2 4 6]
```

Very different behavior.

---

# NumPy Cheat Sheet

Create Array:

```python
np.array()
```

Zeros:

```python
np.zeros()
```

Ones:

```python
np.ones()
```

Range:

```python
np.arange()
```

Even Spacing:

```python
np.linspace()
```

Shape:

```python
arr.shape
```

Dimensions:

```python
arr.ndim
```

Reshape:

```python
arr.reshape()
```

Flatten:

```python
arr.flatten()
```

Mean:

```python
np.mean()
```

Sum:

```python
np.sum()
```

Standard Deviation:

```python
np.std()
```

Dot Product:

```python
np.dot()
```

Transpose:

```python
A.T
```

Random Numbers:

```python
np.random.rand()
```

---

# Final Thoughts

NumPy is the mathematical engine behind modern Data Science and Machine Learning.

A good learning path is:

```text
Python
   ↓
NumPy
   ↓
Pandas
   ↓
Matplotlib
   ↓
Scikit-Learn
   ↓
Machine Learning
```

Master NumPy first, and every other data science library will become easier to understand.

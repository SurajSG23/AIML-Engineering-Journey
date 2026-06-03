# Linear Algebra for AI and Machine Learning

> Linear Algebra is the language of Machine Learning and Deep Learning.
>
> Every ML model, neural network, image, dataset, and embedding eventually becomes numbers arranged in vectors and matrices.
>
> The goal of this guide is not to turn you into a mathematician.
>
> The goal is to help you understand Linear Algebra well enough to confidently study Machine Learning and Deep Learning.

---

# Why Learn Linear Algebra?

Suppose you have a house price dataset:

| Area | Bedrooms | Price  |
| ---- | -------- | ------ |
| 1200 | 2        | 200000 |
| 1500 | 3        | 250000 |
| 1800 | 4        | 300000 |

Machine Learning does not see:

```text
Area
Bedrooms
Price
```

Instead, it sees:

```text
[
 [1200, 2],
 [1500, 3],
 [1800, 4]
]
```

This is a matrix.

Most Machine Learning is simply:

```text
Data
↓
Matrices
↓
Matrix Operations
↓
Predictions
```

That is why Linear Algebra is important.

---

# Scalars

A scalar is a single number.

Examples:

```text
5
10
100
3.14
```

Examples in AI:

* Age = 21
* Salary = 50000
* Temperature = 30

These are scalars.

---

# Vectors

A vector is a collection of numbers arranged in order.

Example:

```text
[2, 4, 6]
```

Think of a vector as a list of features.

Example:

```text
Student:

Age = 21
CGPA = 8.5
Projects = 5
```

Can be represented as:

```text
[21, 8.5, 5]
```

This is a vector.

---

# Why Vectors Matter

Machine Learning represents most objects as vectors.

Examples:

A house:

```text
[1200, 2]
```

A student:

```text
[21, 8.5, 5]
```

A movie:

```text
[Action, Comedy, Rating]
```

A word embedding:

```text
[0.2, -1.4, 3.1, 0.8, ...]
```

Everything becomes a vector.

---

# Vector Dimensions

Number of elements inside a vector.

Example:

```text
[1,2]
```

Dimension = 2

---

```text
[1,2,3]
```

Dimension = 3

---

```text
[1,2,3,4,5]
```

Dimension = 5

---

In AI:

High-dimensional vectors are common.

Example:

```text
768 dimensions
1024 dimensions
4096 dimensions
```

for modern embeddings.

---

# Vector Operations

---

# Vector Addition

Example:

```text
A = [1,2]

B = [3,4]
```

Add corresponding elements:

```text
A + B

[1+3, 2+4]

[4,6]
```

---

Interpretation

Suppose:

```text
Today's Sales

[10,20]
```

Tomorrow:

```text
[5,10]
```

Total:

```text
[15,30]
```

---

# Vector Subtraction

Example:

```text
[5,7]

-

[2,3]
```

Result:

```text
[3,4]
```

---

# Scalar Multiplication

Multiply every element.

Example:

```text
2 × [1,2,3]
```

Result:

```text
[2,4,6]
```

---

Used in ML when adjusting weights.

---

# Magnitude of a Vector

Magnitude means length.

Example:

```text
[3,4]
```

Magnitude:

```text
√(3² + 4²)

√(9 + 16)

√25

5
```

---

Why It Matters

Magnitude tells us how large a vector is.

Used in:

* Similarity calculations
* Embeddings
* Deep Learning

---

# Unit Vector

A vector with length 1.

Example:

```text
[0.6, 0.8]
```

Magnitude:

```text
1
```

---

Why Useful?

When we care about direction but not size.

---

# Dot Product

Most important concept in Linear Algebra for ML.

---

Example

```text
A = [1,2,3]

B = [4,5,6]
```

Calculation:

```text
1×4 + 2×5 + 3×6

= 4 + 10 + 18

= 32
```

Dot Product:

```text
32
```

---

Intuition

Dot product measures similarity.

Large value:

Vectors point in similar directions.

Small value:

Vectors are less similar.

---

Applications

* Recommendation Systems
* Search Engines
* Word Embeddings
* Neural Networks

---

# Matrices

A matrix is a table of numbers.

Example:

```text
[
 [1,2,3],
 [4,5,6]
]
```

Rows:

```text
2
```

Columns:

```text
3
```

Shape:

```text
(2,3)
```

---

# Why Matrices Matter

Most datasets become matrices.

Example:

```text
Students

Age CGPA Projects

21  8.5   4
22  9.1   6
20  8.0   3
```

Matrix form:

```text
[
 [21, 8.5, 4],
 [22, 9.1, 6],
 [20, 8.0, 3]
]
```

Machine Learning models work with matrices.

---

# Matrix Shape

Shape:

```text
(rows, columns)
```

Example:

```text
[
 [1,2,3],
 [4,5,6]
]
```

Shape:

```text
(2,3)
```

---

# Matrix Addition

Possible only when shapes match.

Example:

```text
A

[
 [1,2],
 [3,4]
]
```

```text
B

[
 [5,6],
 [7,8]
]
```

Result:

```text
[
 [6,8],
 [10,12]
]
```

---

# Matrix Multiplication

One of the most important operations in ML.

---

Example

```text
A

(2×3)
```

```text
B

(3×2)
```

Multiplication is possible because:

```text
Columns of A

=

Rows of B
```

---

Rule:

```text
(m × n)

×

(n × p)

=

(m × p)
```

---

Why Important?

Neural networks repeatedly perform:

```text
Input

×

Weights

=

Output
```

which is matrix multiplication.

---

# Identity Matrix

Special matrix:

```text
[
 [1,0,0],
 [0,1,0],
 [0,0,1]
]
```

Similar to number 1 in multiplication.

---

Example:

```text
A × I = A
```

---

# Transpose

Converts rows into columns.

Example:

```text
A

[
 [1,2,3],
 [4,5,6]
]
```

Transpose:

```text
Aᵀ

[
 [1,4],
 [2,5],
 [3,6]
]
```

---

Why Useful?

Commonly used in:

* Machine Learning
* Statistics
* Neural Networks

---

# Distance Between Points

Suppose:

```text
A = [1,2]

B = [4,6]
```

Distance:

```text
√((4-1)² + (6-2)²)

√25

5
```

---

Applications:

* KNN
* Clustering
* Recommendation Systems

---

# Eigenvalues and Eigenvectors

These sound scary but the intuition is simple.

---

Imagine stretching a rubber sheet.

Most arrows:

* Change length
* Change direction

Some special arrows:

* Change length
* Keep same direction

Those special arrows are Eigenvectors.

The amount of stretching is the Eigenvalue.

---

Why Important?

Used in:

* PCA
* Dimensionality Reduction
* Computer Vision
* Deep Learning

---

For beginners:

Understand the intuition.

Do not worry about calculations yet.

---

# Linear Algebra in Machine Learning

---

# Linear Regression

Uses:

* Vectors
* Matrices
* Matrix multiplication

---

# Neural Networks

Every layer performs:

```text
Input

×

Weights

+

Bias

=

Output
```

This is Linear Algebra.

---

# Recommendation Systems

Use:

* Dot Product
* Similarity

---

# Word Embeddings

Words become vectors.

Example:

```text
King

[0.1, 0.8, -0.2 ...]
```

```text
Queen

[0.2, 0.7, -0.1 ...]
```

Similarity is measured using vector operations.

---

# Computer Vision

Images become matrices.

Example:

```text
Pixel Values

[
 [255,120,30],
 [80,40,10]
]
```

Neural networks process these matrices.

---

# NumPy Examples

Create Vector:

```python
import numpy as np

v = np.array([1,2,3])
```

---

Create Matrix:

```python
A = np.array([
    [1,2],
    [3,4]
])
```

---

Dot Product:

```python
np.dot(
    [1,2,3],
    [4,5,6]
)
```

Output:

```python
32
```

---

Matrix Multiplication:

```python
A @ B
```

---

Transpose:

```python
A.T
```

---

Shape:

```python
A.shape
```

---

# Common Beginner Mistakes

---

## Memorizing Formulas Without Understanding

Bad approach:

```text
Memorize
Forget
Repeat
```

Good approach:

```text
Understand intuition
Practice
Apply
```

---

## Ignoring Shapes

Always check:

```text
(rows, columns)
```

Most Linear Algebra errors come from shape mismatches.

---

## Fear of Matrices

Remember:

A matrix is simply a table of numbers.

Nothing more.

---

# Key Takeaways

1. Scalars are single numbers.
2. Vectors are ordered collections of numbers.
3. Matrices are tables of numbers.
4. Dot product measures similarity.
5. Matrix multiplication powers neural networks.
6. Transpose swaps rows and columns.
7. Distance calculations power clustering and KNN.
8. Eigenvectors are important for advanced ML topics.
9. Most ML datasets are matrices.
10. Linear Algebra is the mathematical language of AI.

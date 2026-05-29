# NumPy

## Overview
Short, practical NumPy notes for AI. Simple explanations, small examples, and clear tips to help with data and math tasks.

---

## 1. Introduction to NumPy

- What is NumPy: a foundational numeric library for Python providing fast array operations and linear algebra tools.
- Why NumPy was created: to provide efficient, vectorized operations on homogeneous numeric data backed by C implementations.
- Why NumPy is faster than Python lists: contiguous memory, contiguous C loops, SIMD-friendly operations, and fewer Python-level loops.
- NumPy's role in AI/ML: base for tensors, numerical routines, and as the backbone for higher-level libraries (Pandas, scikit-learn, PyTorch/TF interoperability).
- Real-world applications: image processing, signal processing, scientific computing, feature preprocessing, batch operations in training.

---

## SECTION 1 — NumPy Foundations

### 2. Understanding Arrays

What is an array?
- A grid of numbers with the same type (like a matrix). It can have many dimensions.

Why use arrays?
- They let you do math on many numbers at once (fast and memory-friendly).

Lists vs arrays:
- Lists are flexible but slow for math. Arrays are fast and use less memory.

Create an array:
```python
import numpy as np
arr = np.array([1, 2, 3])
```

Shapes and dims:
- 1D is a list of numbers, 2D is rows and columns, 3D+ are tensors (like image batches).
- `arr.shape` tells the size of each dimension.

AI note: features, labels, and weights are usually NumPy arrays.

---

### 3. Array Attributes

Common attributes:
- `shape`: size of each axis
- `ndim`: number of axes
- `size`: total elements
- `dtype`: element type (e.g., `float32`)
- `itemsize`: bytes per element

Memory layout matters for speed. Some arrays are C-contiguous; others are not.

Example:
```python
a = np.arange(12).reshape(3,4)
print(a.shape, a.ndim, a.size, a.dtype)
```

---

### 4. Creating Arrays

Create arrays:
- `np.array()` from lists
- `np.zeros((m,n))`, `np.ones((m,n))`, `np.empty((m,n))`
- `np.arange()` and `np.linspace()` for ranges
- Use `np.random.default_rng()` for random numbers
- Identity: `np.eye(n)`

Examples:
```python
np.zeros((2,3))
np.linspace(0,1,5)
rng = np.random.default_rng(42)
rng.normal(size=(3,3))
```

---

## SECTION 2 — Array Operations

### 5. Indexing & Slicing

### 5. Indexing & Slicing

Get values with indexes: `arr[i]` or `arr[i,j]` for 2D.
Use `arr[-1]` for the last item. Slice with `arr[1:4]` or `arr[:, :2]`.

Note: slices often return views (not copies).

Use indexing to pick batches or time windows.

---

### 6. Reshaping Arrays

### 6. Reshaping Arrays

- `reshape(new_shape)` changes the view of data without copying when possible.
- `flatten()` gives a copy of data as 1D.
- `ravel()` is like flatten but tries to return a view.
- `arr.T` or `transpose()` swaps axes.

Shapes must match what functions expect (e.g., `[batch, features]`).

---

### 7. Array Mathematics

### 7. Array Mathematics

Use `+ - * / **` for elementwise math.
Use `np.dot(A, B)` or `A @ B` for matrix multiply.

Broadcasting makes shapes match automatically when rules allow it. It saves writing loops.

Always prefer vectorized ops over Python loops for big speed gains.

---

## SECTION 3 — Statistical Operations

### 8. Statistical Functions

### 8. Statistical Functions

Common stats: `np.mean`, `np.median`, `np.std`, `np.var`, `np.sum`, `np.min`, `np.max`.
Use `np.percentile` or `np.quantile` for percentiles.

These help compute normalization and summaries for datasets.

---

### 9. Aggregation Functions

### 9. Aggregation Functions

`axis=0` works down rows (gives column results). `axis=1` works across columns (gives row results).

Example:
```python
arr.sum(axis=0)
arr.mean(axis=1)
```

Check shapes when using axis to avoid mistakes.

---

## SECTION 4 — Matrix Operations

### 10. Matrix Fundamentals

### 10. Matrix Fundamentals

Matrix multiply: `np.dot(A, B)` or `A @ B`.
Elementwise multiply is `A * B`.

Example:
```python
A = np.eye(3)
B = np.ones((3,3))
C = A @ B
```

---

### 11. Linear Algebra with NumPy

### 11. Linear Algebra with NumPy

Find inverse, determinant, eigenvalues via `np.linalg` (e.g., `np.linalg.inv`, `np.linalg.eig`).
Prefer `np.linalg.solve(A, b)` over `inv(A) @ b` for stability.

Linear algebra is the math behind many ML methods.

---

## SECTION 5 — Broadcasting

### 12. Broadcasting

### 12. Broadcasting

Broadcasting lets arrays with different shapes work together if they follow simple rules (align trailing dims, or dim=1).

Example:
```python
X = np.ones((3,4))
v = np.array([1,2,3,4])  # shape (4,)
X + v  # v is used for each row
```

Broadcasting keeps code short and fast. Check shapes to avoid surprises.

---

## SECTION 6 — Advanced Array Manipulation

### 13. Stacking Arrays

### 13. Stacking Arrays

Combine arrays with `np.hstack`, `np.vstack`, `np.concatenate`, or `np.stack`.

Example:
```python
np.vstack([a, b])
np.concatenate([a, b], axis=0)
```

---

### 14. Filtering Arrays

### 14. Filtering Arrays

Use boolean masks to pick values:
```python
mask = arr > 0
arr[mask]
np.where(arr > 0, arr, 0)
```

Use `&` and `|` with parentheses for multiple conditions.

Use masking to clean or filter data.

---

### 15. Sorting & Searching

### 15. Sorting & Searching

Useful functions: `np.sort`, `np.argsort`, `np.unique`, `np.searchsorted`, `np.argmax`, `np.argmin`.

Use these for top-k selection, thresholds, and deduplication.

---

## SECTION 7 — Random Numbers

### 16. Random Module

### 16. Random Module

Use the new Generator API:
```python
rng = np.random.default_rng(123)
rng.integers(0, 10, size=(3,))
rng.random((2,2))
```

Set a seed so experiments can be repeated. Randomness is used for shuffling and initialization.

---

## SECTION 8 — Performance

### 17. Why NumPy is Fast

### 17. Why NumPy is Fast

NumPy runs math in C, not Python. This makes it much faster. It also uses memory efficiently and links to fast math libraries.

Measure speed with `timeit`.

### 18. Memory Optimization

### 18. Memory Optimization

Slicing usually returns a view (same data, different view). Use `.copy()` to make a real copy.

Avoid extra copies and keep data types (`dtype`) consistent to save memory.

---

## SECTION 9 — NumPy for Machine Learning

### 19. Feature Matrices

### 19. Feature Matrices

Data is usually `X` with shape `(n_samples, n_features)` and labels `y` with shape `(n_samples,)`.

### 20. Math Basics

Vectors, matrices, and tensors are basic data structures you will use for ML.

### 21. Data Preprocessing

Handle missing values with `np.nan` and `np.isnan()`.
Normalize: `(x - mean) / std`. Scale with min-max.

Example:
```python
mean = X.mean(axis=0)
std = X.std(axis=0)
X_norm = (X - mean) / (std + 1e-8)
```

---

## SECTION 10 — Best Practices

### 22. Clean NumPy Coding


### 22. Clean NumPy Coding

Use clear names like `X`, `y`, `weights`. Prefer vectorized operations over loops. Pick `float32` or `float64` according to memory and precision needs.

### 23. Common Beginner Mistakes


### 23. Common Beginner Mistakes

Check `shape` often. Watch broadcasting rules. Use `.copy()` when you need a separate array.

---

## SECTION 11 — Mini Projects

## SECTION 11 — Mini Projects

Simple projects:
- Student marks analyzer
- Expense stats calculator

Intermediate:
- Dataset summary tool
- Image pixel analyzer

AI projects:
- Feature matrix builder
- Linear regression from scratch (closed form and gradient descent)

Linear regression example (closed form):
```python
X = np.column_stack([np.ones(n), X_raw])  # add bias column
w = np.linalg.pinv(X.T @ X) @ X.T @ y
```

---

## SECTION 12 — NumPy in Real AI Systems

NumPy underpins data pipelines, model prototypes, numerical experiments, and research code. It integrates with libraries like Pandas, scikit-learn, PyTorch, TensorFlow, and OpenCV.

---


## SECTION 13 — Revision Cheatsheet

Key functions:
```python
np.array, np.zeros, np.ones, np.arange, np.linspace
np.reshape, np.mean, np.sum, np.max, np.min
np.dot, np.where, np.random.default_rng
```

Key concepts: arrays, shapes, broadcasting, vectorization, views vs copies, matrix multiply.

---

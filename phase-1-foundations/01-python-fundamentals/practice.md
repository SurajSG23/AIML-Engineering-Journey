# Python Fundamentals Practice

## Overview
This document is a concise, practical set of notes for Python fundamentals focused on AI engineering. Each section gives key concepts, short examples, common pitfalls, and AI/ML relevance.

---

## 1. Introduction to Python

- What is Python: A high-level, interpreted, general-purpose language with readable syntax and a large standard library.
- Why Python for AI/ML: Rich ecosystem (NumPy, Pandas, scikit-learn, PyTorch, TensorFlow), fast prototyping, strong community, and many learning resources.
- Real-world AI applications: Recommendation systems, computer vision, NLP, time-series forecasting, anomaly detection, and production APIs.
- Python ecosystem overview: stdlib, PyPI packages, scientific stack (NumPy, SciPy), data (Pandas), ML (scikit-learn, PyTorch), deployment (FastAPI, Docker).

---

## SECTION 1 — Python Basics

### 2. Variables & Data Types

Variables store values. Python is dynamically typed — variables bind to objects.

Variables:
- Assignment: `x = 10`
- Naming rules: letters, digits, underscores; can't start with digit; avoid reserved words.
- Dynamic typing: `x = 3` then `x = "text"` is allowed.

Data types:
- `int`, `float`, `str`, `bool`, `NoneType`

Type checking and conversion:
```python
type(3)        # int
type(3.0)      # float
type('a')      # str

int('3')       # 3
float('3.1')   # 3.1
str(10)        # '10'
bool(0)        # False
```

Common mistakes:
- Confusing `=` and `==`.
- Mutable vs immutable objects (e.g., lists vs tuples).

Best practices:
- Use descriptive names, follow PEP8, avoid reusing variables for different types.

AI/ML relevance:
- Choosing numeric types for tensors/arrays matters for memory and speed.

---

### 3. Input & Output

`print()` – simple output. `input()` – reads strings from stdin.

String formatting:
- f-strings (recommended): `f"{name} is {age}"`
- `format()` method: `"{} {}".format(a,b)`

Debug printing:
- Use `print()` for quick checks, or `logging` for production-level debug info.

Real-world use cases:
- Logging training progress, printing metrics, saving outputs to files.

---

### 4. Operators

Categories:
- Arithmetic: `+ - * / // % **`
- Comparison: `== != > < >= <=`
- Logical: `and or not`
- Assignment: `=, +=, -=, *=, /=`
- Membership: `in, not in`
- Identity: `is, is not`

Operator precedence follows standard math rules; use parentheses to be explicit.

AI/ML relevance:
- Filter datasets, compute loss, aggregate results.

---

## SECTION 2 — Control Flow

### 5. Conditional Statements

Syntax examples:
```python
if x > 0:
	print('positive')
elif x == 0:
	print('zero')
else:
	print('negative')
```

Real-world examples: access control, preprocessing branches, early exits in training loops.

Common mistakes: wrong indentation, unreachable `elif`, using `is` for equality checks with literals.

---

### 6. Loops

For loops:
```python
for i in range(5):
	print(i)

for item in collection:
	process(item)
```

While loops and controls:
```python
while cond:
	if some_condition:
		break
	continue
```

Use `pass` as a placeholder. Beware infinite loops.

AI/ML relevance:
- Training epochs, batch iteration, data augmentation loops.

---

## SECTION 3 — Functions

### 7. Functions

Why functions matter: modularity, reuse, testability.

Define and call:
```python
def add(a, b=0):
	return a + b

add(2, 3)
```

Parameters: positional, keyword, default, `*args`, `**kwargs`.

Lambda functions:
```python
square = lambda x: x*x
```

Scope: local vs global — prefer returning values, avoid globals.

Best practices: small, single-responsibility functions; document inputs/outputs.

AI/ML relevance:
- Build preprocessing pipelines and model wrappers as functions.

---

## SECTION 4 — Data Structures

### 8. Lists

Create: `lst = [1,2,3]` Indexing and slicing: `lst[0]`, `lst[-1]`, `lst[1:3]`.
Common methods: `append`, `remove`, `pop`, `sort`, `extend`.
List comprehensions for concise transforms:
```python
[x*2 for x in lst if x>1]
```

AI/ML relevance: datasets, minibatches.

---

### 9. Tuples

Immutable sequences. Good for fixed collections and keys in dictionaries.
Packing & unpacking:
```python
t = (1,2)
a,b = t
```

---

### 10. Sets

Unique unordered collection. Operations: union, intersection, difference.
Use for fast membership tests and deduplication.

---

### 11. Dictionaries

Key-value mapping. Create: `d = {'a':1}`. Access: `d['a']` or `d.get('a', default)`.
Methods: `keys()`, `values()`, `items()`, `update()`.
Useful for JSON-like data, configs, model params.

---

## SECTION 5 — Strings

Basics: indexing, slicing, common methods:
- `lower()`, `upper()`, `split()`, `replace()`, `strip()`

Escape characters: `\\n`, `\\t`, use raw strings `r"..."` for regex or windows paths.

AI/ML relevance: NLP preprocessing, tokenization, prompt assembly.

---

## SECTION 6 — File Handling

Open/read/write files:
```python
with open('data.txt', 'r', encoding='utf-8') as f:
	text = f.read()

with open('out.csv', 'w', encoding='utf-8') as f:
	f.write('col1,col2\\n')
```

Modes: `r`, `w`, `a`, `rb` (binary).

CSV basics: prefer `csv` or `pandas.read_csv` for tabular data.

AI/ML relevance: loading datasets, saving models, logging.

---

## SECTION 7 — Error Handling

Exception handling:
```python
try:
	risky()
except ValueError as e:
	handle(e)
finally:
	cleanup()
```

Raise errors with `raise ValueError('msg')`.

Common exceptions: `ValueError`, `TypeError`, `IndexError`, `KeyError`.

Debugging mindset: reproduce, isolate, fix minimal failing case.

---

## SECTION 8 — Object-Oriented Programming

### 15. OOP Basics

Classes and objects:
```python
class Model:
	def __init__(self, name):
		self.name = name
	def predict(self, x):
		return x
```

Encapsulation: keep internal state private. Inheritance and polymorphism for shared behavior.

Why OOP matters in AI: model classes, dataset wrappers, training loops.

---

## SECTION 9 — Advanced Python Concepts

### 16. Modules & Packages

Importing: `import math`, `from module import fn`.
Create `__init__.py` for packages. Manage dependencies with `pip`, `requirements.txt`, or `venv`/`virtualenv`.

Quick virtualenv setup:
```powershell
python -m venv .venv
.\.venv\\Scripts\\Activate.ps1
pip install -r requirements.txt
```

---

### 17. Iterators & Generators

Iterables implement `__iter__()`. Generators use `yield` for lazy sequences.
Example:
```python
def gen(n):
	for i in range(n):
		yield i*i
```

Memory efficient for large datasets, streaming, data loaders.

---

### 18. Decorators

Decorators wrap functions to add behavior:
```python
def timer(fn):
	def wrapper(*a, **k):
		import time
		t0 = time.time()
		r = fn(*a, **k)
		print(time.time()-t0)
		return r
	return wrapper
```

Use for logging, caching, access control.

---

### 19. Context Managers

Implement resource management with `with` and `__enter__/__exit__`.

---

## SECTION 10 — Python for AI Engineering

### 20. Clean Code Principles

- Naming conventions: `snake_case` for functions/variables, `CamelCase` for classes.
- Readability: short functions, clear variable names, docstrings.
- DRY: avoid repeating code, abstract common logic.

Beginner mistakes: premature optimization, neglecting tests, poor error handling.

---

### 21. Debugging Skills

- Read tracebacks top-to-bottom.
- Use `print()` and `logging` to inspect values.
- Use debuggers (`pdb`, VS Code debugger) for step-through.

---

### 22. Time Complexity Basics

Big-O quick guide: `O(1)`, `O(n)`, `O(log n)`, `O(n^2)`.
Performance matters in AI when processing large datasets and model inference.

---

## SECTION 11 — Mini Projects & Exercises

Beginner exercises:
- Build a calculator CLI.
- Implement a CSV analyzer that prints column stats.
- Quiz app: store questions in JSON and grade answers.

Intermediate:
- Student management system using dictionaries/lists.
- Simple chatbot that responds by pattern matching.

AI-oriented beginner projects:
- Text cleaner (lowercase, strip punctuation, token counts).
- Dataset analyzer: load CSV and show missing values, distributions.

Optional quick exercise code:
```python
# word frequency
from collections import Counter
def word_freq(text):
	import re
	tokens = re.findall(r"\w+", text.lower())
	return Counter(tokens)
```

---

## SECTION 12 — Python in Real AI Systems

Where Python is used: model training, inference scripts, APIs (FastAPI), data pipelines (Airflow), MLOps tools, and wrappers for research code.

---

## SECTION 13 — Important Best Practices

DO:
- write readable code
- use functions
- handle errors
- write tests and docstrings

DON'T:
- hardcode secrets
- use meaningless names
- ignore exceptions

---

## SECTION 14 — Revision Cheatsheet

Most important concepts: variables, loops, functions, lists, dictionaries, file handling, OOP.

Most used built-ins:
```python
len(), type(), range(), print(), input(), sum(), max(), min()
```

---

## SECTION 15 — AI Engineering Connection

Python connects to the AI stack via `NumPy`, `Pandas`, `scikit-learn`, `PyTorch`, `TensorFlow`, `FastAPI`, and containerization with Docker. Learn how data flows from raw files → preprocessing → model → deployment.

---
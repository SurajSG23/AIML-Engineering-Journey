# Python Fundamentals Practice

## Overview
Simple, practical Python notes for AI engineering. Short explanations, small examples, and clear tips to help you learn and apply Python quickly.

---

## 1. Introduction to Python

- What is Python: A simple, popular programming language used for many tasks.
- Why Python for AI/ML: Many ready-made libraries (NumPy, Pandas, PyTorch) and fast to test ideas.
- Real-world AI uses: image recognition, language tools, recommendations, and model servers.
- Ecosystem: built-in modules, packages from PyPI, and many tools for data and ML.

---

## SECTION 1 — Python Basics

### 2. Variables & Data Types

Variables store data. Python lets you change a variable to hold any type.

Variables:
- Assign: `x = 10`
- Names: use letters, numbers, and `_`. Don't start with a number.
- Dynamic typing: `x = 3` then `x = "text"` is allowed.

Common types: `int`, `float`, `str`, `bool`, `NoneType`.

Check or convert types:
```python
type(3)        # int
int('3')       # 3
float('3.1')   # 3.1
str(10)        # '10'
```

Watch out:
- `=` sets a value, `==` compares values.
- Lists change in place (mutable); tuples do not (immutable).

Good habits:
- Use clear names and follow style guides.

AI tip:
- Pick the right numeric type (`float32` vs `float64`) to save memory and speed up training.

---

### 3. Input & Output

Output and input are simple.
- `print()` shows values on screen.
- `input()` reads text from the user.

Format strings:
- f-strings (easy): `f"{name} is {age}"`
- `format()` works too: `"{} {}".format(a,b)`

For quick checks use `print()`. For real code use `logging`.

Use cases: show training steps, print metrics, save small logs.

---

### 4. Operators

Operators perform math and checks.
- Arithmetic: `+ - * / // % **`
- Compare: `== != > <`
- Logic: `and, or, not`
- Membership: `in, not in`
- Identity: `is, is not`

Use parentheses to make expressions clear.

AI use: conditions, filters, math for loss and metrics.

---

## SECTION 2 — Control Flow

### 5. Conditional Statements

Use `if`, `elif`, and `else` to pick code paths.
```python
if x > 0:
    print('positive')
elif x == 0:
    print('zero')
else:
    print('negative')
```

Common errors: wrong indent, using `is` instead of `==` for value checks.

---

### 6. Loops

`for` goes over items:
```python
for i in range(5):
	print(i)
```

`while` repeats while a condition is true. Use `break` to stop early.

Use `pass` as a placeholder. Avoid infinite loops.

AI use: training epochs and dataset loops.

---

## SECTION 3 — Functions

### 7. Functions

Functions group code to reuse it.
```python
def add(a, b=0):
	return a + b

add(2, 3)
```

You can use defaults, positional and keyword arguments, `*args`, and `**kwargs`.

Lambdas are short functions: `square = lambda x: x*x`.

Keep functions short and focused. Return values instead of using globals.

Use functions to build preprocess steps and model helpers.

---

## SECTION 4 — Data Structures

### 8. Lists

Create: `lst = [1,2,3]`.
Index: `lst[0]`, last: `lst[-1]`, slice: `lst[1:3]`.
Common methods: `append`, `remove`, `pop`, `sort`.
Comprehension example: `[x*2 for x in lst if x>1]`.

Use lists for simple collections and small datasets.

---

### 9. Tuples

Tuples are like lists but cannot change (immutable).
Use them for fixed groups of values.
```python
t = (1,2)
a,b = t
```

---

### 10. Sets

Sets hold unique items and are unordered.
Useful for removing duplicates and fast membership checks.

---

### 11. Dictionaries

Dictionaries store data as key:value pairs.
Create: `d = {'a':1}`. Access: `d['a']` or `d.get('a', 0)`.
Useful methods: `keys()`, `values()`, `items()`, `update()`.

Use dictionaries for configs, JSON, and mapping values.

---

## SECTION 5 — Strings

Strings hold text. Common methods: `lower()`, `upper()`, `split()`, `replace()`, `strip()`.
Use `\n` for newlines and `r"..."` for raw strings (useful with regex or Windows paths).

Strings are important for NLP and building prompts.

---

## SECTION 6 — File Handling

Read and write files with `open()` and `with`:
```python
with open('data.txt', 'r', encoding='utf-8') as f:
	text = f.read()

with open('out.csv', 'w', encoding='utf-8') as f:
	f.write('col1,col2\n')
```

Common modes: `r` (read), `w` (write), `a` (append), `rb` (read binary).
Use `csv` or `pandas.read_csv` for tables.

Files are used to load data and save results.

---

## SECTION 7 — Error Handling

Use `try/except` to catch errors and keep the program running:
```python
try:
	risky()
except ValueError as e:
	handle(e)
finally:
	cleanup()
```

Raise errors with `raise ValueError('msg')`.
Common errors: `ValueError`, `TypeError`, `IndexError`, `KeyError`.

When debugging: reproduce the error, narrow it down, then fix it.

---

## SECTION 8 — Object-Oriented Programming

### 15. OOP Basics

Classes let you group data and functions together:
```python
class Model:
	def __init__(self, name):
		self.name = name
	def predict(self, x):
		return x
```

Use OOP for models, data loaders, and reusable components.

---

## SECTION 9 — Advanced Python Concepts

### 16. Modules & Packages

Import modules with `import math` or `from module import fn`.
Create packages using `__init__.py`. Use `pip` and `requirements.txt` to manage packages.

Quick virtual environment setup:
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

---

### 17. Iterators & Generators

Iterators let you loop over data. Generators use `yield` to produce items one by one.
They save memory when working with large data.
```python
def gen(n):
	for i in range(n):
		yield i*i
```

---

### 18. Decorators

Decorators let you add code before or after a function runs.
They are useful for timing, logging, or caching.
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

---

### 19. Context Managers

Use `with` to manage resources like files or network connections. It ensures cleanup.

---

## SECTION 10 — Python for AI Engineering

### 20. Clean Code Principles

Use `snake_case` for functions and variables, `CamelCase` for classes. Keep functions short and clear. Don't repeat code.

Avoid premature optimization. Write tests and handle errors.

---

### 21. Debugging Skills

Read the error message first. Use `print()` or `logging` to see values. Use a debugger to step through code.

---

### 22. Time Complexity Basics

Big-O shows how runtime grows with data size: `O(1)`, `O(n)`, `O(log n)`, `O(n^2)`. Performance matters for large datasets.

---

## SECTION 11 — Mini Projects & Exercises

Beginner ideas:
- Calculator CLI
- CSV analyzer (basic stats)
- Quiz app using JSON

Intermediate:
- Student management system
- Simple rule-based chatbot

AI-focused:
- Text cleaner (lowercase, remove punctuation)
- Dataset analyzer (missing values, simple plots)

Quick example (word counts):
```python
from collections import Counter
import re

def word_freq(text):
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
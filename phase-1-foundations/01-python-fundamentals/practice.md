# Python Fundamentals

> Python is one of the most popular programming languages in the world.
>
> It is widely used in:
>
> * Artificial Intelligence
> * Machine Learning
> * Data Science
> * Web Development
> * Automation
> * Cybersecurity
>
> In this guide, we will learn Python from scratch.

---

# Why Learn Python?

Python is:

* Easy to read
* Easy to write
* Beginner friendly
* Powerful
* Widely used in industry

Example:

```python
print("Hello World")
```

Output:

```text
Hello World
```

Simple and readable.

---

# Running Python

Create a file:

```text
main.py
```

Write:

```python
print("Hello World")
```

Run:

```bash
python main.py
```

---

# Variables

Variables store data.

Example:

```python
name = "Suraj"
age = 21
```

Think of a variable as a labeled box.

```text
name → "Suraj"

age → 21
```

---

# Rules for Variable Names

Valid:

```python
student_name = "Suraj"
age = 21
_marks = 90
```

Invalid:

```python
2name = "Suraj"
student-name = "Suraj"
```

---

# Data Types

Everything in Python has a type.

---

## Integer (int)

Whole numbers.

```python
age = 21
```

Examples:

```python
10
20
100
-5
```

---

## Float (float)

Decimal numbers.

```python
height = 175.5
```

Examples:

```python
3.14
2.5
100.99
```

---

## String (str)

Text data.

```python
name = "Suraj"
```

Examples:

```python
"Hello"
"Python"
"Germany"
```

---

## Boolean (bool)

Represents True or False.

```python
is_student = True
```

Examples:

```python
True
False
```

---

# Checking Data Type

Use:

```python
type(value)
```

Example:

```python
print(type(21))
```

Output:

```text
<class 'int'>
```

---

# Taking User Input

```python
name = input("Enter your name: ")

print(name)
```

Example:

```text
Enter your name: Suraj

Suraj
```

---

# Type Conversion

Input always returns a string.

Convert when needed.

---

String to Integer

```python
age = int(input("Enter age: "))
```

---

String to Float

```python
salary = float(input("Enter salary: "))
```

---

Integer to String

```python
age = 21

print(str(age))
```

---

# Output

Display information using:

```python
print()
```

Example:

```python
print("Hello")
```

---

Multiple Values

```python
name = "Suraj"
age = 21

print(name, age)
```

Output:

```text
Suraj 21
```

---

# Arithmetic Operators

```python
a = 10
b = 3
```

Addition:

```python
a + b
```

Output:

```text
13
```

---

Subtraction:

```python
a - b
```

---

Multiplication:

```python
a * b
```

---

Division:

```python
a / b
```

Output:

```text
3.3333...
```

---

Floor Division

```python
a // b
```

Output:

```text
3
```

---

Modulus

Returns remainder.

```python
a % b
```

Output:

```text
1
```

---

Power

```python
a ** b
```

Output:

```text
1000
```

---

# Comparison Operators

Used to compare values.

```python
10 == 10
```

Output:

```text
True
```

---

```python
10 != 5
```

Output:

```text
True
```

---

```python
10 > 5
```

Output:

```text
True
```

---

```python
10 < 5
```

Output:

```text
False
```

---

```python
10 >= 10
```

Output:

```text
True
```

---

```python
10 <= 8
```

Output:

```text
False
```

---

# Logical Operators

Combine conditions.

---

## and

Both conditions must be true.

```python
age = 21

age > 18 and age < 30
```

Output:

```text
True
```

---

## or

At least one condition must be true.

```python
10 > 20 or 5 < 10
```

Output:

```text
True
```

---

## not

Reverses result.

```python
not True
```

Output:

```text
False
```

---

# Conditional Statements

Programs often make decisions.

---

## if

```python
age = 20

if age >= 18:
    print("Adult")
```

---

## if-else

```python
age = 16

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

---

## if-elif-else

```python
marks = 85

if marks >= 90:
    print("A")

elif marks >= 75:
    print("B")

else:
    print("C")
```

---

# Loops

Loops repeat code.

---

# for Loop

```python
for i in range(5):
    print(i)
```

Output:

```text
0
1
2
3
4
```

---

# while Loop

```python
count = 0

while count < 5:
    print(count)
    count += 1
```

---

# break

Stops loop.

```python
for i in range(10):

    if i == 5:
        break

    print(i)
```

Output:

```text
0
1
2
3
4
```

---

# continue

Skips current iteration.

```python
for i in range(5):

    if i == 2:
        continue

    print(i)
```

Output:

```text
0
1
3
4
```

---

# Strings

Strings store text.

```python
name = "Suraj"
```

---

Length

```python
len(name)
```

Output:

```text
5
```

---

Uppercase

```python
name.upper()
```

Output:

```text
SURAJ
```

---

Lowercase

```python
name.lower()
```

---

Replace

```python
name.replace("Suraj","Rahul")
```

---

Split

```python
"apple,banana".split(",")
```

Output:

```python
['apple', 'banana']
```

---

# Lists

Lists store multiple values.

```python
fruits = ["apple","banana","mango"]
```

---

Access Elements

```python
fruits[0]
```

Output:

```text
apple
```

---

Last Element

```python
fruits[-1]
```

---

Add Item

```python
fruits.append("orange")
```

---

Remove Item

```python
fruits.remove("banana")
```

---

Length

```python
len(fruits)
```

---

Loop Through List

```python
for fruit in fruits:
    print(fruit)
```

---

# Tuples

Tuples are like lists but cannot be changed.

```python
numbers = (1,2,3)
```

Why use tuples?

* Safer
* Faster
* Immutable

---

# Sets

Store unique values.

```python
nums = {1,2,3,3,3}
```

Output:

```text
{1,2,3}
```

Duplicates are removed.

---

Add Element

```python
nums.add(4)
```

---

# Dictionaries

Store data as key-value pairs.

```python
student = {
    "name":"Suraj",
    "age":21
}
```

---

Access Value

```python
student["name"]
```

Output:

```text
Suraj
```

---

Add Value

```python
student["city"] = "Mysuru"
```

---

Loop Through Dictionary

```python
for key, value in student.items():
    print(key, value)
```

---

# Functions

Functions help reuse code.

---

Creating Function

```python
def greet():

    print("Hello")
```

Call Function:

```python
greet()
```

---

Function with Parameters

```python
def greet(name):

    print("Hello", name)
```

Usage:

```python
greet("Suraj")
```

---

Return Values

```python
def add(a,b):

    return a+b
```

Usage:

```python
result = add(10,20)

print(result)
```

Output:

```text
30
```

---

# Exception Handling

Programs can crash.

Exceptions help handle errors.

---

Example

```python
try:

    num = int(input())

except:

    print("Invalid Input")
```

---

Better Version

```python
try:

    num = int(input())

except ValueError:

    print("Enter a valid number")
```

---

# Modules

Modules contain reusable code.

---

Import Math Module

```python
import math
```

Square Root:

```python
math.sqrt(25)
```

Output:

```text
5
```

---

Random Number

```python
import random

random.randint(1,10)
```

---

# File Handling

Write File:

```python
file = open("data.txt","w")

file.write("Hello")

file.close()
```

---

Read File:

```python
file = open("data.txt","r")

print(file.read())

file.close()
```

---

Recommended Method

```python
with open("data.txt","r") as file:

    print(file.read())
```

Automatically closes file.

---

# List Comprehension

A Pythonic way to create lists.

Traditional:

```python
numbers = []

for i in range(5):
    numbers.append(i)
```

---

Better:

```python
numbers = [i for i in range(5)]
```

Output:

```python
[0,1,2,3,4]
```

---

# Useful Built-in Functions

Length:

```python
len()
```

---

Maximum:

```python
max()
```

---

Minimum:

```python
min()
```

---

Sum:

```python
sum()
```

---

Sorted:

```python
sorted()
```

---

# Python for AI and ML

Before learning:

* NumPy
* Pandas
* Scikit-Learn
* PyTorch
* TensorFlow

You must be comfortable with:

* Variables
* Functions
* Loops
* Lists
* Dictionaries
* File Handling

These appear everywhere in AI projects.

---

# Common Beginner Mistakes

## Forgetting Indentation

Wrong:

```python
if True:
print("Hello")
```

Correct:

```python
if True:
    print("Hello")
```

---

## Confusing = and ==

Assignment:

```python
age = 21
```

Comparison:

```python
age == 21
```

---

## Modifying Tuple Values

```python
numbers = (1,2,3)

numbers[0] = 10
```

Error.

Tuples are immutable.

---

## Infinite While Loops

Wrong:

```python
while True:
    print("Hello")
```

Be careful.

---

# Mini Project

Student Grade Checker

```python
name = input("Enter Name: ")

marks = int(input("Enter Marks: "))

if marks >= 90:
    grade = "A"

elif marks >= 75:
    grade = "B"

elif marks >= 60:
    grade = "C"

else:
    grade = "D"

print(name)
print("Grade:", grade)
```

---

# Final Thoughts

Python is the foundation of your AI/ML journey.

Recommended order:

```text
Python Fundamentals
        ↓
NumPy
        ↓
Pandas
        ↓
Matplotlib
        ↓
Statistics
        ↓
Machine Learning
        ↓
Deep Learning
```

Master Python first. Every other library becomes much easier once the fundamentals are strong.

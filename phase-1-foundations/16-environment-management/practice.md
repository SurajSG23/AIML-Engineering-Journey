# Environment Management

> One of the biggest problems beginners face is:
>
> **"It was working yesterday... why is it broken today?"**
>
> Or:
>
> **"This project works, but another project stopped working after installing a new package."**
>
> The reason is usually poor environment management.
>
> Environment management helps you isolate projects, manage dependencies, and ensure your code runs consistently on any machine.

---

# Why Do We Need Environment Management?

Imagine you're working on two Python projects.

### Project A

Uses:

* Python 3.10
* NumPy 1.24
* TensorFlow 2.12

---

### Project B

Uses:

* Python 3.12
* NumPy 2.0
* PyTorch 2.8

If both projects share the same Python installation, installing packages for one project may break the other.

This is called a:

```text
Dependency Conflict
```

Environment management solves this problem.

---

# What is an Environment?

An environment is an isolated workspace containing:

* A Python interpreter
* Installed packages
* Project dependencies
* Environment variables

Each project can have its own environment.

Think of it like having separate rooms for different activities.

```text
Room 1
↓

AI Project
```

```text
Room 2
↓

Web Development Project
```

Changes made in one room don't affect the other.

---

# What is a Virtual Environment?

A Virtual Environment (often called **venv**) is a private Python environment created for a single project.

Instead of installing packages globally:

```text
Computer

↓

One Python

↓

Everything Installed Together
```

you get:

```text
Project A

↓

Own Python Environment
```

```text
Project B

↓

Own Python Environment
```

Both projects remain independent.

---

# Why Virtual Environments Matter

Suppose Project A requires:

```text
NumPy 1.24
```

Project B requires:

```text
NumPy 2.0
```

Without virtual environments:

```text
Conflict
```

With virtual environments:

```text
Project A

↓

NumPy 1.24
```

```text
Project B

↓

NumPy 2.0
```

No conflict.

---

# Creating a Virtual Environment

Python provides a built-in module called:

```text
venv
```

Create a virtual environment:

```bash
python -m venv venv
```

This creates a folder named:

```text
venv/
```

which contains a separate Python installation for the project.

---

# Activating the Environment

### Windows

```bash
venv\Scripts\activate
```

---

### macOS/Linux

```bash
source venv/bin/activate
```

After activation, your terminal may look like:

```text
(venv) C:\Projects\AI_Project>
```

The `(venv)` indicates that the virtual environment is active.

---

# Deactivating the Environment

When you're done:

```bash
deactivate
```

This returns you to your normal system Python.

---

# Installing Packages

After activating the environment:

```bash
pip install numpy pandas scikit-learn
```

These packages are installed **only inside this environment**.

Other projects are unaffected.

---

# Checking Installed Packages

View installed packages:

```bash
pip list
```

Example:

```text
numpy

pandas

scikit-learn

fastapi
```

---

# Saving Dependencies

Suppose your project uses:

* NumPy
* Pandas
* FastAPI
* Scikit-learn

Instead of asking others to install everything manually, generate a requirements file.

```bash
pip freeze > requirements.txt
```

Example:

```text
fastapi==0.116.1
numpy==2.3.1
pandas==2.3.1
scikit-learn==1.7.1
```

This file records the exact package versions.

---

# Installing from requirements.txt

Another developer can recreate the environment using:

```bash
pip install -r requirements.txt
```

All required packages are installed automatically.

---

# Why Version Numbers Matter

Imagine you built your project using:

```text
NumPy 1.26
```

A newer version:

```text
NumPy 2.0
```

changes some behavior.

Your code might stop working.

By storing package versions, everyone uses the same environment.

---

# What is pip?

`pip` is Python's package manager.

It is used to:

* Install packages
* Upgrade packages
* Remove packages

Example:

Install:

```bash
pip install numpy
```

Upgrade:

```bash
pip install --upgrade numpy
```

Uninstall:

```bash
pip uninstall numpy
```

---

# Global Installation vs Virtual Environment

### Global Installation

```text
Computer

↓

Python

↓

NumPy

Pandas

TensorFlow

FastAPI

Everything Together
```

Problem:

Projects can interfere with each other.

---

### Virtual Environment

```text
Project A

↓

Own Packages
```

```text
Project B

↓

Own Packages
```

No conflicts.

---

# Project Structure

A typical Python project:

```text
house_price_prediction/

│── venv/
│── app.py
│── requirements.txt
│── README.md
│── data/
│── models/
```

Notice:

```text
venv/
```

is inside the project but is **not uploaded to GitHub**.

---

# Why We Don't Upload venv

A virtual environment can be recreated.

Instead of uploading thousands of files:

Upload only:

```text
requirements.txt
```

Others can recreate the environment.

---

# .gitignore

Create:

```text
.gitignore
```

Example:

```text
venv/

__pycache__/

*.pyc

.env
```

Git ignores these files.

---

# Environment Variables

Projects often require:

* API Keys
* Database URLs
* Passwords
* Secret Tokens

Never write:

```python
API_KEY = "123456789"
```

Instead:

```python
import os

api_key = os.getenv("API_KEY")
```

This keeps sensitive information out of your code.

---

# The .env File

A `.env` file stores environment variables.

Example:

```text
API_KEY=abc123

DATABASE_URL=mysql://localhost

MODEL_PATH=models/model.pkl
```

Python libraries like `python-dotenv` can load these values automatically.

---

# Loading Environment Variables

Install:

```bash
pip install python-dotenv
```

Example:

```python
from dotenv import load_dotenv
import os

load_dotenv()

api_key = os.getenv("API_KEY")
```

Now your code stays clean and secure.

---

# Conda

Besides `venv`, another popular environment manager is:

```text
Conda
```

Conda is commonly used in:

* Data Science
* Machine Learning
* Scientific Computing

Unlike `venv`, Conda can manage:

* Python versions
* Python packages
* Non-Python libraries

---

# Creating a Conda Environment

```bash
conda create -n ai_env python=3.12
```

Activate:

```bash
conda activate ai_env
```

Deactivate:

```bash
conda deactivate
```

---

# venv vs Conda

| venv                    | Conda                        |
| ----------------------- | ---------------------------- |
| Built into Python       | Separate tool                |
| Lightweight             | More features                |
| Python packages only    | Python + non-Python packages |
| Great for most projects | Popular in Data Science      |

For beginners, **venv is usually enough**.

---

# Docker vs Virtual Environment

Many beginners confuse these.

### Virtual Environment

Isolates:

```text
Python

Packages
```

---

### Docker

Packages:

* Application
* Python
* Dependencies
* Operating system components

Docker solves a bigger problem than virtual environments.

---

# Typical AI Project Workflow

```text
Create Project
      ↓
Create Virtual Environment
      ↓
Activate Environment
      ↓
Install Packages
      ↓
Develop Project
      ↓
Freeze Requirements
      ↓
Push to GitHub
      ↓
Deploy (Optional: Docker)
```

---

# Common Commands

Create environment:

```bash
python -m venv venv
```

Activate (Windows):

```bash
venv\Scripts\activate
```

Activate (Linux/macOS):

```bash
source venv/bin/activate
```

Deactivate:

```bash
deactivate
```

Install package:

```bash
pip install numpy
```

List packages:

```bash
pip list
```

Freeze requirements:

```bash
pip freeze > requirements.txt
```

Install requirements:

```bash
pip install -r requirements.txt
```

---

# Common Beginner Mistakes

---

## Installing Packages Globally

Always create a virtual environment before installing packages.

---

## Forgetting to Activate the Environment

If you forget to activate it, packages may install into the global Python installation.

---

## Uploading the venv Folder to GitHub

Never upload:

```text
venv/
```

Instead upload:

```text
requirements.txt
```

---

## Hardcoding Secrets

Never write:

```python
API_KEY = "secret"
```

Use environment variables instead.

---

## Forgetting requirements.txt

Without it, others won't know which package versions your project needs.

---

# Real-World Example

Suppose you're building a FastAPI application using:

* FastAPI
* NumPy
* Pandas
* Scikit-learn
* Joblib

Workflow:

```text
Create Virtual Environment
        ↓
Activate Environment
        ↓
Install Dependencies
        ↓
Build API
        ↓
Freeze requirements.txt
        ↓
Push to GitHub
        ↓
Deploy with Docker
```

This ensures anyone can recreate your project exactly.

---

# Interview Questions

---

## What is a Virtual Environment?

An isolated Python environment for a project.

---

## Why Do We Use Virtual Environments?

To avoid dependency conflicts between projects.

---

## What is requirements.txt?

A file containing all project dependencies and their versions.

---

## What is pip?

Python's package manager.

---

## Why Should venv Be Added to .gitignore?

Because it can be recreated using `requirements.txt`.

---

## What Are Environment Variables?

Variables used to store configuration and sensitive information outside the source code.

---

## Difference Between venv and Docker?

`venv` isolates Python packages.

Docker packages the entire application and its environment.

---

# Key Takeaways

1. Every Python project should have its own virtual environment.
2. Virtual environments prevent dependency conflicts.
3. `pip` installs and manages Python packages.
4. `requirements.txt` makes projects reproducible.
5. Never upload `venv` to GitHub.
6. Use `.gitignore` to exclude unnecessary files.
7. Store secrets using environment variables, not in code.
8. `venv` is ideal for most Python projects.
9. Conda is another environment manager, popular in Data Science.
10. Good environment management makes your projects reliable, portable, and easier to collaborate on.

---

# Final Mental Model

```text
Create Project
      ↓
Create Virtual Environment
      ↓
Activate Environment
      ↓
Install Packages
      ↓
Write Code
      ↓
Save requirements.txt
      ↓
Push to GitHub
      ↓
Deploy
```

Think of a virtual environment as a **private workspace** for each project. Every project gets its own Python installation and dependencies, so changes in one project never accidentally break another.

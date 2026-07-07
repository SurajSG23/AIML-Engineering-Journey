# Docker Fundamentals

> Imagine you build an AI application on your laptop.
>
> It works perfectly.
>
> You send it to your friend, but it doesn't work.
>
> You deploy it to a server, and it still doesn't work.
>
> The most common reason is:
>
> **Different environments.**
>
> Docker solves this problem by packaging your application and everything it needs into a single portable container.

---

# Why Do We Need Docker?

Suppose you build a Python project.

It uses:

* Python 3.12
* NumPy
* Pandas
* FastAPI
* Scikit-learn

Everything works perfectly on your laptop.

Your friend tries to run it.

Instead they get:

```text
ModuleNotFoundError

Package version mismatch

Python version mismatch
```

The famous phrase is:

```text
"It works on my machine."
```

Docker ensures it works on **every machine**.

---

# What is Docker?

Docker is a platform used to:

* Build applications
* Package applications
* Run applications

inside lightweight environments called **Containers**.

Think of Docker as a shipping company.

Your application is the product.

Docker packages everything safely so it reaches every computer in exactly the same condition.

---

# What Problem Does Docker Solve?

Without Docker:

```text
My Laptop
     ↓
Works

Friend's Laptop
     ↓
Doesn't Work

Cloud Server
     ↓
Doesn't Work
```

With Docker:

```text
Docker Container
      ↓
Laptop ✓

Server ✓

Cloud ✓

Windows ✓

Linux ✓

Mac ✓
```

Same application.

Same environment.

Same behavior.

---

# What is a Container?

A container is an isolated environment where your application runs.

It contains:

* Application code
* Python
* Required libraries
* Dependencies
* Environment settings

Everything your application needs.

Think of a container as a lunchbox.

Inside it are:

* Food
* Spoon
* Fork
* Napkin

Wherever you take the lunchbox, everything you need is already inside.

---

# Virtual Machines vs Containers

Before Docker, developers used Virtual Machines (VMs).

---

## Virtual Machine

A Virtual Machine includes:

```text
Application
Operating System
Libraries
Drivers
```

Every VM contains its own complete operating system.

Result:

* Large size
* Slow startup
* High memory usage

---

## Docker Container

A Docker Container contains only:

```text
Application
Dependencies
Libraries
```

It shares the host operating system.

Result:

* Smaller
* Faster
* Lightweight

---

Comparison

| Virtual Machine     | Docker Container   |
| ------------------- | ------------------ |
| Includes full OS    | Shares host OS     |
| Large (GBs)         | Small (MBs)        |
| Slow startup        | Starts in seconds  |
| Higher memory usage | Lower memory usage |

---

# Important Docker Terms

Before learning commands, understand these concepts.

---

# Docker Engine

Docker Engine is the software that runs Docker.

Think of it as:

```text
The machine that manages containers.
```

---

# Docker Image

A Docker Image is a blueprint or template.

Think of it as:

```text
A recipe
```

It contains everything needed to create a container.

Example:

```text
Python 3.12

FastAPI

NumPy

Pandas
```

This becomes an image.

---

# Docker Container

A running instance of an image.

Think:

```text
Recipe
↓

Cooked Food
```

Recipe = Image

Cooked Food = Container

---

# Dockerfile

A Dockerfile is a text file containing instructions for building an image.

Example:

```dockerfile
FROM python:3.12

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["python", "app.py"]
```

Docker reads these instructions and builds an image.

---

# Docker Hub

Docker Hub is an online repository of Docker images.

Think of it like:

* GitHub for code
* Docker Hub for Docker images

Examples:

* Python
* Ubuntu
* MySQL
* Redis
* MongoDB

can all be downloaded from Docker Hub.

---

# Docker Workflow

The basic workflow is:

```text
Write Application
        ↓
Create Dockerfile
        ↓
Build Docker Image
        ↓
Run Docker Container
```

---

# Installing Docker

Check installation:

```bash
docker --version
```

Example:

```text
Docker version 28.x.x
```

---

Check if Docker is running:

```bash
docker info
```

---

# Your First Docker Command

Run:

```bash
docker run hello-world
```

Docker:

1. Downloads image
2. Creates container
3. Runs container
4. Prints message

Congratulations!

You have run your first Docker container.

---

# Understanding Docker Images

View downloaded images:

```bash
docker images
```

Example:

```text
python

ubuntu

hello-world
```

These are stored locally.

---

# Pulling Images

Download an image:

```bash
docker pull python
```

Docker downloads the latest Python image.

---

Download Ubuntu:

```bash
docker pull ubuntu
```

---

# Running Containers

Run Python:

```bash
docker run python
```

Docker creates a container from the Python image.

---

Interactive mode:

```bash
docker run -it python
```

This opens a Python terminal.

---

# Listing Containers

Running containers:

```bash
docker ps
```

---

All containers:

```bash
docker ps -a
```

Shows:

* Running
* Stopped
* Exited

containers.

---

# Stopping Containers

Stop container:

```bash
docker stop <container_id>
```

Example:

```bash
docker stop abc123
```

---

# Starting Containers

Restart:

```bash
docker start <container_id>
```

---

# Removing Containers

Delete:

```bash
docker rm <container_id>
```

---

# Removing Images

Delete image:

```bash
docker rmi image_name
```

Example:

```bash
docker rmi python
```

---

# Building Your Own Image

Suppose project:

```text
my_app/

app.py

requirements.txt

Dockerfile
```

Build:

```bash
docker build -t my_app .
```

Meaning:

```text
-t

Assign image name

.

Current directory
```

---

View image:

```bash
docker images
```

---

Run image:

```bash
docker run my_app
```

---

# Understanding Dockerfile

Example:

```dockerfile
FROM python:3.12
```

Meaning:

```text
Start with Python image.
```

---

```dockerfile
WORKDIR /app
```

Meaning:

```text
Working directory inside container.
```

---

```dockerfile
COPY . .
```

Meaning:

```text
Copy project files.
```

---

```dockerfile
RUN pip install -r requirements.txt
```

Meaning:

```text
Install dependencies.
```

---

```dockerfile
CMD ["python", "app.py"]
```

Meaning:

```text
Run application.
```

---

# Volumes

Problem:

Suppose container stores:

```text
Database
```

You delete the container.

Data disappears.

Solution:

```text
Volumes
```

Volumes store data outside containers.

Containers can be deleted without losing data.

---

# Ports

Applications usually run on ports.

Example:

FastAPI:

```text
8000
```

React:

```text
5173
```

Suppose application runs inside Docker:

```text
Container

Port 8000
```

Need to expose it.

Run:

```bash
docker run -p 8000:8000 my_app
```

Meaning:

```text
Computer Port 8000

↓

Container Port 8000
```

Now browser can access the app.

---

# Environment Variables

Applications often need:

* API Keys
* Database URLs
* Secrets

Instead of hardcoding them:

```python
API_KEY="12345"
```

Use environment variables.

Run:

```bash
docker run -e API_KEY=12345 my_app
```

Safer and more flexible.

---

# Docker Compose

Imagine your project uses:

* FastAPI
* PostgreSQL
* Redis

Running each manually becomes difficult.

Docker Compose starts multiple containers together.

Example:

```yaml
services:
  api:
  database:
  redis:
```

Run everything:

```bash
docker compose up
```

Stop everything:

```bash
docker compose down
```

---

# Docker in AI and Machine Learning

Docker is widely used because AI projects have many dependencies.

Example:

```text
Python

TensorFlow

PyTorch

CUDA

FastAPI

NumPy

Pandas
```

Instead of installing everything manually:

```text
One Docker Image
```

contains everything.

---

# Typical AI Deployment Workflow

```text
Train Model
      ↓
Save Model
      ↓
Build FastAPI
      ↓
Create Docker Image
      ↓
Deploy Anywhere
```

---

# Common Docker Commands

Check version:

```bash
docker --version
```

---

Run container:

```bash
docker run image_name
```

---

List images:

```bash
docker images
```

---

List containers:

```bash
docker ps
```

---

Build image:

```bash
docker build -t my_app .
```

---

Stop container:

```bash
docker stop container_id
```

---

Remove container:

```bash
docker rm container_id
```

---

Remove image:

```bash
docker rmi image_name
```

---

Pull image:

```bash
docker pull python
```

---

Start services with Docker Compose:

```bash
docker compose up
```

---

Stop services:

```bash
docker compose down
```

---

# Real-World Example

Suppose you've built an AI chatbot using:

* FastAPI
* Ollama
* LangChain

Without Docker:

```text
Install Python

Install Dependencies

Configure Environment

Hope Everything Works
```

With Docker:

```text
docker run ai-chatbot
```

That's it.

---

# Advantages of Docker

* Consistent environments
* Easy deployment
* Lightweight
* Fast startup
* Simplifies collaboration
* Easy to scale
* Excellent for AI applications

---

# Limitations

* Small learning curve
* Containers share host OS
* Large AI images can consume storage
* GPU configuration can be challenging for beginners

---

# Common Beginner Mistakes

---

## Confusing Images and Containers

Remember:

```text
Image

↓

Blueprint
```

```text
Container

↓

Running Application
```

---

## Forgetting to Expose Ports

Application runs.

Browser cannot access it.

Usually caused by missing:

```bash
-p
```

---

## Building Image After Every Tiny Change

During development, use volumes instead of rebuilding repeatedly.

---

## Storing Secrets in Dockerfile

Never put:

* Passwords
* API Keys
* Tokens

inside Dockerfiles.

Use environment variables.

---

# Interview Questions

---

## What is Docker?

A platform for developing, packaging, and running applications inside containers.

---

## What is a Container?

An isolated environment containing an application and its dependencies.

---

## Difference Between Image and Container?

Image:

Blueprint.

Container:

Running instance of an image.

---

## What is a Dockerfile?

A file containing instructions for building Docker images.

---

## What is Docker Hub?

An online repository of Docker images.

---

## What is Docker Compose?

A tool for running multiple containers together.

---

## Why is Docker Popular?

Because it provides consistent environments and simplifies deployment.

---

# Key Takeaways

1. Docker packages applications with all their dependencies.
2. Containers are lightweight isolated environments.
3. Images are blueprints used to create containers.
4. Dockerfiles define how images are built.
5. Docker Hub stores public images.
6. Docker Compose manages multiple containers.
7. Volumes preserve data outside containers.
8. Ports allow applications inside containers to be accessed.
9. Docker is widely used for AI model deployment.
10. Docker eliminates the "It works on my machine" problem.

---

# Final Mental Model

```text
Write Code
     ↓
Create Dockerfile
     ↓
Build Docker Image
     ↓
Run Docker Container
     ↓
Deploy Anywhere
```

Think of Docker as a **shipping container** used in international trade.

Whether it's transported by a truck, train, or ship, the container and everything inside remain the same. Similarly, a Docker container runs the same way on your laptop, a cloud server, or a production environment.

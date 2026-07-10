# FastAPI Deployment

> Building a Machine Learning model is only half the job.
>
> The real value comes when people can actually **use** your model.
>
> This is called **Deployment**.
>
> In this guide, you'll learn how to deploy AI and Machine Learning models using **FastAPI**, one of the most popular Python web frameworks.

---

# What is Deployment?

Deployment means making your application available for others to use.

For example, suppose you've built a model that predicts house prices.

Without deployment:

```text
You
↓

Run Python Script

↓

Get Prediction
```

Only you can use it.

After deployment:

```text
User

↓

Website / Mobile App

↓

FastAPI

↓

Machine Learning Model

↓

Prediction
```

Anyone can use your model through an API.

---

# What is an API?

API stands for:

```text
Application Programming Interface
```

Don't worry about the complicated name.

Think of an API as a **waiter in a restaurant**.

Example:

```text
Customer
     ↓
Waiter (API)
     ↓
Kitchen (Model)
     ↓
Waiter
     ↓
Customer
```

The customer never enters the kitchen.

Similarly, users never directly interact with your ML model.

They communicate through the API.

---

# Why FastAPI?

FastAPI is a modern Python framework for building APIs.

It is popular because it is:

* Fast
* Easy to learn
* Automatic documentation
* Excellent for AI and ML projects
* Supports asynchronous programming
* Built on Python type hints

Today, many AI applications expose their models using FastAPI.

---

# FastAPI Installation

Install FastAPI:

```bash
pip install fastapi
```

Install the web server:

```bash
pip install uvicorn
```

Or install both together:

```bash
pip install fastapi uvicorn
```

---

# Your First FastAPI Application

Create:

```text
main.py
```

Write:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"message": "Hello FastAPI!"}
```

Run:

```bash
uvicorn main:app --reload
```

Open:

```text
http://127.0.0.1:8000
```

Output:

```json
{
    "message": "Hello FastAPI!"
}
```

Congratulations!

You have created your first API.

---

# Understanding the Code

Create application:

```python
app = FastAPI()
```

This creates a FastAPI application.

---

Define a route:

```python
@app.get("/")
```

Meaning:

When someone visits:

```text
/
```

execute the function below.

---

Function:

```python
def home():
```

Returns:

```python
{"message": "Hello FastAPI!"}
```

FastAPI automatically converts it into JSON.

---

# What is JSON?

Most APIs communicate using JSON.

Example:

```json
{
    "name": "Suraj",
    "age": 22
}
```

JSON is simply a way of exchanging data.

---

# HTTP Methods

FastAPI supports different HTTP methods.

The most common are:

| Method | Purpose       |
| ------ | ------------- |
| GET    | Retrieve data |
| POST   | Send data     |
| PUT    | Update data   |
| DELETE | Delete data   |

---

# GET Request

Example:

```python
@app.get("/hello")
def hello():
    return {"message": "Hello"}
```

Visit:

```text
http://127.0.0.1:8000/hello
```

Response:

```json
{
    "message": "Hello"
}
```

GET is mainly used to retrieve information.

---

# POST Request

POST is used to send data.

Example:

```python
from pydantic import BaseModel

class Student(BaseModel):
    name: str
    age: int

@app.post("/student")
def create_student(student: Student):
    return student
```

Input:

```json
{
    "name": "Suraj",
    "age": 22
}
```

Output:

```json
{
    "name": "Suraj",
    "age": 22
}
```

---

# What is Pydantic?

Pydantic validates incoming data.

Example:

```python
class Student(BaseModel):
    name: str
    age: int
```

If someone sends:

```json
{
    "name": "Suraj",
    "age": "Twenty"
}
```

FastAPI automatically returns an error.

Very useful for preventing invalid input.

---

# Path Parameters

Example:

```python
@app.get("/square/{number}")
def square(number: int):
    return {"square": number * number}
```

Visit:

```text
/square/5
```

Output:

```json
{
    "square": 25
}
```

---

# Query Parameters

Example:

```python
@app.get("/search")
def search(name: str):
    return {"name": name}
```

Visit:

```text
/search?name=Suraj
```

Output:

```json
{
    "name": "Suraj"
}
```

---

# Automatic API Documentation

One of FastAPI's best features.

Run your application.

Visit:

```text
http://127.0.0.1:8000/docs
```

You will see:

* Interactive API documentation
* Test API directly
* View request and response formats

FastAPI generates this automatically.

---

# Serving a Machine Learning Model

Suppose you trained a Linear Regression model.

Save it:

```python
import joblib

joblib.dump(model, "model.pkl")
```

Later:

```python
model = joblib.load("model.pkl")
```

Now the model is ready to serve predictions.

---

# Example Prediction API

```python
from fastapi import FastAPI
from pydantic import BaseModel
import joblib

app = FastAPI()

model = joblib.load("model.pkl")

class House(BaseModel):
    area: float

@app.post("/predict")
def predict(data: House):
    prediction = model.predict([[data.area]])

    return {
        "predicted_price": prediction[0]
    }
```

Input:

```json
{
    "area": 1500
}
```

Output:

```json
{
    "predicted_price": 250000
}
```

This is how most ML APIs work.

---

# Typical ML Deployment Workflow

```text
Collect Data
      ↓
Train Model
      ↓
Save Model
      ↓
Load Model
      ↓
Create FastAPI Endpoint
      ↓
Deploy
      ↓
Users Get Predictions
```

---

# Project Structure

A typical FastAPI project:

```text
house_price_api/

│── main.py
│── model.pkl
│── requirements.txt
│── Dockerfile
│── app/
│    ├── models.py
│    ├── routes.py
│    └── utils.py
```

As projects grow, separating files makes maintenance easier.

---

# Running FastAPI

Development mode:

```bash
uvicorn main:app --reload
```

Explanation:

```text
main

↓

Python file
```

```text
app

↓

FastAPI object
```

```text
--reload

↓

Automatically restart after code changes
```

---

# Requirements File

Generate:

```bash
pip freeze > requirements.txt
```

Example:

```text
fastapi
uvicorn
numpy
pandas
scikit-learn
joblib
```

This allows others to install the same dependencies.

---

# Deploying with Docker

Create a Dockerfile:

```dockerfile
FROM python:3.12

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

Build:

```bash
docker build -t fastapi-app .
```

Run:

```bash
docker run -p 8000:8000 fastapi-app
```

Your API now runs inside a Docker container.

---

# Deploying to the Cloud

Common platforms include:

* Render
* Railway
* Google Cloud
* AWS
* Azure
* DigitalOcean

General workflow:

```text
Code
    ↓
GitHub
    ↓
Cloud Platform
    ↓
Public API
```

Your FastAPI application becomes accessible from anywhere.

---

# Testing APIs

You can test your API using:

* FastAPI Docs (`/docs`)
* Postman
* Insomnia
* cURL

Example using cURL:

```bash
curl http://127.0.0.1:8000
```

---

# Error Handling

Example:

```python
from fastapi import HTTPException

@app.get("/student/{id}")
def student(id: int):

    if id < 1:
        raise HTTPException(
            status_code=404,
            detail="Student not found"
        )

    return {"id": id}
```

Instead of crashing, the API returns a proper error.

---

# Environment Variables

Never hardcode secrets like:

```python
API_KEY = "123456"
```

Instead use environment variables.

Example:

```python
import os

api_key = os.getenv("API_KEY")
```

Safer and more professional.

---

# FastAPI in AI Applications

FastAPI is commonly used for:

* Image Classification APIs
* Chatbots
* Recommendation Systems
* Sentiment Analysis
* Speech Recognition
* OCR
* LLM Applications
* RAG Applications

Example:

```text
User
   ↓
FastAPI
   ↓
LLM
   ↓
Response
```

---

# Advantages of FastAPI

* Easy to learn
* Extremely fast
* Automatic documentation
* Input validation
* Excellent Python support
* Perfect for AI deployment

---

# Limitations

* Requires understanding of APIs
* Large-scale deployments need additional tools
* Async programming may be confusing initially

---

# Common Beginner Mistakes

---

## Forgetting to Install Uvicorn

FastAPI needs a server to run.

Install:

```bash
pip install uvicorn
```

---

## Hardcoding Model Paths

Instead of:

```python
model = joblib.load("C:/Users/Desktop/model.pkl")
```

Use relative paths.

---

## Not Validating Input

Always use Pydantic models.

They prevent many bugs.

---

## Keeping Training Code in the API

The API should:

```text
Load Model

↓

Predict
```

Training should happen separately.

---

# Interview Questions

---

## What is FastAPI?

A modern Python framework for building APIs.

---

## Why is FastAPI Popular for AI?

Because it is fast, easy to use, and integrates well with Python ML libraries.

---

## What is Uvicorn?

An ASGI server used to run FastAPI applications.

---

## What is Pydantic?

A library used for validating and parsing input data.

---

## What is an API?

A way for different applications to communicate with each other.

---

## Why Save Models Using Joblib?

So they can be loaded later without retraining.

---

# Key Takeaways

1. Deployment makes your model available to users.
2. FastAPI is one of the best frameworks for deploying Python ML models.
3. APIs act as a bridge between users and models.
4. FastAPI automatically generates API documentation.
5. Pydantic validates input data.
6. Uvicorn runs FastAPI applications.
7. Models are usually saved using `joblib` or `pickle`.
8. Docker makes deployment portable and consistent.
9. Cloud platforms host your FastAPI application online.
10. Deployment is an essential part of every AI engineer's workflow.

---

# Final Mental Model

```text
Train Model
     ↓
Save Model (.pkl)
     ↓
Load Model in FastAPI
     ↓
Create API Endpoint
     ↓
Run with Uvicorn
     ↓
(Optional) Dockerize
     ↓
Deploy to Cloud
     ↓
Users Send Requests
     ↓
Model Returns Predictions
```

Think of FastAPI as the **bridge** between your Machine Learning model and the outside world. Your model may be brilliant, but without an API, no one else can easily use it. FastAPI turns your model into a service that websites, mobile apps, and other software can access with a simple request.

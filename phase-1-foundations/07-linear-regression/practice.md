# Linear Regression

> Linear Regression is often the first Machine Learning algorithm people learn.
>
> It is simple, powerful, and forms the foundation for understanding many other Machine Learning algorithms.
>
> If you understand Linear Regression properly, concepts like Gradient Descent, Loss Functions, and Model Training become much easier.

---

# What is Linear Regression?

Linear Regression is a **Supervised Machine Learning Algorithm** used to predict a continuous numerical value.

Examples:

* House Price Prediction
* Salary Prediction
* Sales Forecasting
* Temperature Prediction

---

# Real World Example

Suppose you have the following data:

| House Size (sq ft) | Price ($) |
| ------------------ | --------- |
| 1000               | 200000    |
| 1200               | 240000    |
| 1500               | 300000    |
| 1800               | 360000    |

Question:

```text
If a house is 1600 sq ft,
what should its price be?
```

Linear Regression helps answer this question.

---

# Why "Linear"?

The word "Linear" comes from:

```text
Straight Line
```

Linear Regression tries to find the best straight line through the data.

Example:

```text
Price
 ^
 |
 |           *
 |        *
 |     *
 |  *
 +--------------------> Size
```

The algorithm finds a line that best represents the relationship between size and price.

---

# Understanding Features and Target

In Machine Learning we usually have:

### Features (Input Variables)

Information used to make predictions.

Example:

```text
House Size
Bedrooms
Age of House
```

---

### Target (Output Variable)

What we want to predict.

Example:

```text
House Price
```

---

Dataset:

| Size | Bedrooms | Price  |
| ---- | -------- | ------ |
| 1200 | 2        | 200000 |
| 1500 | 3        | 250000 |

Features:

```text
Size
Bedrooms
```

Target:

```text
Price
```

---

# The Equation of a Line

You may have seen:

```text
y = mx + c
```

In Machine Learning:

```text
y = wx + b
```

Where:

```text
y = Prediction

x = Input Feature

w = Weight

b = Bias
```

---

# Example

Suppose:

```text
y = 100x + 50000
```

House Size:

```text
1500
```

Prediction:

```text
y = 100(1500) + 50000

= 200000
```

Predicted Price:

```text
$200,000
```

---

# Understanding Weight

Weight determines:

```text
How much influence a feature has.
```

Example:

```text
Price = 100 × Size + 50000
```

Weight:

```text
100
```

Meaning:

Every additional square foot increases price by $100.

---

# Understanding Bias

Bias is the starting value.

Example:

```text
Price = 100 × Size + 50000
```

Bias:

```text
50000
```

Even when:

```text
Size = 0
```

Prediction starts at:

```text
50000
```

---

# Goal of Linear Regression

The goal is:

```text
Find the best values of:

Weight (w)

Bias (b)
```

so predictions become accurate.

---

# Prediction Process

Step 1:

Provide input

```text
House Size = 1600
```

---

Step 2:

Apply equation

```text
y = wx + b
```

---

Step 3:

Generate prediction

```text
Price = 210000
```

---

# Error

Predictions are rarely perfect.

Example:

Actual Price:

```text
220000
```

Predicted Price:

```text
210000
```

Error:

```text
10000
```

We need to reduce this error.

---

# Residuals

Residual means:

```text
Actual Value - Predicted Value
```

Example:

```text
220000 - 210000

= 10000
```

Residual:

```text
10000
```

Residuals help measure model performance.

---

# Loss Function

A Loss Function measures:

```text
How wrong the model is.
```

Large loss:

```text
Bad Model
```

Small loss:

```text
Good Model
```

---

# Mean Squared Error (MSE)

Most common loss function for Linear Regression.

Formula:

```text
MSE = Average of Squared Errors
```

---

Example

Errors:

```text
10
20
30
```

Square them:

```text
100
400
900
```

Average:

```text
(100 + 400 + 900) / 3

= 466.67
```

MSE:

```text
466.67
```

---

# Why Square Errors?

Without squaring:

```text
-10 + 10 = 0
```

Errors cancel each other.

Squaring prevents cancellation.

Also penalizes large mistakes more heavily.

---

# Best Fit Line

Many possible lines exist.

Example:

```text
Line A

Line B

Line C
```

Which one should we choose?

Answer:

```text
The line with the lowest loss.
```

---

# Training a Linear Regression Model

Training means:

```text
Finding the best
weight and bias.
```

---

Process:

```text
Data
 ↓
Prediction
 ↓
Error
 ↓
Update Weights
 ↓
Better Prediction
```

Repeat many times.

---

# Gradient Descent

How do we improve weights?

Answer:

```text
Gradient Descent
```

---

Imagine standing on a mountain.

Goal:

```text
Reach the lowest point.
```

You keep moving downhill.

Eventually you reach the bottom.

This is Gradient Descent.

---

# Learning Rate

Determines:

```text
How large each step should be.
```

---

Too Small:

```text
Very slow learning
```

---

Too Large:

```text
May overshoot minimum
```

---

Good Learning Rate:

```text
Fast and stable learning
```

---

# Simple Linear Regression

Uses:

```text
One Feature
```

Example:

```text
House Size → Price
```

Equation:

```text
y = wx + b
```

---

# Multiple Linear Regression

Uses:

```text
Multiple Features
```

Example:

```text
Price =
(Size × w1)
+
(Bedrooms × w2)
+
(Age × w3)
+
Bias
```

---

Dataset:

| Size | Bedrooms | Age | Price  |
| ---- | -------- | --- | ------ |
| 1200 | 2        | 5   | 200000 |
| 1500 | 3        | 3   | 250000 |

Now multiple features influence price.

---

# Assumptions of Linear Regression

---

## Linear Relationship

Input and output should have a roughly linear relationship.

Example:

```text
More Size
→ Higher Price
```

---

## Independent Observations

One data point should not depend on another.

---

## Minimal Outliers

Too many outliers can distort the model.

---

## Low Multicollinearity

Features should not be highly correlated with each other.

Example:

```text
Height in cm

Height in meters
```

Both represent the same information.

---

# Evaluating Linear Regression

After training, we must evaluate performance.

---

# Mean Absolute Error (MAE)

Formula:

```text
Average Absolute Error
```

Example:

Errors:

```text
10
20
30
```

MAE:

```text
20
```

Easy to understand.

---

# Mean Squared Error (MSE)

Squares errors.

Penalizes large mistakes more.

---

# Root Mean Squared Error (RMSE)

Square root of MSE.

Same units as target variable.

Often easier to interpret.

---

# R² Score

Measures:

```text
How much variance
is explained by the model.
```

Range:

```text
0 → Poor

1 → Perfect
```

Example:

```text
R² = 0.85
```

Means:

```text
85% of variation
explained by model.
```

---

# Overfitting

Model memorizes training data.

Training Performance:

```text
Excellent
```

Test Performance:

```text
Poor
```

Bad sign.

---

# Underfitting

Model is too simple.

Fails to learn patterns.

Poor performance everywhere.

---

# Linear Regression Using Scikit-Learn

Import:

```python
from sklearn.linear_model import LinearRegression
```

---

Create Data:

```python
import numpy as np

X = np.array([
    [1000],
    [1200],
    [1500],
    [1800]
])

y = np.array([
    200000,
    240000,
    300000,
    360000
])
```

---

Create Model:

```python
model = LinearRegression()
```

---

Train Model:

```python
model.fit(X, y)
```

---

Predict:

```python
prediction = model.predict([[1600]])

print(prediction)
```

---

# Understanding fit()

```python
model.fit(X, y)
```

This step:

```text
Learns

Weight
Bias
```

from the training data.

---

# Understanding predict()

```python
model.predict()
```

Uses learned patterns to generate predictions.

---

# Real World Applications

---

## House Price Prediction

Input:

```text
Size
Bedrooms
Location
```

Output:

```text
Price
```

---

## Salary Prediction

Input:

```text
Experience
Education
Skills
```

Output:

```text
Salary
```

---

## Sales Forecasting

Input:

```text
Marketing Spend
Previous Sales
```

Output:

```text
Future Sales
```

---

## Energy Consumption

Input:

```text
Temperature
Weather
```

Output:

```text
Power Usage
```

---

# Advantages

* Easy to understand
* Fast training
* Highly interpretable
* Strong baseline model

---

# Limitations

* Assumes linear relationships
* Sensitive to outliers
* Cannot capture complex patterns
* May underperform on highly nonlinear data

---

# Common Beginner Mistakes

---

## Ignoring Data Cleaning

Bad data produces bad predictions.

Always:

* Handle missing values
* Remove duplicates
* Check outliers

---

## Using Linear Regression for Classification

Wrong:

```text
Predicting:

Spam / Not Spam
```

Linear Regression is for continuous values.

Use Logistic Regression instead.

---

## Forgetting Train-Test Split

Always evaluate on unseen data.

---

# Interview Questions

---

## What is Linear Regression?

A supervised learning algorithm used to predict continuous numerical values.

---

## Difference Between Feature and Target?

Feature:

Input variable.

Target:

Output variable to predict.

---

## What is MSE?

Average of squared prediction errors.

---

## Why Square Errors?

To prevent error cancellation and penalize large mistakes.

---

## What is Overfitting?

Model memorizes training data and performs poorly on new data.

---

# Key Takeaways

1. Linear Regression predicts continuous values.

2. It learns a relationship between inputs and outputs.

3. The model equation is:

   ```text
   y = wx + b
   ```

4. Weight determines feature influence.

5. Bias is the starting value.

6. Residuals measure prediction errors.

7. MSE is the most common loss function.

8. Gradient Descent minimizes error.

9. Linear Regression can use one or many features.

10. It is one of the most important foundational ML algorithms.

---

# Final Mental Model

```text
Data
 ↓
Features (X)
 ↓
Linear Regression
 ↓
Prediction (ŷ)
 ↓
Compare With Actual Value (y)
 ↓
Calculate Error
 ↓
Adjust Weights
 ↓
Better Predictions
```

If you understand this flow, you understand the core idea behind not only Linear Regression, but many Machine Learning algorithms.

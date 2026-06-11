# Logistic Regression

> Despite its name, Logistic Regression is **not a regression algorithm**.
>
> Logistic Regression is a **Supervised Machine Learning Classification Algorithm**.
>
> It is used when we want to predict categories such as:
>
> * Yes / No
> * Spam / Not Spam
> * Pass / Fail
> * Fraud / Not Fraud
> * Disease / No Disease
>
> Logistic Regression is one of the most important classification algorithms and serves as the foundation for understanding many advanced Machine Learning models.

---

# Why Not Use Linear Regression?

Suppose we want to predict:

```text
Pass or Fail
```

We can represent:

```text
Fail = 0

Pass = 1
```

Using Linear Regression:

```text
Prediction = 1.7
```

Problem:

```text
1.7
```

does not make sense.

We need a prediction between:

```text
0 and 1
```

because probabilities must lie in that range.

This is why Logistic Regression exists.

---

# What is Logistic Regression?

Logistic Regression predicts:

```text
Probability
```

instead of a continuous value.

Example:

```text
Probability of passing exam

= 0.90
```

Meaning:

```text
90% chance of passing
```

---

# Real World Example

Suppose we have:

| Hours Studied | Pass |
| ------------- | ---- |
| 1             | 0    |
| 2             | 0    |
| 3             | 0    |
| 5             | 1    |
| 6             | 1    |
| 8             | 1    |

Question:

```text
A student studied 4 hours.

Will they pass?
```

Logistic Regression helps answer this.

---

# Classification

Classification means predicting categories.

Examples:

### Spam Detection

Input:

```text
Email Content
```

Output:

```text
Spam
Not Spam
```

---

### Medical Diagnosis

Input:

```text
Patient Information
```

Output:

```text
Disease
No Disease
```

---

### Loan Approval

Input:

```text
Income
Credit Score
Age
```

Output:

```text
Approved
Rejected
```

---

# Understanding Probability

Probability measures likelihood.

Range:

```text
0 → Impossible

1 → Certain
```

Examples:

```text
0.20
```

20% chance.

---

```text
0.80
```

80% chance.

---

```text
0.99
```

99% chance.

---

Logistic Regression predicts probabilities.

---

# The Sigmoid Function

The heart of Logistic Regression is the:

```text
Sigmoid Function
```

Its job is to convert any number into:

```text
0 to 1
```

---

Example:

Input:

```text
-100
```

Output:

```text
~0
```

---

Input:

```text
0
```

Output:

```text
0.5
```

---

Input:

```text
100
```

Output:

```text
~1
```

---

Graph:

```text
            ______
          /
        /
------/
     /
   /
___/
```

This S-shaped curve is called a Sigmoid Curve.

---

# Why Sigmoid is Useful

Without Sigmoid:

Predictions could be:

```text
-50
20
1000
```

These are not valid probabilities.

Sigmoid converts them into:

```text
0.01
0.60
0.99
```

which are valid probabilities.

---

# Logistic Regression Equation

Linear Regression:

```text
y = wx + b
```

---

Logistic Regression:

Step 1:

```text
z = wx + b
```

Step 2:

Apply Sigmoid.

```text
Probability = Sigmoid(z)
```

---

Think of it as:

```text
Input
  ↓
wx + b
  ↓
Sigmoid
  ↓
Probability
```

---

# Decision Boundary

Eventually we must convert probability into a class.

Example:

```text
Probability = 0.85
```

Prediction:

```text
Pass
```

---

Common rule:

```text
Probability ≥ 0.5

Class = 1
```

---

```text
Probability < 0.5

Class = 0
```

---

This cutoff is called the:

```text
Decision Boundary
```

---

# Example

Suppose:

```text
Probability = 0.90
```

Prediction:

```text
1
```

Pass.

---

Suppose:

```text
Probability = 0.20
```

Prediction:

```text
0
```

Fail.

---

# Understanding the Output

Logistic Regression does NOT directly say:

```text
Pass
```

Instead it says:

```text
90% probability of passing
```

Then we apply a threshold.

---

# Training Logistic Regression

Goal:

```text
Find the best

Weights
Bias
```

so classification becomes accurate.

---

Process:

```text
Input Data
      ↓
Prediction
      ↓
Error
      ↓
Update Weights
      ↓
Better Prediction
```

Repeated many times.

---

# Why MSE is Not Used

In Linear Regression we used:

```text
Mean Squared Error (MSE)
```

For Logistic Regression, MSE creates optimization problems.

Instead we use:

```text
Log Loss
```

also called:

```text
Binary Cross Entropy
```

---

# Log Loss

Measures how wrong predicted probabilities are.

---

Good Prediction:

Actual:

```text
1
```

Predicted:

```text
0.95
```

Loss:

```text
Small
```

---

Bad Prediction:

Actual:

```text
1
```

Predicted:

```text
0.05
```

Loss:

```text
Large
```

---

Goal:

```text
Minimize Log Loss
```

---

# Gradient Descent

Just like Linear Regression.

Used to:

```text
Adjust Weights

Adjust Bias
```

to reduce loss.

---

Process:

```text
Prediction
 ↓
Calculate Loss
 ↓
Calculate Gradient
 ↓
Update Parameters
 ↓
Repeat
```

---

# Binary Classification

Most common Logistic Regression problem.

Two classes.

Examples:

```text
Spam / Not Spam

Fraud / Not Fraud

Pass / Fail

Disease / No Disease
```

---

Output:

```text
0 or 1
```

---

# Multiclass Classification

More than two classes.

Examples:

```text
Cat

Dog

Bird
```

---

Student Grades:

```text
A

B

C

D
```

---

Standard Logistic Regression handles:

```text
Binary Classification
```

Multiclass problems use extensions such as:

```text
Softmax Regression
```

---

# Evaluating Logistic Regression

Accuracy alone is often not enough.

---

# Accuracy

Formula:

```text
Correct Predictions

÷

Total Predictions
```

---

Example:

100 predictions.

95 correct.

Accuracy:

```text
95%
```

---

# Problem with Accuracy

Suppose:

```text
1000 Transactions

995 Normal

5 Fraud
```

Model predicts:

```text
Everything Normal
```

Accuracy:

```text
99.5%
```

Looks amazing.

Actually useless.

---

# Precision

Among predicted positives:

```text
How many were actually positive?
```

---

Example:

Fraud Detection.

If model says:

```text
Fraud
```

How often is it correct?

---

# Recall

Among actual positives:

```text
How many did we find?
```

---

Example:

Cancer Detection.

Missing cancer cases is dangerous.

High recall is important.

---

# F1 Score

Combines:

```text
Precision
Recall
```

into one metric.

Useful when classes are imbalanced.

---

# Confusion Matrix

A powerful evaluation tool.

---

Predicted vs Actual.

|                 | Predicted Positive | Predicted Negative |
| --------------- | ------------------ | ------------------ |
| Actual Positive | True Positive      | False Negative     |
| Actual Negative | False Positive     | True Negative      |

---

# Understanding Terms

### True Positive

Predicted:

```text
Fraud
```

Actually:

```text
Fraud
```

Correct.

---

### True Negative

Predicted:

```text
Not Fraud
```

Actually:

```text
Not Fraud
```

Correct.

---

### False Positive

Predicted:

```text
Fraud
```

Actually:

```text
Not Fraud
```

False alarm.

---

### False Negative

Predicted:

```text
Not Fraud
```

Actually:

```text
Fraud
```

Dangerous mistake.

---

# Example Applications

---

## Spam Detection

Input:

```text
Email Text
```

Output:

```text
Spam
Not Spam
```

---

## Disease Prediction

Input:

```text
Medical Data
```

Output:

```text
Disease
No Disease
```

---

## Customer Churn

Input:

```text
Customer Activity
```

Output:

```text
Leave Company
Stay
```

---

## Loan Approval

Input:

```text
Income
Age
Credit Score
```

Output:

```text
Approve
Reject
```

---

# Logistic Regression in Scikit-Learn

Import:

```python
from sklearn.linear_model import LogisticRegression
```

---

Example Dataset:

```python
import numpy as np

X = np.array([
    [1],
    [2],
    [3],
    [5],
    [6],
    [8]
])

y = np.array([
    0,
    0,
    0,
    1,
    1,
    1
])
```

---

Create Model:

```python
model = LogisticRegression()
```

---

Train Model:

```python
model.fit(X, y)
```

---

Predict:

```python
model.predict([[4]])
```

Output:

```python
[1]
```

---

Probability:

```python
model.predict_proba([[4]])
```

Example Output:

```python
[[0.25, 0.75]]
```

Meaning:

```text
25% chance class 0

75% chance class 1
```

---

# Difference Between Linear and Logistic Regression

| Feature       | Linear Regression | Logistic Regression |
| ------------- | ----------------- | ------------------- |
| Problem Type  | Regression        | Classification      |
| Output        | Continuous Value  | Probability         |
| Example       | House Price       | Spam Detection      |
| Loss Function | MSE               | Log Loss            |
| Output Range  | Any Number        | 0 to 1              |

---

# Advantages

* Easy to understand
* Fast training
* Works well on many classification tasks
* Probabilistic output
* Highly interpretable

---

# Limitations

* Assumes linear decision boundary
* May struggle with highly complex data
* Sensitive to outliers
* Less powerful than advanced models

---

# Common Beginner Mistakes

---

## Thinking Logistic Regression is Regression

Despite the name:

```text
Logistic Regression

=

Classification Algorithm
```

---

## Using Accuracy Alone

Always consider:

* Precision
* Recall
* F1 Score

especially for imbalanced datasets.

---

## Ignoring Class Imbalance

A high accuracy model may still be useless.

---

## Not Understanding Probabilities

The model predicts:

```text
Probability
```

not directly the class.

---

# Interview Questions

---

## What is Logistic Regression?

A supervised classification algorithm that predicts probabilities and class labels.

---

## Why is it called Logistic Regression?

Because it uses a logistic (sigmoid) function, even though it performs classification.

---

## What is the Sigmoid Function?

A function that converts any value into a probability between 0 and 1.

---

## Why use Log Loss?

Because MSE is not suitable for optimizing classification probabilities.

---

## Difference Between Linear and Logistic Regression?

Linear Regression predicts continuous values.

Logistic Regression predicts probabilities and classes.

---

# Key Takeaways

1. Logistic Regression is a classification algorithm.
2. It predicts probabilities.
3. Probabilities are converted into classes using a threshold.
4. The Sigmoid Function maps values to 0–1.
5. Log Loss is used instead of MSE.
6. Gradient Descent is used for optimization.
7. Accuracy is not always sufficient.
8. Precision, Recall, and F1 Score are important metrics.
9. Logistic Regression is widely used in real-world classification problems.
10. It is one of the most important foundational ML algorithms.

---

# Final Mental Model

```text
Features (X)
      ↓
wx + b
      ↓
Sigmoid Function
      ↓
Probability
      ↓
Threshold (0.5)
      ↓
Class Prediction
      ↓
Calculate Loss
      ↓
Update Weights
      ↓
Better Classifier
```

If you understand this flow, you understand the core idea behind Logistic Regression and many other classification algorithms.

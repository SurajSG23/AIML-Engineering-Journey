# Random Forest

> Random Forest is one of the most powerful and widely used Machine Learning algorithms.
>
> If a Decision Tree is a single expert making a decision,
>
> then a Random Forest is a committee of experts voting together.
>
> This simple idea makes Random Forest more accurate, more stable, and less prone to overfitting than a single Decision Tree.

---

# Why Do We Need Random Forest?

Let's start with a Decision Tree.

Suppose we train a Decision Tree on a dataset.

Result:

```text
Training Accuracy = 100%

Test Accuracy = 75%
```

Problem:

```text
Overfitting
```

The tree memorized the training data.

It learned:

```text
Noise
+
Patterns
```

instead of just patterns.

We need something more reliable.

This is where Random Forest helps.

---

# What is a Random Forest?

A Random Forest is a collection of many Decision Trees.

Instead of relying on one tree:

```text
Decision Tree
     ↓
Prediction
```

we use:

```text
Tree 1
Tree 2
Tree 3
Tree 4
Tree 5
...
Tree N
     ↓
Voting
     ↓
Final Prediction
```

This idea is called:

```text
Ensemble Learning
```

---

# What is Ensemble Learning?

Ensemble Learning means:

```text
Combine multiple models
to create a better model.
```

Idea:

```text
Many weak learners
       ↓
One strong learner
```

Random Forest is an ensemble of Decision Trees.

---

# Real Life Analogy

Imagine you ask:

```text
Should I buy this stock?
```

One expert says:

```text
Buy
```

Would you blindly trust them?

Probably not.

Instead you ask:

```text
10 experts
```

If:

```text
8 say Buy

2 say Don't Buy
```

You are more confident.

Random Forest works similarly.

---

# How Random Forest Works

Step 1:

Create multiple Decision Trees.

---

Step 2:

Each tree sees a slightly different version of the data.

---

Step 3:

Each tree makes a prediction.

---

Step 4:

Combine predictions.

---

Step 5:

Return final prediction.

---

Process:

```text
Dataset
    ↓
Create Many Trees
    ↓
Each Tree Predicts
    ↓
Voting/Averaging
    ↓
Final Prediction
```

---

# Why Is It Called "Random" Forest?

Two types of randomness are introduced.

---

# Random Data Sampling

Each tree receives a random subset of data.

Example:

Original dataset:

```text
1000 rows
```

Tree 1:

```text
Random rows
```

Tree 2:

```text
Different random rows
```

Tree 3:

```text
Another random sample
```

Each tree learns slightly different patterns.

---

# Random Feature Selection

Suppose dataset contains:

```text
Age
Income
Credit Score
Education
Experience
```

Decision Tree:

```text
Can use all features.
```

Random Forest:

```text
Each tree sees only a random subset.
```

Example:

Tree 1:

```text
Age
Income
```

Tree 2:

```text
Credit Score
Education
```

Tree 3:

```text
Income
Experience
```

This increases diversity among trees.

---

# Bootstrap Sampling

Random Forest uses:

```text
Bootstrap Sampling
```

---

What is Bootstrap Sampling?

Randomly sample rows:

```text
WITH replacement
```

---

Example

Original data:

```text
A
B
C
D
E
```

Bootstrap sample:

```text
A
C
C
D
E
```

Notice:

```text
C appears twice.
```

This is allowed.

---

Why?

It creates different training datasets for different trees.

---

# Voting in Classification

Suppose:

```text
Tree 1 → Spam

Tree 2 → Spam

Tree 3 → Not Spam

Tree 4 → Spam

Tree 5 → Spam
```

Votes:

```text
Spam = 4

Not Spam = 1
```

Final prediction:

```text
Spam
```

This is called:

```text
Majority Voting
```

---

# Averaging in Regression

Suppose:

```text
Tree 1 → 200000

Tree 2 → 220000

Tree 3 → 210000

Tree 4 → 205000
```

Average:

```text
208750
```

Final prediction:

```text
208750
```

This reduces noise.

---

# Classification vs Regression

Random Forest can do both.

---

# Random Forest Classifier

Used for:

```text
Spam Detection

Fraud Detection

Disease Prediction

Customer Churn
```

Output:

```text
Class Label
```

---

# Random Forest Regressor

Used for:

```text
House Prices

Salary Prediction

Sales Forecasting
```

Output:

```text
Continuous Number
```

---

# Why Random Forest Works So Well

A single Decision Tree:

```text
High Variance
```

Meaning:

Small data changes can produce very different trees.

---

Random Forest:

```text
Many Trees
```

Average out mistakes.

Result:

```text
More Stable
```

---

Think of it as:

```text
One opinion
      ↓
Risky

Many opinions
      ↓
Reliable
```

---

# Bias and Variance

A very important ML concept.

---

# Bias

Error caused by overly simple assumptions.

Example:

```text
Underfitting
```

---

# Variance

Error caused by sensitivity to data.

Example:

```text
Overfitting
```

---

Decision Trees:

```text
Low Bias

High Variance
```

---

Random Forest:

```text
Low Bias

Lower Variance
```

Much better balance.

---

# Feature Importance

One huge advantage of Random Forest:

It tells us:

```text
Which features matter most.
```

Example:

Loan Approval Dataset

Feature Importance:

```text
Credit Score   50%

Income         30%

Age            15%

Education       5%
```

Now we know:

```text
Credit Score
```

is most important.

---

# Out-of-Bag (OOB) Samples

Remember:

Bootstrap sampling does not use every row.

Some rows are left out.

These are called:

```text
Out-of-Bag Samples
```

---

They can be used to estimate model performance without needing a separate validation set.

Useful but not required for beginners.

---

# Hyperparameters

Hyperparameters are settings we choose before training.

---

# n_estimators

Number of trees.

Example:

```python
RandomForestClassifier(
    n_estimators=100
)
```

Meaning:

```text
100 Decision Trees
```

---

More trees:

```text
Better Performance

But Slower Training
```

---

# max_depth

Maximum depth of each tree.

Example:

```python
max_depth=5
```

Helps prevent overfitting.

---

# min_samples_split

Minimum samples needed before splitting.

Example:

```python
min_samples_split=10
```

Prevents tiny branches.

---

# max_features

Number of features considered at each split.

Example:

```python
max_features="sqrt"
```

Introduces randomness.

Improves diversity.

---

# Training a Random Forest

Process:

```text
Dataset
   ↓
Create Bootstrap Samples
   ↓
Train Multiple Trees
   ↓
Each Tree Predicts
   ↓
Combine Results
   ↓
Final Prediction
```

---

# Random Forest in Scikit-Learn

Import:

```python
from sklearn.ensemble import RandomForestClassifier
```

---

Example Dataset:

```python
import numpy as np

X = np.array([
    [1],
    [2],
    [3],
    [4],
    [5]
])

y = np.array([
    0,
    0,
    0,
    1,
    1
])
```

---

Create Model:

```python
model = RandomForestClassifier()
```

---

Train:

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

# Random Forest Regressor

Import:

```python
from sklearn.ensemble import RandomForestRegressor
```

---

Example:

```python
model = RandomForestRegressor()

model.fit(X, y)

prediction = model.predict([[4]])
```

Used for numerical predictions.

---

# Evaluating Random Forest

Classification Metrics:

* Accuracy
* Precision
* Recall
* F1 Score

---

Regression Metrics:

* MAE
* MSE
* RMSE
* R²

---

# Advantages

---

High Accuracy

Often performs better than a single Decision Tree.

---

Reduces Overfitting

Averaging many trees improves generalization.

---

Handles Nonlinear Relationships

Can learn complex patterns.

---

Works With Large Datasets

Scales well.

---

Provides Feature Importance

Very useful for analysis.

---

Minimal Data Preparation

Usually no feature scaling needed.

---

# Limitations

---

Slower Than One Tree

Many trees require more computation.

---

Less Interpretable

A Decision Tree can be visualized.

A forest with 500 trees cannot.

---

Larger Memory Usage

Stores many trees.

---

May Still Overfit

If hyperparameters are poorly chosen.

---

# Real World Applications

---

# Fraud Detection

Input:

```text
Transaction Data
```

Output:

```text
Fraud
Not Fraud
```

---

# Loan Approval

Input:

```text
Income
Credit Score
Employment
```

Output:

```text
Approve
Reject
```

---

# Customer Churn

Input:

```text
Customer Behavior
```

Output:

```text
Leave
Stay
```

---

# Disease Prediction

Input:

```text
Medical Features
```

Output:

```text
Disease
No Disease
```

---

# Stock Market Analysis

Input:

```text
Historical Data
```

Output:

```text
Price Forecast
```

---

# Decision Tree vs Random Forest

| Feature          | Decision Tree | Random Forest  |
| ---------------- | ------------- | -------------- |
| Number of Trees  | 1             | Many           |
| Overfitting Risk | High          | Lower          |
| Accuracy         | Moderate      | Usually Higher |
| Stability        | Lower         | Higher         |
| Interpretability | Excellent     | Moderate       |
| Training Speed   | Faster        | Slower         |

---

# Logistic Regression vs Random Forest

| Feature             | Logistic Regression | Random Forest |
| ------------------- | ------------------- | ------------- |
| Relationship        | Linear              | Nonlinear     |
| Interpretability    | High                | Medium        |
| Complexity          | Simple              | More Powerful |
| Feature Engineering | Often Needed        | Less Needed   |
| Accuracy            | Good                | Often Better  |

---

# Common Beginner Mistakes

---

## Using Too Few Trees

Example:

```python
n_estimators=5
```

Usually not enough.

Common values:

```python
100
200
500
```

---

## Ignoring Hyperparameters

Random Forest has important settings.

Always experiment.

---

## Using Accuracy Alone

Also check:

* Precision
* Recall
* F1 Score

---

## Assuming Random Forest Cannot Overfit

It can.

Just less than a Decision Tree.

---

# Interview Questions

---

## What is Random Forest?

An ensemble learning algorithm that combines many Decision Trees.

---

## Why is it Better Than a Single Decision Tree?

Because it reduces variance and overfitting.

---

## What is Bootstrap Sampling?

Random sampling with replacement.

---

## What is Majority Voting?

Combining predictions by selecting the most common class.

---

## What is Feature Importance?

A measure of how useful a feature is for predictions.

---

## What is Ensemble Learning?

Combining multiple models to create a stronger model.

---

## Why is it Called Random Forest?

Because it uses:

* Random data samples
* Random feature subsets

to create diverse trees.

---

# Key Takeaways

1. Random Forest is an ensemble of Decision Trees.
2. It uses bootstrap sampling and random feature selection.
3. Classification uses majority voting.
4. Regression uses averaging.
5. It reduces overfitting compared to a single tree.
6. It handles nonlinear relationships well.
7. Feature importance is a major advantage.
8. More trees generally improve stability.
9. It is one of the most widely used ML algorithms.
10. Random Forest is often a strong baseline model for tabular data.

---

# Final Mental Model

```text
Dataset
    ↓
Create Random Samples
    ↓
Train Many Decision Trees
    ↓
Each Tree Makes Prediction
    ↓
Voting / Averaging
    ↓
Final Prediction
```

Think of a Decision Tree as:

```text
One Doctor
```

and a Random Forest as:

```text
A Panel of Doctors
```

A panel usually makes better decisions than a single person. That is the core idea behind Random Forest.

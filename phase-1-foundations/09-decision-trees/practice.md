# Decision Trees

> A Decision Tree is one of the most intuitive Machine Learning algorithms.
>
> It works very similarly to how humans make decisions:
>
> Ask a question → Get an answer → Ask another question → Make a decision.
>
> Decision Trees can be used for:
>
> * Classification
> * Regression
>
> They are easy to understand, visualize, and explain.

---

# What is a Decision Tree?

A Decision Tree is a Machine Learning algorithm that makes predictions by asking a series of questions.

Example:

```text
Will a student pass the exam?
```

Decision Tree:

```text
Hours Studied > 5?

        Yes
         |
         v
      Attendance > 75?

       /       \
     Yes       No
      |         |
      v         v
    Pass      Fail

```

The model keeps asking questions until it reaches a final prediction.

---

# Why is it Called a Tree?

The structure resembles a tree.

Example:

```text
            Root
              |
      ----------------
      |              |
     Yes            No
      |              |
    Node           Node
      |              |
    Leaf           Leaf
```

Important parts:

* Root Node
* Decision Node
* Leaf Node

---

# Real World Example

Suppose a bank wants to decide whether to approve a loan.

Data:

| Income | Credit Score | Loan Approved |
| ------ | ------------ | ------------- |
| High   | Good         | Yes           |
| High   | Poor         | Yes           |
| Low    | Good         | No            |
| Low    | Poor         | No            |

Decision Tree:

```text
Income = High?

      Yes
       |
       v
    Approve

      No
       |
       v
   Reject
```

Simple and intuitive.

---

# Terminology

---

# Root Node

The first question in the tree.

Example:

```text
Income > 50000?
```

This is the starting point.

---

# Decision Node

Intermediate question.

Example:

```text
Credit Score > 700?
```

More splitting occurs.

---

# Leaf Node

Final prediction.

Example:

```text
Approved
```

or

```text
Rejected
```

No further questions.

---

# How a Decision Tree Makes Predictions

Suppose we have:

```text
Age = 25

Income = 60000
```

Tree:

```text
Income > 50000?

     Yes
      |
      v
 Approved
```

Prediction:

```text
Approved
```

The sample travels from root to leaf.

---

# Why Decision Trees are Powerful

Humans naturally think in rules.

Example:

```text
If Age > 18

AND

Income > 50000

THEN

Approve Loan
```

Decision Trees automatically learn these rules.

---

# Classification Trees

Used when output is a category.

Examples:

```text
Spam / Not Spam

Pass / Fail

Fraud / Not Fraud

Disease / No Disease
```

Output:

```text
Class Label
```

---

# Regression Trees

Used when output is numerical.

Examples:

```text
House Price

Salary

Sales
```

Output:

```text
Continuous Number
```

---

# Example Classification Tree

Question:

```text
Will a student pass?
```

Tree:

```text
Hours Studied > 4?

      Yes
       |
       v
Attendance > 70?

    /       \
  Yes       No

 Pass      Fail
```

---

# Example Regression Tree

Question:

```text
Predict House Price
```

Tree:

```text
Area > 1500?

      Yes
       |
    300000

      No
       |
    200000
```

Leaf nodes contain numbers.

---

# The Main Goal

The goal is:

```text
Create groups
that are as pure as possible.
```

Example:

Bad Split:

```text
Pass
Fail
Pass
Fail
Pass
```

Mixed.

---

Good Split:

```text
Pass
Pass
Pass
Pass
```

Pure.

---

Decision Trees try to create pure groups.

---

# Understanding Purity

Imagine a node:

```text
Pass
Pass
Pass
Pass
```

Very pure.

---

Another node:

```text
Pass
Fail
Pass
Fail
```

Not pure.

---

The algorithm prefers pure nodes.

---

# How Does the Tree Choose Questions?

Suppose we have:

```text
Age

Income

Attendance
```

Which should be chosen first?

The algorithm calculates which question gives the best split.

---

For classification:

Common measures:

* Gini Impurity
* Entropy
* Information Gain

---

# Gini Impurity

Measures impurity.

Range:

```text
0 = Perfectly Pure
```

Higher values:

```text
More Mixed
```

---

Example:

```text
Pass
Pass
Pass
Pass
```

Gini:

```text
0
```

Perfectly pure.

---

Example:

```text
Pass
Fail
Pass
Fail
```

Higher impurity.

---

Goal:

```text
Minimize Gini Impurity
```

---

# Entropy

Another measure of impurity.

Think of entropy as:

```text
Disorder
```

Example:

```text
Pass
Pass
Pass
Pass
```

Low entropy.

---

Example:

```text
Pass
Fail
Pass
Fail
```

High entropy.

---

Goal:

```text
Reduce Entropy
```

---

# Information Gain

Measures how much uncertainty decreases after a split.

High Information Gain:

```text
Good Split
```

Low Information Gain:

```text
Bad Split
```

The tree chooses splits with maximum information gain.

---

# Building a Tree

Process:

```text
Start with Dataset
        ↓
Try Different Questions
        ↓
Choose Best Split
        ↓
Create Branches
        ↓
Repeat
        ↓
Leaf Nodes
```

---

# Stopping Criteria

When should the tree stop growing?

Common rules:

---

All samples belong to same class.

Example:

```text
Pass
Pass
Pass
```

Stop.

---

Maximum depth reached.

Example:

```text
Depth = 5
```

Stop.

---

Minimum samples reached.

Example:

```text
Only 2 rows left
```

Stop.

---

# Tree Depth

Depth means:

```text
Number of levels
```

Example:

```text
Root

 Level 1

 Level 2

 Level 3
```

Depth:

```text
3
```

---

# Deep Trees

Can learn complex patterns.

But risk:

```text
Overfitting
```

---

# Shallow Trees

Simpler.

Better generalization.

But risk:

```text
Underfitting
```

---

# Overfitting

Decision Trees can easily memorize data.

Example:

Training Accuracy:

```text
100%
```

Test Accuracy:

```text
70%
```

Bad sign.

---

Tree became too specific.

---

# Underfitting

Tree too simple.

Cannot learn patterns.

Example:

Training Accuracy:

```text
60%
```

Test Accuracy:

```text
58%
```

Poor everywhere.

---

# Pruning

Pruning means:

```text
Removing unnecessary branches.
```

Purpose:

* Reduce overfitting
* Improve generalization

---

Example:

Before:

```text
Very Deep Tree
```

After:

```text
Simpler Tree
```

---

# Feature Importance

Decision Trees naturally tell us:

```text
Which features matter most.
```

Example:

```text
Income → 60%

Credit Score → 30%

Age → 10%
```

Useful for understanding data.

---

# Decision Trees in Scikit-Learn

Import:

```python
from sklearn.tree import DecisionTreeClassifier
```

---

Dataset:

```python
import numpy as np

X = np.array([
    [2],
    [3],
    [4],
    [5],
    [6]
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
model = DecisionTreeClassifier()
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
[0]
```

---

# Important Parameters

---

## max_depth

Limits tree depth.

Example:

```python
DecisionTreeClassifier(
    max_depth=3
)
```

Helps prevent overfitting.

---

## min_samples_split

Minimum samples required to split.

Example:

```python
DecisionTreeClassifier(
    min_samples_split=5
)
```

---

## criterion

Determines split quality.

Options:

```python
criterion="gini"
```

or

```python
criterion="entropy"
```

---

# Evaluating Decision Trees

Common metrics:

---

Classification:

* Accuracy
* Precision
* Recall
* F1 Score

---

Regression:

* MAE
* MSE
* RMSE
* R²

---

# Advantages

---

Easy to understand.

---

Easy to visualize.

---

Handles numerical and categorical data.

---

No feature scaling required.

---

Provides feature importance.

---

Works for classification and regression.

---

# Limitations

---

Can overfit easily.

---

Small data changes can create different trees.

---

Less stable than ensemble methods.

---

May struggle with very complex relationships.

---

# Real World Applications

---

## Loan Approval

Input:

```text
Income
Credit Score
```

Output:

```text
Approve
Reject
```

---

## Medical Diagnosis

Input:

```text
Symptoms
Test Results
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
Usage
Subscription Length
```

Output:

```text
Leave
Stay
```

---

## Fraud Detection

Input:

```text
Transaction Data
```

Output:

```text
Fraud
Normal
```

---

# Decision Tree vs Logistic Regression

| Feature                | Logistic Regression | Decision Tree |
| ---------------------- | ------------------- | ------------- |
| Model Type             | Linear              | Rule-Based    |
| Easy to Interpret      | Yes                 | Very Easy     |
| Handles Nonlinear Data | Limited             | Better        |
| Feature Scaling Needed | Usually             | No            |
| Overfitting Risk       | Lower               | Higher        |

---

# Common Beginner Mistakes

---

## Letting Trees Grow Forever

Very deep trees usually overfit.

---

## Ignoring max_depth

One of the most important parameters.

---

## Using Accuracy Alone

Always examine:

* Precision
* Recall
* F1 Score

---

## Not Checking Feature Importance

Decision Trees provide valuable insights.

Use them.

---

# Interview Questions

---

## What is a Decision Tree?

A supervised learning algorithm that makes predictions using a series of decision rules.

---

## What is a Leaf Node?

A final prediction node.

---

## What is Gini Impurity?

A measure of how mixed classes are within a node.

---

## What is Entropy?

A measure of disorder or uncertainty.

---

## What is Information Gain?

The reduction in uncertainty after a split.

---

## Why Do Decision Trees Overfit?

Because they can keep creating branches until they memorize training data.

---

## What is Pruning?

Removing unnecessary branches to reduce overfitting.

---

# Key Takeaways

1. Decision Trees learn by asking questions.
2. They work for classification and regression.
3. Trees consist of root nodes, decision nodes, and leaf nodes.
4. The goal is to create pure groups.
5. Gini and Entropy measure impurity.
6. Information Gain helps choose the best split.
7. Deep trees may overfit.
8. Pruning helps generalization.
9. Feature importance is a major advantage.
10. Decision Trees are among the easiest ML algorithms to understand.

---

# Final Mental Model

```text
Dataset
   ↓
Ask Best Question
   ↓
Split Data
   ↓
Ask Another Question
   ↓
Create Pure Groups
   ↓
Leaf Node
   ↓
Prediction
```

If Logistic Regression learns a mathematical boundary, a Decision Tree learns a set of human-readable rules. That intuition will help you understand Random Forests and Gradient Boosting, which are built using many Decision Trees.

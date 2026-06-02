# Statistics for Machine Learning

> This file connects statistics directly to AI and Machine Learning.

Everything in previous notes becomes useful here.

---

# Why Statistics Matters in ML

Machine Learning is:

Data + Statistics + Optimization

Without statistics:

- Data cannot be understood
- Features cannot be evaluated
- Models cannot be trusted

---

# Feature Analysis

Features are input variables.

Examples:

House Price Dataset

Features:

- Area
- Bedrooms
- Age of house

Target:

- Price

---

Before training:

Ask:

- Is feature useful?
- Is feature noisy?
- Is feature missing values?

---

# Correlation

Measures relationship between variables.

Range:

-1 to +1

---

+1

Perfect positive relationship.

---

-1

Perfect negative relationship.

---

0

No linear relationship.

---

Example

Hours Studied vs Marks

Usually positive correlation.

---

# Pearson Correlation

Measures linear relationships.

Most common correlation metric.

---

# Spearman Correlation

Measures rank-based relationships.

Works better with non-linear trends.

---

# Correlation vs Causation

Extremely important.

Correlation:

Two variables move together.

Causation:

One variable causes another.

---

Example

Ice cream sales and drowning incidents increase together.

Ice cream does NOT cause drowning.

Summer causes both.

---

# Feature Selection

Choosing useful features.

Benefits:

- Faster training
- Better performance
- Less overfitting

---

# Dataset Bias

Occurs when data does not represent reality.

Example:

Facial recognition trained mostly on one demographic.

Results become unfair.

---

# Class Imbalance

Example:

10000 transactions

- 9950 Normal
- 50 Fraud

Model can achieve:

99.5% accuracy

by predicting everything as normal.

Accuracy becomes misleading.

---

Use:

- Precision
- Recall
- F1 Score

instead.

---

# Outlier Detection

Important in:

- Fraud detection
- Network security
- Manufacturing

Outliers may indicate rare events.

---

# Data Leakage

One of the most dangerous ML mistakes.

Occurs when future information accidentally enters training data.

---

Example

Predict whether a student passes.

Feature:

Final Exam Result

This directly reveals answer.

Model appears amazing.

Reality:

It cheated.

---

# Model Evaluation

---

## Accuracy

Correct Predictions / Total Predictions

Good when classes are balanced.

---

## Precision

Among predicted positives:

How many were correct?

Important when false positives are costly.

---

Example:

Spam detection.

---

## Recall

Among actual positives:

How many were found?

Important when missing positives is dangerous.

---

Example:

Cancer detection.

---

## F1 Score

Balances Precision and Recall.

Useful for imbalanced datasets.

---

# Overfitting

Model memorizes training data.

Training Accuracy:

99%

Test Accuracy:

70%

Bad generalization.

---

# Underfitting

Model too simple.

Cannot learn patterns.

Poor performance everywhere.

---

# Training and Validation Curves

Used to diagnose learning behavior.

---

Healthy Model

Training Error ↓

Validation Error ↓

---

Overfitting

Training Error ↓

Validation Error ↑

---

# Real-World Examples

---

## House Price Prediction

Statistics Used:

- Mean
- Median
- Correlation
- Outlier Detection

---

## Customer Churn

Statistics Used:

- Probability
- Class Imbalance
- Feature Selection

---

## Fraud Detection

Statistics Used:

- Outlier Detection
- Probability
- Precision
- Recall

---

## Recommendation Systems

Statistics Used:

- Probability
- Similarity Measures
- User Behavior Analysis

---

# Statistics Mindset for AI Engineers

Always ask:

1. Is data trustworthy?
2. Is sample representative?
3. Are there outliers?
4. Is there bias?
5. Is performance statistically meaningful?
6. Can results generalize?

Great AI engineers think statistically before thinking algorithmically.

---

# Key Takeaways

1. Statistics is the foundation of ML.
2. Correlation helps understand relationships.
3. Correlation does not imply causation.
4. Feature selection improves models.
5. Bias can ruin predictions.
6. Accuracy is not always enough.
7. Precision and recall are critical.
8. Data leakage creates misleading results.
9. Overfitting and underfitting must be monitored.
10. Strong statistical thinking leads to better AI systems.
# Statistics Practice

## Overview
Friendly, practical statistics notes for AI engineering. Short explanations, simple examples, and clear tips for data analysis and model evaluation.

---

## 1. Introduction

- What is statistics: tools to summarize data and make decisions based on data.
- Why stats for AI: measure data, evaluate models, design experiments, and make claims with confidence.
- Key areas: descriptive statistics, probability, estimation, hypothesis testing, regression, and resampling.

---

## SECTION 1 — Descriptive Statistics

### 2. Measures of Center

- Mean: average, use for symmetric data.
- Median: middle value, robust to outliers.
- Mode: most common value.

Example:
```python
import numpy as np
x = np.array([1,2,2,3,100])
np.mean(x), np.median(x)
```

### 3. Measures of Spread

- Range: max - min.
- Variance / standard deviation: how spread values are.
- IQR (interquartile range): Q3 - Q1, robust to outliers.

Example:
```python
np.std(x), np.var(x)
```

### 4. Shape

- Skewness: asymmetry of distribution.
- Kurtosis: "tailedness" of distribution.

---

## SECTION 2 — Probability Basics

### 5. Random Variables

- Discrete vs continuous.
- Expectation (mean) and variance definitions.

### 6. Common Distributions

- Bernoulli / Binomial: binary outcomes.
- Poisson: counts per interval.
- Uniform: equal probability.
- Normal (Gaussian): common continuous distribution; many stats tools assume normality.

Use NumPy / SciPy to sample and inspect.

---

## SECTION 3 — Sampling & Estimation

### 7. Sampling

- Random sampling gives representative subsets.
- Use `np.random` or Pandas `sample()` for shuffling and sampling.

### 8. Point Estimation

- Estimators (mean, proportion) estimate population values from samples.

### 9. Confidence Intervals

- Interval estimate around an estimator showing plausible values.
- Example (approximate 95% CI for mean): mean +/- 1.96 * (std / sqrt(n)).

---

## SECTION 4 — Hypothesis Testing

### 10. Basics

- Null hypothesis (H0) and alternative (H1).
- p-value: probability of observing data at least as extreme under H0.
- Choose significance level `alpha` (commonly 0.05).

### 11. Common Tests

- t-test: compare means (one-sample or two-sample).
- chi-square test: categorical association.
- ANOVA: compare many group means.

Example with SciPy:
```python
from scipy import stats
stats.ttest_ind(a, b)
```

### 12. Errors and Power

- Type I error: reject H0 when it's true (false positive).
- Type II error: fail to reject H0 when it's false (false negative).
- Power = 1 - Type II error; larger sample size increases power.

---

## SECTION 5 — Correlation & Association

### 13. Correlation

- Pearson correlation: linear relation between two continuous variables.
- Spearman: rank-based, robust to monotonic non-linear relations.

Use `np.corrcoef` or `pd.DataFrame.corr()` to compute correlations.

### 14. Causality note

- Correlation ≠ causation. Use experiments or causal methods to claim causality.

---

## SECTION 6 — Regression Basics

### 15. Simple Linear Regression

Model: y = a + b*x + error. Fit with ordinary least squares (OLS).

Closed-form solution (normal equation):
```python
import numpy as np
X = np.column_stack([np.ones(len(x)), x])
w = np.linalg.pinv(X.T @ X) @ X.T @ y
```

### 16. Multiple Regression

- Include multiple features; interpret coefficients carefully (collinearity issues).
- Use libraries like `statsmodels` or `scikit-learn` for robust fitting and summaries.

### 17. Model Evaluation

- R-squared, adjusted R-squared for goodness of fit.
- RMSE, MAE for prediction error.

---

## SECTION 7 — Resampling & Robust Methods

### 18. Bootstrapping

- Resample with replacement to estimate sampling distribution of an estimator.
- Useful for confidence intervals without parametric assumptions.

Example quick bootstrap:
```python
def bootstrap_mean(x, n_boot=1000):
	import numpy as np
	means = [np.mean(np.random.choice(x, size=len(x), replace=True)) for _ in range(n_boot)]
	return np.percentile(means, [2.5, 97.5])
```

### 19. Cross-validation

- Split data into folds to measure model generalization (k-fold CV).

---

## SECTION 8 — Experimental Design & A/B Testing

### 20. Randomized Experiments

- Randomly assign units to control/treatment to infer causal effect.

### 21. A/B Testing Basics

- Define metric, choose sample size, run test, and compute p-value or confidence interval for difference.

---

## SECTION 9 — Bayesian Intro (Short)

- Bayesian view: combine prior beliefs with data (likelihood) to get posterior.
- Useful for small-data regimes and to express uncertainty directly.

Example libraries: `pymc`, `numpyro` for Bayesian models.

---

## SECTION 10 — Metrics for ML

- Classification: accuracy, precision, recall, F1, ROC-AUC.
- Regression: RMSE, MAE, R2.
- Clustering: silhouette score, adjusted rand index.

Use scikit-learn `metrics` module for implementations.

---

## SECTION 11 — Practical Tips

- Visualize data first: histograms, boxplots, scatter plots.
- Check assumptions before using parametric tests.
- Log-transform skewed data when appropriate.
- Scale features for many models (standardize or normalize).

---

## SECTION 12 — Mini Projects & Exercises

Beginner:
- Compute summary stats and plots for a CSV dataset.
- Implement a bootstrap CI for the mean.

Intermediate:
- Build and evaluate a linear regression model with train/test split.
- Run an A/B test simulation and analyze results.

AI-focused:
- Evaluate classifier metrics on imbalanced data and tune thresholds.
- Implement cross-validation for a small model and compare metrics.

---

## SECTION 13 — Cheatsheet

Common functions and commands:
```python
np.mean, np.median, np.std, np.percentile
from scipy import stats
pd.DataFrame.describe(), df.groupby(), df.sample()
```

Key ideas: variation, uncertainty, sampling, testing, and model evaluation.

---

## Next steps (suggested)

- Add hands-on exercises with small CSVs and test scripts.
- Create one runnable mini-project (regression or bootstrap demo).

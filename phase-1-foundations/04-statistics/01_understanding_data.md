# Understanding Data

> Statistics begins with understanding data.
>
> Before we can build models, make predictions, or draw conclusions, we must first understand what our data represents.

---

# Why This Matters

Imagine you are given a dataset containing:

| Student | Marks |
|----------|--------|
| A | 85 |
| B | 92 |
| C | 67 |
| D | 78 |

Before doing any calculations, we should ask:

- What do these numbers represent?
- Are there missing values?
- Are there unusual values?
- Is the dataset representative?

Statistics starts by answering these questions.

---

# Data and Variables

A variable is a characteristic that can take different values.

Examples:

- Age
- Height
- Salary
- Gender
- Marks

---

## Numerical Variables

Represent numbers.

Examples:

- Age = 21
- Salary = ₹50,000
- Temperature = 30°C

Used for mathematical calculations.

---

## Categorical Variables

Represent labels or groups.

Examples:

- Male / Female
- Red / Blue / Green
- India / Germany / Japan

These describe categories rather than quantities.

---

# Continuous vs Discrete Data

## Continuous Data

Can take any value within a range.

Examples:

- Height = 175.4 cm
- Weight = 68.75 kg
- Temperature = 29.6°C

---

## Discrete Data

Countable values.

Examples:

- Number of students
- Number of cars
- Number of books

You cannot have:

- 2.7 students
- 4.3 cars

---

# Population vs Sample

## Population

The entire group you want to study.

Example:

All engineering students in India.

---

## Sample

A smaller subset selected from the population.

Example:

1000 engineering students selected for a survey.

---

Why use samples?

Studying an entire population is often:

- Expensive
- Time-consuming
- Difficult

Instead, we study a sample and draw conclusions.

---

# Sampling Methods

## Random Sampling

Every member has an equal chance of being selected.

Example:

Randomly selecting 100 students from a university.

---

## Stratified Sampling

Divide population into groups and sample from each.

Example:

Select students from:

- 1st Year
- 2nd Year
- 3rd Year
- 4th Year

This ensures representation.

---

## Sampling Bias

Occurs when some groups are unfairly represented.

Example:

Surveying only students from one college and claiming it represents all students.

This leads to misleading conclusions.

---

# Descriptive Statistics

Descriptive statistics summarize data.

Instead of reading thousands of values, we use a few numbers.

---

# Mean

The average.

Formula:

Mean = Sum of values / Number of values

Example:

10, 20, 30

Mean = (10 + 20 + 30) / 3 = 20

---

# Median

Middle value after sorting.

Example:

10, 20, 30, 40, 50

Median = 30

---

Why median matters:

Income data often contains extremely rich individuals.

Median usually gives a better picture than average.

---

# Mode

Most frequent value.

Example:

1, 2, 2, 2, 3

Mode = 2

Useful for categorical data.

---

# Variance

Measures how spread out the data is.

Low variance:

10, 11, 10, 12

High variance:

1, 50, 100, 200

---

# Standard Deviation

Square root of variance.

Most commonly used measure of spread.

Small standard deviation:

Values are close together.

Large standard deviation:

Values are spread out.

---

# Percentiles

Show relative position.

Example:

90th percentile means you performed better than 90% of people.

Used in:

- JEE
- CAT
- GRE

---

# Quartiles

Divide data into four equal parts.

- Q1 = 25%
- Q2 = 50% (Median)
- Q3 = 75%

Useful for understanding spread.

---

# Data Distributions

A distribution shows how data is spread.

---

## Symmetric Distribution

Looks balanced.

Example:

Normal distribution.

```
        *
      *   *
    *       *
      *   *
        *
```

Mean ≈ Median

---

## Right Skewed Distribution

Long tail on the right.

Example:

Income distribution.

A few very rich individuals pull the average upward.

Mean > Median

---

## Left Skewed Distribution

Long tail on the left.

Example:

Easy exams where most students score high.

Mean < Median

---

# Outliers

Outliers are unusual observations.

Example:

70, 72, 75, 71, 250

250 is an outlier.

---

Possible causes:

- Data entry mistakes
- Measurement errors
- Rare events

---

Why outliers matter:

They can distort averages and affect ML models.

---

# Exploratory Data Analysis (EDA)

EDA means exploring data before modeling.

Questions:

- How many rows?
- Missing values?
- Outliers?
- Data types?
- Distributions?

---

Common Pandas Commands

```python
df.head()

df.info()

df.describe()

df.isnull().sum()
```

---

# Statistics in AI/ML

Statistics helps us:

- Understand datasets
- Detect problems
- Remove noise
- Identify outliers
- Improve data quality

Remember:

Good Data > Fancy Algorithms

A simple model with clean data often beats a complex model with poor data.

---

# Key Takeaways

1. Data is the foundation of statistics.
2. Variables can be numerical or categorical.
3. Data can be continuous or discrete.
4. Samples are used to study populations.
5. Mean, median, and mode summarize data.
6. Variance and standard deviation measure spread.
7. Distributions reveal patterns.
8. Outliers require attention.
9. EDA is the first step in every ML project.
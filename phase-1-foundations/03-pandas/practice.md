# Pandas Complete Guide

> Pandas is the most important library for data manipulation and analysis in Python.
>
> If NumPy provides powerful arrays, Pandas provides tools to work with real-world data such as CSV files, Excel sheets, databases, and machine learning datasets.

---

# 1. Introduction to Pandas

Pandas is an open-source Python library used for:

* Data Analysis
* Data Cleaning
* Data Transformation
* Data Exploration
* Feature Engineering

In Machine Learning, most of your time is spent preparing data rather than building models.

Pandas makes this process easier.

---

# Why Pandas?

Imagine a CSV file:

| Name  | Age | Salary |
| ----- | --- | ------ |
| Suraj | 21  | 50000  |
| Rahul | 22  | 60000  |

Without Pandas:

* Reading files is difficult
* Filtering data is tedious
* Cleaning data is slow

With Pandas:

```python
import pandas as pd

df = pd.read_csv("employees.csv")
```

Done.

---

# 2. Installing Pandas

```bash
pip install pandas
```

Import:

```python
import pandas as pd
```

Convention:

```python
pd
```

is used worldwide.

---

# 3. Series

A Series is a one-dimensional labeled array.

Think of it as a single column.

Example:

```python
import pandas as pd

s = pd.Series([10,20,30,40])

print(s)
```

Output:

```text
0    10
1    20
2    30
3    40
```

---

## Access Elements

```python
s[0]
```

Output:

```text
10
```

---

## Useful Operations

```python
s.mean()

s.max()

s.min()

s.sum()
```

---

# 4. DataFrames

A DataFrame is a table.

It consists of:

* Rows
* Columns

Example:

```python
data = {
    "Name":["Suraj","Rahul","Priya"],
    "Age":[21,22,20]
}

df = pd.DataFrame(data)

print(df)
```

Output:

```text
    Name   Age
0  Suraj   21
1  Rahul   22
2  Priya   20
```

---

# Understanding Index

```text
0
1
2
```

These numbers are called indexes.

They uniquely identify rows.

---

# 5. Reading Data

## CSV

```python
df = pd.read_csv("data.csv")
```

---

## Excel

```python
df = pd.read_excel("data.xlsx")
```

---

## JSON

```python
df = pd.read_json("data.json")
```

---

# 6. Exploring Data

Whenever you load a dataset, start here.

---

## head()

Shows first 5 rows.

```python
df.head()
```

---

## tail()

Shows last 5 rows.

```python
df.tail()
```

---

## shape

Returns:

```python
df.shape
```

Example:

```text
(1000,5)
```

Meaning:

* 1000 rows
* 5 columns

---

## columns

```python
df.columns
```

---

## dtypes

Shows data types.

```python
df.dtypes
```

---

## info()

Most important inspection method.

```python
df.info()
```

Shows:

* Rows
* Columns
* Missing values
* Data types

---

## describe()

Statistical summary.

```python
df.describe()
```

Shows:

* Mean
* Std
* Min
* Max
* Quartiles

---

# 7. Selecting Data

---

## Single Column

```python
df["Age"]
```

---

## Multiple Columns

```python
df[["Name","Age"]]
```

---

## Select Row Using loc

```python
df.loc[0]
```

First row.

---

## Select Row Using iloc

```python
df.iloc[0]
```

Also first row.

---

Difference:

loc → label based

iloc → position based

---

# 8. Filtering Data

One of the most used Pandas operations.

---

## Single Condition

```python
df[df["Age"] > 21]
```

---

## Multiple Conditions

```python
df[
    (df["Age"] > 21)
    &
    (df["Salary"] > 50000)
]
```

---

## isin()

```python
df[
    df["City"].isin(["Mysuru","Bengaluru"])
]
```

---

## between()

```python
df[
    df["Age"].between(20,25)
]
```

---

# 9. Adding and Modifying Columns

---

## New Column

```python
df["Bonus"] = 5000
```

---

## Derived Column

```python
df["AnnualSalary"] = df["Salary"] * 12
```

---

## Update Values

```python
df["Age"] = df["Age"] + 1
```

---

# 10. Handling Missing Values

Missing values are extremely common.

---

## Check Missing Values

```python
df.isnull()
```

---

## Count Missing Values

```python
df.isnull().sum()
```

---

## Remove Missing Rows

```python
df.dropna()
```

---

## Fill Missing Values

```python
df.fillna(0)
```

---

Fill with mean:

```python
df["Age"].fillna(
    df["Age"].mean()
)
```

---

# 11. Sorting Data

---

## Ascending

```python
df.sort_values("Salary")
```

---

## Descending

```python
df.sort_values(
    "Salary",
    ascending=False
)
```

---

# 12. GroupBy Operations

One of Pandas' most powerful features.

Suppose:

| Department | Salary |
| ---------- | ------ |
| IT         | 50000  |
| IT         | 60000  |
| HR         | 40000  |

Find average salary per department.

```python
df.groupby("Department")["Salary"].mean()
```

---

# 13. Aggregation Functions

---

## Mean

```python
df["Salary"].mean()
```

---

## Sum

```python
df["Salary"].sum()
```

---

## Count

```python
df["Salary"].count()
```

---

## Maximum

```python
df["Salary"].max()
```

---

## Minimum

```python
df["Salary"].min()
```

---

## Standard Deviation

```python
df["Salary"].std()
```

---

# 14. Working With Strings

---

## Lowercase

```python
df["Name"].str.lower()
```

---

## Uppercase

```python
df["Name"].str.upper()
```

---

## Contains

```python
df[
    df["Name"].str.contains("a")
]
```

---

## Replace

```python
df["Name"].str.replace(
    "Rahul",
    "Rohan"
)
```

---

# 15. Working With Dates

---

Convert to datetime:

```python
df["Date"] = pd.to_datetime(
    df["Date"]
)
```

---

Extract year:

```python
df["Date"].dt.year
```

---

Extract month:

```python
df["Date"].dt.month
```

---

Extract day:

```python
df["Date"].dt.day
```

---

# 16. Combining DataFrames

---

## Concat

```python
pd.concat([df1,df2])
```

Stacks DataFrames.

---

## Merge

Most important join operation.

```python
pd.merge(
    df1,
    df2,
    on="ID"
)
```

Similar to SQL JOIN.

---

# 17. Pivot Tables

Convert raw data into summaries.

```python
df.pivot_table(
    values="Salary",
    index="Department",
    aggfunc="mean"
)
```

Output:

```text
Department
HR     40000
IT     55000
```

---

# 18. Duplicates

---

## Find Duplicates

```python
df.duplicated()
```

---

## Remove Duplicates

```python
df.drop_duplicates()
```

---

# 19. Apply Functions

Useful for custom transformations.

---

Example:

```python
def double(x):
    return x * 2

df["Salary"].apply(double)
```

---

Using lambda:

```python
df["Salary"].apply(
    lambda x: x * 2
)
```

---

# 20. Pandas Workflow for Machine Learning

Most ML projects follow this pattern:

---

Step 1

Load Data

```python
pd.read_csv()
```

---

Step 2

Inspect Data

```python
head()
info()
describe()
```

---

Step 3

Handle Missing Values

```python
fillna()
dropna()
```

---

Step 4

Remove Duplicates

```python
drop_duplicates()
```

---

Step 5

Feature Engineering

Create useful columns.

---

Step 6

Filtering and Analysis

Understand patterns.

---

Step 7

Prepare Dataset

Ready for model training.

---

# Example Mini Project

Dataset:

Employees

| Name | Salary |
| ---- | ------ |
| A    | 50000  |
| B    | 60000  |
| C    | 70000  |

Average Salary:

```python
df["Salary"].mean()
```

Highest Salary:

```python
df["Salary"].max()
```

Employees above 55000:

```python
df[
    df["Salary"] > 55000
]
```

---

# Common Interview Questions

### Difference Between loc and iloc?

loc:

Label-based indexing.

iloc:

Position-based indexing.

---

### Difference Between merge and concat?

merge:

Combines using common columns.

concat:

Stacks DataFrames.

---

### What does groupby do?

Splits data into groups and performs calculations.

---

### What is a DataFrame?

A two-dimensional table consisting of rows and columns.

---

# Pandas Cheat Sheet

Load CSV:

```python
pd.read_csv()
```

First Rows:

```python
df.head()
```

Info:

```python
df.info()
```

Statistics:

```python
df.describe()
```

Select Column:

```python
df["column"]
```

Filter:

```python
df[df["Age"] > 20]
```

Missing Values:

```python
df.isnull().sum()
```

Fill Missing:

```python
df.fillna()
```

Group Data:

```python
df.groupby()
```

Sort:

```python
df.sort_values()
```

Merge:

```python
pd.merge()
```

Apply Function:

```python
df.apply()
```

---

# Final Thoughts

Pandas is the backbone of data analysis in Python.

For AI and Machine Learning projects, your workflow is usually:

Data → Pandas → Cleaning → Feature Engineering → Model Training

Mastering Pandas will make every Data Science and AI project significantly easier.

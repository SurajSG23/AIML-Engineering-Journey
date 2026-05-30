# Pandas Practice

## Overview
Short, practical Pandas notes for AI engineering. Clear explanations, short examples, and useful tips for working with tabular data.

---

## 1. Introduction to Pandas

- What is Pandas: a Python library for working with tables (rows and columns).
- Main objects: `DataFrame` (table) and `Series` (single column).
- Why Pandas: easy data cleaning, fast prototyping, and seamless use with NumPy and ML libraries.
- Real-world uses: data cleaning, feature engineering, reporting, and exploratory data analysis.

---

## SECTION 1 — Basics

### 2. Core Objects

`Series`: 1D labeled array. `DataFrame`: 2D table with rows and columns.

Create examples:
```python
import pandas as pd
s = pd.Series([1,2,3], name='count')
df = pd.DataFrame({'a':[1,2], 'b':[3,4]})
```

Check shape and types:
```python
df.shape
df.dtypes
```

---

### 3. Reading & Writing Data

Read CSV, Excel, JSON, SQL, and more:
```python
df = pd.read_csv('data.csv')
df.to_csv('out.csv', index=False)
```

Tips: specify `dtype`, `parse_dates`, and `usecols` for speed.

---

## SECTION 2 — Indexing & Selection

### 4. Column and Row Access

- Select column: `df['col']` or `df.col`.
- Select rows by position: `df.iloc[0]`.
- Select rows by label: `df.loc['row_label']`.
- Slice rows: `df.iloc[0:5]`.

Example:
```python
df.loc[ df['age'] > 30, ['name', 'age'] ]
```

---

### 5. Boolean Indexing & Masks

Use conditions to filter rows:
```python
mask = (df['score'] >= 80) & (df['passed'] == True)
df[mask]
```

Use `between`, `isin`, `str.contains` for convenience.

---

## SECTION 3 — Cleaning Data

### 6. Missing Values

Detect and handle missing data:
```python
df.isna().sum()
df.dropna()
df.fillna(0)
```

Decide per-column strategy: drop, fill with mean, or keep flag column.

---

### 7. Data Types & Conversion

Check and convert dtypes:
```python
df['date'] = pd.to_datetime(df['date'])
df['id'] = df['id'].astype('int')
```

Use `category` dtype for repeated strings to save memory.

---

## SECTION 4 — Transformations

### 8. Adding & Modifying Columns

Create new columns or change existing ones:
```python
df['total'] = df['a'] + df['b']
df['year'] = df['date'].dt.year
```

### 9. Apply / Map

Use `apply`, `map`, or vectorized functions. Prefer vectorized/NumPy ops for speed.
```python
df['len_name'] = df['name'].str.len()
```

---

### 10. GroupBy and Aggregation

Group rows and compute summaries:
```python
df.groupby('city')['salary'].mean()
df.groupby(['dept','role']).agg({'salary':'mean','id':'count'})
```

Use `transform` to add aggregated values back to rows.

---

## SECTION 5 — Joins & Reshaping

### 11. Merge / Join

Combine tables like SQL:
```python
pd.merge(left, right, on='id', how='inner')
```

Options: `how='left'|'right'|'outer'|'inner'`.

### 12. Concatenation & Reshape

Stack or split tables:
```python
pd.concat([df1, df2], axis=0)
df.pivot_table(index='id', columns='type', values='value')
df.melt(id_vars=['id'], value_vars=['a','b'])
```

---

## SECTION 6 — Time Series

### 13. Datetime Handling

Convert and use datetime index:
```python
df['date'] = pd.to_datetime(df['date'])
df.set_index('date', inplace=True)
df.resample('M').sum()
```

Use rolling windows: `df['x'].rolling(7).mean()`.

---

## SECTION 7 — Performance & Memory

### 14. Speed Tips

- Use `dtype` hints on read.
- Avoid `apply()` where possible; use vectorized ops.
- Use `query()` for readable filtering.
- Use `chunksize` to read large files in pieces.

### 15. Memory Tips

- Convert object columns with few unique values to `category`.
- Downcast numeric types with `pd.to_numeric(..., downcast='integer')`.

---

## SECTION 8 — Useful Functions

- `df.head()`, `df.tail()`, `df.info()`, `df.describe()`
- `df.sample()`, `df.sort_values()`
- `df.to_csv()`, `pd.read_excel()`

---

## SECTION 9 — Common Pitfalls

- Chained assignment warning: `df['a'][mask] = val` (use `.loc[]`).
- Mixing indices: explicit `reset_index()` when needed.
- Unintended copies vs views: use `.copy()` when required.

---

## SECTION 10 — Mini Projects & Exercises

Beginner projects:
- CSV analyzer: load CSV, show missing values, and basic stats.
- Simple data cleaner: fill missing, convert dtypes, export clean CSV.

Intermediate projects:
- Sales dashboard dataset: aggregate sales by region and time.
- Feature builder: take raw CSV and build `X` and `y` for ML.

AI-focused projects:
- Time-series prep: resample and create lag features.
- Small ETL pipeline: read raw files, clean, save to cleaned folder.

Example quick task:
```python
df = pd.read_csv('data.csv')
df_clean = df.dropna(subset=['target']).copy()
df_clean['target_norm'] = (df_clean['target'] - df_clean['target'].mean())/df_clean['target'].std()
```

---

## SECTION 11 — Pandas in AI Workflows

- Use Pandas for data exploration, cleaning, and feature engineering before feeding arrays to ML libraries.
- Combine Pandas with NumPy and Scikit-learn pipelines.

---

## SECTION 12 — Cheatsheet

Key methods/examples:
```python
pd.read_csv, df.head, df.info, df.describe
df.groupby, pd.merge, df.pivot_table, df.melt
df.to_csv, pd.to_datetime, df.resample
```

Key ideas: DataFrame, Series, indexing, grouping, joins, missing data, time handling.

---

# Unsupervised Learning

> In Supervised Learning, we learn from examples that already have answers.
>
> In Unsupervised Learning, there are **no answers provided**.
>
> The algorithm must discover patterns, groups, structures, or relationships on its own.
>
> This makes Unsupervised Learning one of the most fascinating areas of Machine Learning.

---

# What is Unsupervised Learning?

In Unsupervised Learning:

```text
Input Data → Available

Correct Answers → Not Available
```

The algorithm receives only data and tries to find hidden patterns.

---

# Supervised vs Unsupervised Learning

## Supervised Learning

Dataset:

| Hours Studied | Pass |
| ------------- | ---- |
| 2             | No   |
| 4             | No   |
| 6             | Yes  |
| 8             | Yes  |

Notice:

```text
Pass / Fail
```

already exists.

This is called a:

```text
Label
```

---

## Unsupervised Learning

Dataset:

| Age | Salary |
| --- | ------ |
| 22  | 30000  |
| 25  | 35000  |
| 45  | 90000  |
| 50  | 100000 |

No label exists.

The algorithm must discover patterns itself.

---

# Why Do We Need Unsupervised Learning?

Real-world data often looks like:

```text
Millions of Customers

Millions of Transactions

Millions of Images
```

Most of this data has:

```text
No Labels
```

Labeling data is expensive and time-consuming.

Unsupervised Learning helps us extract value from unlabeled data.

---

# Main Goals of Unsupervised Learning

Usually we want to:

```text
Find Groups

Find Patterns

Reduce Complexity

Detect Anomalies
```

These lead to four major tasks:

1. Clustering
2. Dimensionality Reduction
3. Association Rule Learning
4. Anomaly Detection

---

# Clustering

The most common unsupervised learning task.

Goal:

```text
Group similar data points together.
```

Example:

Customer Data

```text
Customer A
Customer B
Customer C
Customer D
```

The algorithm might discover:

```text
Young Customers

Middle-aged Customers

High Income Customers
```

without being told these groups exist.

---

# Real-Life Example

Suppose an online store has customer data:

| Age | Salary |
| --- | ------ |
| 22  | 30000  |
| 23  | 32000  |
| 45  | 90000  |
| 50  | 95000  |

The algorithm might discover:

Cluster 1:

```text
Young Customers
```

Cluster 2:

```text
High Income Customers
```

No labels were provided.

The model discovered them automatically.

---

# What is a Cluster?

A cluster is:

```text
A group of similar data points.
```

Example:

```text
● ● ●

      ▲ ▲ ▲

             ■ ■ ■
```

Three natural groups exist.

Each group is a cluster.

---

# K-Means Clustering

The most popular clustering algorithm.

---

# Goal of K-Means

Given data:

```text
● ● ● ● ● ▲ ▲ ▲ ▲ ▲
```

Find natural groups.

---

# What Does K Mean?

K represents:

```text
Number of Clusters
```

Example:

```text
K = 3
```

means:

```text
Create 3 groups.
```

---

# How K-Means Works

Step 1:

Choose K.

Example:

```text
K = 3
```

---

Step 2:

Randomly place cluster centers.

---

Step 3:

Assign each point to nearest center.

---

Step 4:

Move centers to the average location.

---

Step 5:

Repeat until centers stop moving.

---

# Simple Visualization

Initial:

```text
● ● ●     X

▲ ▲ ▲     X

■ ■ ■     X
```

---

After several iterations:

```text
● ● ●  X

▲ ▲ ▲      X

■ ■ ■          X
```

Clusters become stable.

---

# Why K-Means Works

Similar points tend to stay together.

Over time:

```text
Nearby points
↓
Same cluster
```

---

# Choosing K

A common question:

```text
How many clusters should we create?
```

Example:

```text
K = 2

K = 3

K = 5
```

Different values produce different results.

---

# Elbow Method

A popular technique.

Idea:

```text
Try different K values
```

Measure clustering quality.

Find the point where improvement slows down.

This point often looks like an elbow.

---

# Applications of Clustering

---

## Customer Segmentation

Group customers by behavior.

Example:

```text
Students

Professionals

Business Owners
```

---

## Recommendation Systems

Group users with similar interests.

---

## Social Network Analysis

Identify communities.

---

## Image Segmentation

Group similar pixels.

---

## Market Research

Identify customer categories.

---

# Advantages of K-Means

* Easy to understand
* Fast
* Scales well
* Widely used

---

# Limitations of K-Means

* Need to choose K
* Sensitive to outliers
* Assumes spherical clusters
* Different random starts may produce different results

---

# Hierarchical Clustering

Another clustering technique.

Instead of creating clusters immediately:

```text
Build a hierarchy of groups.
```

---

# How It Works

Initially:

```text
A
B
C
D
```

Each point is its own cluster.

---

Gradually merge:

```text
(A B)

(C D)
```

Then:

```text
((A B) (C D))
```

until everything is connected.

---

# Dendrogram

Hierarchical Clustering produces a tree-like structure.

Called:

```text
Dendrogram
```

Example:

```text
       -----
      |     |
   ---      ---
  |  |      |  |
  A  B      C  D
```

Shows how clusters are formed.

---

# Dimensionality Reduction

Another major area of Unsupervised Learning.

---

# Why Reduce Dimensions?

Imagine:

```text
100 Features

500 Features

1000 Features
```

Working with so many features becomes difficult.

Problems:

* Slower training
* More memory
* Hard visualization

---

Goal:

```text
Keep important information

Remove unnecessary information
```

---

# Principal Component Analysis (PCA)

The most popular dimensionality reduction technique.

---

# What PCA Does

Suppose dataset has:

```text
100 Features
```

PCA may reduce it to:

```text
10 Features
```

while preserving most information.

---

Think:

```text
Large File
↓
Compressed File
```

Information is mostly retained.

---

# Benefits of PCA

* Faster training
* Reduced storage
* Better visualization
* Less noise

---

# Example

Original:

```text
100 Features
```

After PCA:

```text
10 Features
```

Model becomes faster.

---

# Anomaly Detection

Another important unsupervised task.

Goal:

```text
Find unusual data points.
```

---

# What is an Anomaly?

A point that looks very different from others.

Example:

```text
10
11
12
13
14
500
```

Value:

```text
500
```

looks suspicious.

---

# Applications

---

## Fraud Detection

Most transactions:

```text
Normal
```

One transaction:

```text
₹10,00,000
```

Potential fraud.

---

## Cybersecurity

Detect unusual login activity.

---

## Manufacturing

Detect faulty products.

---

## Healthcare

Detect abnormal patient readings.

---

# Association Rule Learning

Goal:

```text
Find relationships between items.
```

---

# Market Basket Analysis

Suppose customers buy:

```text
Bread
Butter
Milk
```

Frequently together.

Algorithm discovers:

```text
Bread → Butter
```

relationship.

---

Applications:

* Product recommendations
* Retail analysis
* E-commerce

---

# Unsupervised Learning Algorithms

Common algorithms:

| Algorithm               | Purpose                  |
| ----------------------- | ------------------------ |
| K-Means                 | Clustering               |
| Hierarchical Clustering | Clustering               |
| DBSCAN                  | Clustering               |
| PCA                     | Dimensionality Reduction |
| Isolation Forest        | Anomaly Detection        |
| Apriori                 | Association Rules        |

---

# Evaluating Unsupervised Learning

Harder than supervised learning.

Why?

Because:

```text
No Correct Answers Exist
```

---

Instead we evaluate:

* Cluster quality
* Compactness
* Separation
* Business usefulness

---

# Unsupervised Learning in AI

---

# Recommendation Systems

Group similar users.

---

# Customer Segmentation

Identify customer types.

---

# Fraud Detection

Find unusual transactions.

---

# Image Compression

Reduce image dimensions.

---

# NLP

Word embeddings often emerge from unsupervised learning.

---

# Example Workflow

Suppose an e-commerce company has:

```text
Age

Salary

Purchase Amount

Visits
```

but no labels.

---

Step 1:

Apply K-Means.

---

Step 2:

Discover customer groups.

---

Example:

```text
Cluster 1:
Students

Cluster 2:
Working Professionals

Cluster 3:
High-Value Customers
```

---

Step 3:

Use clusters for marketing.

---

# Supervised vs Unsupervised vs Reinforcement Learning

| Learning Type          | Labels Available? |
| ---------------------- | ----------------- |
| Supervised Learning    | Yes               |
| Unsupervised Learning  | No                |
| Reinforcement Learning | Rewards Only      |

---

Example:

Supervised:

```text
Spam / Not Spam
```

Known answers.

---

Unsupervised:

```text
Group similar emails
```

No answers.

---

Reinforcement Learning:

```text
Learn through rewards and penalties.
```

---

# Common Beginner Mistakes

---

## Thinking Clustering Finds Perfect Groups

Clusters are discovered patterns.

They may not always match human expectations.

---

## Assuming K-Means Always Works

Different datasets may require:

* DBSCAN
* Hierarchical Clustering
* Other algorithms

---

## Using Too Many Features

High-dimensional data can hurt clustering performance.

---

## Ignoring Feature Scaling

Distance-based algorithms need properly scaled data.

---

# Interview Questions

---

## What is Unsupervised Learning?

Learning from unlabeled data.

---

## What is Clustering?

Grouping similar data points together.

---

## What is K-Means?

A clustering algorithm that partitions data into K groups.

---

## What is PCA?

A dimensionality reduction technique.

---

## What is Anomaly Detection?

Finding unusual observations.

---

## Why is Unsupervised Learning Important?

Because most real-world data is unlabeled.

---

# Key Takeaways

1. Unsupervised Learning works with unlabeled data.
2. The algorithm discovers patterns automatically.
3. Clustering is the most common task.
4. K-Means is the most popular clustering algorithm.
5. PCA reduces dimensionality.
6. Anomaly Detection finds unusual observations.
7. Association Rules discover relationships between items.
8. Most real-world data is unlabeled.
9. Unsupervised Learning is heavily used in industry.
10. It helps extract knowledge from data without requiring labels.

---

# Final Mental Model

```text
Raw Data
    ↓
No Labels
    ↓
Find Hidden Patterns
    ↓
Clusters
Patterns
Anomalies
Relationships
    ↓
Useful Insights
```

Supervised Learning learns from answers.

Unsupervised Learning discovers answers that nobody explicitly provided.

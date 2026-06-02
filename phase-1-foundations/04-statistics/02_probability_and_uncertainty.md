# Probability and Uncertainty

> Probability is the language of uncertainty.
>
> Whenever we say:
>
> - "There is a 90% chance of rain."
> - "The model is 95% confident."
> - "This email is probably spam."
>
> We are using probability.

---

# Why Probability Exists

In many situations we cannot predict outcomes with certainty.

Example:

Will it rain tomorrow?

Nobody knows for sure.

But based on past information we can estimate likelihood.

That likelihood is probability.

---

# What is Probability?

Probability measures how likely an event is to occur.

Range:

0 → Impossible

1 → Certain

---

Examples:

P(Rain Tomorrow) = 0.7

Meaning:

70% chance of rain.

---

# Probability Formula

Probability = Favorable Outcomes / Total Outcomes

---

Example

Rolling a die.

What is probability of getting 3?

Favorable outcomes = 1

Total outcomes = 6

Probability = 1/6

---

# Conditional Probability

Probability of an event given another event already occurred.

Notation:

P(A | B)

Read:

Probability of A given B.

---

Example

Suppose:

- 100 students
- 60 are boys
- 30 boys play football

Question:

Probability a football player is a boy?

Conditional probability helps answer such questions.

---

# Independent Events

One event does not affect another.

Example:

Two coin tosses.

First toss outcome does not affect second toss.

---

# Dependent Events

One event affects another.

Example:

Drawing cards without replacement.

Removing one card changes future probabilities.

---

# Bayes Theorem

One of the most important ideas in AI.

Bayes helps update beliefs when new evidence arrives.

---

Example

A medical test is positive.

Question:

What is the probability the person actually has the disease?

Bayes helps answer this.

---

Conceptually:

Prior Belief

↓

New Evidence

↓

Updated Belief

---

This is how many AI systems reason.

---

# Random Variables

A variable whose value depends on a random process.

Examples:

- Dice outcome
- Number of customers arriving
- Daily stock returns

---

# Probability Distributions

A distribution describes possible outcomes and their probabilities.

---

# Bernoulli Distribution

Only two outcomes.

Examples:

- Yes / No
- Success / Failure
- Spam / Not Spam

---

# Binomial Distribution

Counts number of successes across multiple trials.

Example:

10 coin tosses.

How many heads?

---

# Uniform Distribution

Every outcome equally likely.

Example:

Fair die.

---

# Poisson Distribution

Counts events occurring over time.

Examples:

- Calls per hour
- Customers arriving
- Website visits

---

# Normal Distribution

Most important distribution.

Also called:

Bell Curve

```
          *
       *     *
     *         *
   *             *
```

Many natural phenomena follow it:

- Height
- Weight
- Exam scores

---

Properties

- Symmetric
- Mean = Median
- Bell-shaped

---

# Standard Normal Distribution

Special normal distribution with:

Mean = 0

Standard Deviation = 1

Used for statistical calculations.

---

# Z-Score

Measures how far a value is from the mean.

Formula:

Z = (Value - Mean) / Standard Deviation

---

Interpretation

Z = 0

Exactly at average.

---

Z = 2

Two standard deviations above average.

---

Z = -1

One standard deviation below average.

---

# Probability in AI/ML

---

## Spam Detection

Probability email is spam.

---

## Recommendation Systems

Probability user likes a movie.

---

## Fraud Detection

Probability transaction is fraudulent.

---

## Medical AI

Probability disease exists.

---

# Key Takeaways

1. Probability measures uncertainty.
2. Values range from 0 to 1.
3. Conditional probability incorporates additional information.
4. Bayes theorem updates beliefs using evidence.
5. Random variables model uncertain outcomes.
6. Distributions describe possible outcomes.
7. Normal distribution is extremely important.
8. Probability powers many AI systems.
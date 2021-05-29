---
title: Real Number Theory
date: 2019-1-31
tags: 
	- Calculus
	- Real Analysis
categories: 
	- Mathematics
	- Analysis
---
This note contains basic knowledge of Set, Some basic principles of the real number.

# Completeness of the Real Numbers

## Existence of supremum and infimum

### Upper Bound & Lower Bound

+ Upper Bound

Let $S$ be a nonempty set of real numbers. If $ \exists ~ M \in R$, such that $ \forall ~ x \in S$, $x \leq M $, then $M$ is called an **upper bound** for $S$, or $S$ has an upper bound. And $S$ is said to be *bounded above*. A set may have many upper bounds.

+ Lower Bound

Similarly, if $ \exists ~ m \in R$, such that $ \forall ~ x \in S$, $x \geq m $, then $m$ is called an **lower bound** for $S$, or $S$ has an lower bound. And $S$ is said to be *bounded below*. A set may have many upper bounds and lower bounds.

If a set $S$ has both upper bounds and lower bounds, then $S$ is called the **bounded set**. Evidently, it is equivalent to:
$$
\exists ~ X > 0, such ~ that ~ \forall ~ x \in S, |x| \leq X
$$

### Supremum & Infimum

- Supremum

Let $U$ be a set of upper bounds of $S$. Obviously it has no maximum element. And let the minimum of $U$ be $\beta$, then $\beta$ is called the least upper bound of $S$, which is also called the **supremum** of $S$. It is denoted as 
$$
\beta = sup ~ S
$$
There are two properties of supremum $\beta$

1. $\beta$ is an upper bound of $S$: $\forall  ~ x \in S$, $x \leq \beta$.

2. Any number that is less than $\beta$ is not the upper bound of $S$: $\forall ~ \varepsilon > 0$, $\exists ~ x \in S$, such that $x > \beta - \varepsilon$.

- Infimum

Similarly, let $L$ be a set of upper bounds of $S$. Obviously it has no minimum element. And let the maximum of $L$ be $\alpha$, then $\alpha$ is called the greatest lower bound of $S$, which is also called the **infimum** of $S$. It is denoted as
$$
\alpha = inf ~ S
$$
There are also two properties of infimum $\alpha$

1. $\alpha$ is an lower bound of $S$: $\forall  ~ x \in S$, $x \geq \alpha$.

2. Any number that is greater than $\alpha$ is not the lower bound of $S$: $\forall ~ \varepsilon > 0$, $\exists ~ x \in S$, such that $x < \alpha + \varepsilon$.

###  Supremum and Infimum Theorem

+ A nonempty set of real numbers that's bounded above has supremum.
+ A nonempty set of real numbers that's bounded below has infimum.

This theorem, which is crucial for establishing many of the important theorems of calculus and real analysis, is one of the basic theorems of the real number system.
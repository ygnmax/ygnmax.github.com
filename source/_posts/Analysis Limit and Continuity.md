---
title: Limit and Continuity
date: 2019-1-31
tags: 
	- Calculus
	- Real Analysis
categories: 
	- Mathematics
	- Analysis
	- Real Analysis
---
This note contains basic knowledge of Limit and Continuity.

# Limits of Sequences

## Definition

A sequence is an infinite or finite ordered list of terms base on the positive number index:
$$
x_1, x_2,...,x_n,...
$$
It is usually denoted as $\{x_n\}$, and $x_n$ is called the general term. And the **limits of sequences** can be rigorously defined as this:

Let $\{ x_n \}$ is a given sequence, $a$ is a constant. If $\forall $ given $\varepsilon > 0$, $\exists$ a positive integer $N$, such that when $n > N$ there is 
$$
|x_n - a|<\varepsilon
$$
then we call sequence $\{ x_n \}$ is **convergent** and converges to $a$, or $a$ is the **limit** of  sequence $\{ x_n \}$, denoted as
$$
\lim_{n \to \infty}x_n=a
$$
or
$$
x_n \to a ~(x \to \infty)
$$
If there does not exist a real number $a$ such that $\{ x_n \}$ converges to $a$, then the sequence is said to be **divergent**. 

Similarly, We can define the neighborhood as this:

For a point $a$ which is on the x-axis of the Cartesian Coordinates, the interval $(a-\varepsilon, a+\varepsilon)$ is called as the $\varepsilon$ **neighborhood** of point $a$, denoted as $O(a,\varepsilon)$:
$$
O(a,\varepsilon) = \{x|a - \varepsilon < x < a+\varepsilon\} 
$$
Whether a sequence is convergent or divergent has nothing to do with the finite terms, because if a sequence is convergent, "when $n > N$, there is $|x_n-a|<\varepsilon$" means that all the terms from the $N+1$ order will be in the $\varepsilon$ neighborhood, that is to say $x_n \in O(a, \varepsilon), n > N$.

Among the convergent sequences, the one whose limit is 0 is called **infinitesimals**.

## Properties

### Uniqueness

The limit of a convergent sequence is unique.
$$
\text{if}
\lim_{n \to \infty}x_n=a \\
\lim_{n \to \infty}x_n=b \\
\text{then} \
a = b
$$

### Boundedness

A convergent sequence must be bounded.

### Squeeze Theorem

For 3 sequence $\{x_n\}$,  $\{y_n\}$,  $\{z_n\}$ from a certain term there is
$$
x_n \leq y_n \leq z_n, n \ge N_0
$$
and $\lim_{n \to \infty} x_n = \lim_{n \to \infty} z_n = a$, then
$$
\lim_{n \to \infty}y_n = a
$$

### Arithmetic

If $\lim_{n \to \infty}x_n=a$, $\lim_{n \to \infty}y_n=b$, then
$$
\begin{align*}
&\lim_{n \to \infty}(\alpha x_n+\beta y_n)=\alpha a+\beta b \\
&\lim_{n \to \infty}(x_ny_n)=ab \\
&\lim_{n \to \infty}\frac{x_n}{y_n}=\frac{a}{b}
\end{align*}
$$

# Infinity

## Definition

For any given $G>0$, if $\exist$ positive integer $N$ such that when $n>N$, $|x_n|>G$, then call $\{x_n\}$ the infinity, denote as
$$
\lim_{n \to \infty}x_n=\infty
$$
It can be $\lim_{n \to \infty}a_n=+\infty$ or $\lim_{n \to \infty}b_n=-\infty$.


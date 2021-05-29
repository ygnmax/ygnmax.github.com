---
title: Law of Large Numbers
date: 2020-3-11
tags: 
	- Probability
	- Statistics
	- Stochastic
categories: 
	- Mathematics
	- Statistics
	- Classic Statistics
mathjax: true
---
# Lemma: Chebyshev Inequality

For $E(X) = \mu$ and $D(x) = \sigma^2$, then
$$
p\{| X-\mu| \geq \epsilon \} \leq\frac{\sigma^2}{\epsilon^2}
$$
Proof:
$$
\begin{eqnarray*}p\{| X-\mu| \geq \epsilon \} &=& \int_{|x-\mu|\geq\epsilon}f(x)dx \\&\leq& \int_{|x-\mu|\geq\epsilon} \frac{|x-\mu|^2}{\epsilon^2} f(x)dx \\&\leq& \frac{1}{\epsilon^2}\int_{-\infty}^{\infty} (x-\mu)^2 f(x)dx \\&=& \frac{\sigma^2}{\epsilon^2}\end{eqnarray*}
$$
which also implies
$$
p\{| X-\mu| < \epsilon \} \geq 1- \frac{\sigma^2}{\epsilon^2}
$$

# Law of Large Numbers

## Khinchin LLN

For infinite independent random variable $X_1, X_2, ...$, which are from the identical distribution with the expectation $E(x_k) = \mu$, then for $\forall ~ \epsilon$
$$
\lim_{n \to \infty}P\left\{ \left| \frac{1}{n}\sum_{k=1}^{n}X_k-\mu \right| <\epsilon\right\} = 1
$$
When the $n$ is close to positive infinity, $\frac{1}{n}\sum_{k=1}^{n}X_k$ is close to $\mu$, which is the expectation of $X$ 

Proof:

Assume the variance exist $D(X) = \sigma^2$, then
$$
\begin{eqnarray*}
E\left(\frac{1}{n}\sum_{k=1}^nX_k\right) 
&=& \frac{1}{n}\sum_{k=1}^nE(X_k) \\
&=& \frac{1}{n}\times n\mu \\
&=& \mu
\end{eqnarray*}
$$

$$
\begin{eqnarray*}
D\left(\frac{1}{n}\sum_{k=1}^nX_k\right) 
&=& \frac{1}{n^2}\sum_{k=1}^nD(X_k) \\
&=& \frac{1}{n^2}\times n\sigma^2 \\
&=& \frac{\sigma^2}{n}
\end{eqnarray*}
$$

use the Chebyshev Inequity:
$$
\begin{eqnarray*}
1 \geq  P\left\{ \left| \frac{1}{n}\sum_{k=1}^{n}X_k-\mu \right| <\epsilon\right\} \geq 
1-\frac{\frac{\sigma^2}{n}}{\epsilon^2}
\end{eqnarray*}
$$
when $n\to\infty$, then we can draw the conclusion.

## Bernoulli LLN

Assume that $f_A$ is the frequency of event $A$ happening in $n$ times independent repeated experiment,  and $p$ is the probability of event $A$ happening in each experiment, then for $\forall ~ \epsilon> 0$
$$
\lim_{n \to \infty}P\left\{ \left| \frac{f_A}{n}-p \right| <\epsilon\right\} = 1
$$
Proof:

From the Khinchin LLN




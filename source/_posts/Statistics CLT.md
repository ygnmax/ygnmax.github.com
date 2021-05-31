---
title: Central Limit Theorem
date: 2020-3-11
tags: 
	- Probability
	- Statistics
	- Stochastic
categories: 
	- Mathematics
	- Probability
	- Classic Statistics
mathjax: true
---
# Central Limit Theorem

## IID CLT

For infinite independent random variable $X_1, X_2, ...X_n, ...$, which are from the identical distribution with the expectation $E(X_k) = \mu$, and variance $D(X_k) = \sigma^2$, then for $\forall ~ x$
$$
\lim_{n \to \infty} F_n(x)=\lim_{n \to \infty} P\left\{ \frac{\sum\limits_{k=1}^{n}X_k-n\mu}{\sqrt{n}\sigma} \leq x \right\} = \Phi(x)
$$
where  $F_n(x)$ is the distribution function of $\frac{\sum\limits_{k=1}^{n}X_k-n\mu}{\sqrt{n}\sigma}$.

+ The CLT implies that large iid experiment usually follows the normal distribution

+ $$
  \begin{eqnarray*}
  \sum\limits_{k=1}^{n}X_k \sim N(n\mu, n\sigma^2) \\
  \frac{1}{n}\sum\limits_{k=1}^{n}X_k \sim N(\mu, \frac{\sigma^2}{n})
  \end{eqnarray*}
  $$

+ Here, the sum of random variable $\sum\limits_{k=1}^{n}X_k$ matters.

## De Moivre-Laplace Theorem

For infinite independent random variable $\eta_1, \eta_2, ...\eta_n, ...$, which are from the **binomial distribution** $b(n,p)$, then for $\forall ~ x$
$$
\lim_{n \to \infty} P\left\{ \frac{\eta_n-np}{\sqrt{np(1-p)}} \leq x \right\} = \Phi(x)
$$

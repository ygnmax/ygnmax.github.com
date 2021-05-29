---
title: Useful Distributions
date: 2019-2-15
tags: 
	- Probability
	- Statistics
	- Stochastic
categories: 
	- Mathematics
	- Probability
	- Probability Theory
mathjax: true
---
# Useful Distributions

## Discrete

Here are some useful *distributions* of ***discrete random variables*** which have distinct expected values and variances. A discrete uniform random variable represents the occurrence of a value between number a and b when all values in the set ${a; a + 1; a + 2; ...; b}$ have equal probability.

### Bernoulli Distribution

A binomial random variable represents the number of successful trials in a sequences of $n$ experiments ($r$ success and $i$ failure) when each trial is independent with a successful probability $p$.

$$
P(X=r)=p^r(1-p)^{1-r}, r=0, 1
$$

### Binomial Distribution

A binomial random variable represents the number of successful trials in a sequences of $n$ experiments ($r$ success and $i$ failure) when each trial is independent with a successful probability $p$.

$$
P(X=r)=C_{n}^{r}p^r(1-p)^{n-r}
$$

### Poisson Distribution

A Poisson random variable represents the number of events occurring in a fixed period of time with expected number of occurrences $\lambda t$ when events occur with a known average rate $\lambda$ (per unit time) and are independent since the last event.

+ memorylessness

  Shortfall distribution:
  $$
  P(\tau > t+s | \tau > s) = \frac{e^{-\lambda(t+s)}}{e^{-\lambda s}} 
  					     = e^{-\lambda t}
  $$
  

### Geometric Distribution

A geometric random variable represents the total trial number to get the first success when each trial is independent with a successful probability $p$.

$$
P(X=i)=p(1-p)^{i-1}
$$


### Negative binomial distribution

A negative binomial random variable represents that the number of failure trial in a sequences of $r+i$ experiments (to get the $r^{th}$ success) when each trial is independent with a successful probability $p $.

$$
P(X=i) = C_{r+i-1}^{i}p^r(1-p)^i
$$

### Pascal Distribution

A pascal random variable $X$ represents the total trial number, (in $n$ trials), to get $r$ successes when each trial is independent with a successful probability $\theta$.
$$
P(X=n)=C_{n-1}^{r-1}p^r(1-p)^{n-r}, n \geq r
$$


### Hypergeometric Distribution



## Relationship between the distribution above

### Negative binomial Distribution is the same as Pascal distribution

**Negative binomial**: Given $r$ success, the number of failures $i$
$$
P(X=i) = C_{r+i-1}^{i}p^r(1-p)^i
$$
**Pascal**: Given $r$ success, the number of trials $n$
$$
P(X=n)=C_{n-1}^{r-1}p^r(1-p)^{n-r}, n \geq r
$$
**Binomial** ($n$ Bernoulli trials): Given $n$ trials, the number of successes $r$ 
$$
P(X=r)=C_{n}^{r}p^r(1-p)^{n-r}
$$
**Bernoulli**: Given 1 trials, the number of success $r$
$$
P(X=r)=p^r(1-p)^{1-r}, r = 0, 1
$$
**Geometric**: Given 1 success, the number of trials $n$
$$
P(X=n)=p(1-p)^{n-1}
$$


## Continuous

Here are some useful *distributions* of ***discrete random variables*** which have distinct expected values and variances.

### Uniform Distribution

A continuous uniform random variable describes a random variable uniformly distributed over the interval $[a, b]$.



### Gauss Distribution (Normal Distribution)

Due to the central limit theorem, the normal distribution/Gaussian distribution is by far the most popular continuous distribution.
$$
\begin{align*}
f(x)=\frac{1}{\sqrt{2 \pi}}
\end{align*}
$$




### Exponential Distribution

The exponential distribution models **the arrival time of an event** if is has a constant arrival rate $\lambda$.



### Gamma Distribution

The gamma distribution with parameters $(\alpha, \lambda)$ often arises in practice, as the distribution of the amount of time one has to wait until a total of n events occur.



### Beta Distribution

The beta distribution is used to model events that are constrained within a defined interval. By adjusting the shape parameters $\alpha$ and $\beta$, it can model different shapes of probability distributions.







### Cauchy Distribution

$$
f(x;\mu,\sigma)=\frac{1}{\pi}\frac{\sigma}{\sigma^2+(x-\mu)^2}
$$

All the moments don't exist.

### Pareto Distribution

$$
f(x;\alpha, \theta)=\alpha\theta^{\alpha}x^{-(\alpha+1)}I\{x\geq \theta\}, ~~~ \theta>0, \alpha > 0
$$



### Weibull Distribution



### Rayleigh Distribution




---
title: Poisson Process
date: 2020-8-9
tags: 
	- Probability
	- Stochastic Processes
categories: 
	- Mathematics
	- Probability
	- Stochastic Processes
mathjax: true
---

# Exponential Distribution

If $\tau \sim \exp(\lambda)$, then the pdf is
$$
f_{\tau}(t) = \begin{cases}
\lambda e^{-\lambda t},& t \geq 0 \\
0,& t < 0
\end{cases}
$$
the cdf is
$$
F_{\tau}(t) = \begin{cases}
1-e^{-\lambda t},& t \geq 0 \\
0,& t < 0
\end{cases}
$$
The expectation is
$$
\mathbb{E}[\tau] = \int_{0}^{\infty}tf_{\tau}(t)dt = \frac{1}{\lambda}
$$


The variance is
$$
\mathbb{E}[\tau^2] = \int_{0}^{\infty}t^2f_{\tau}(t)dt = \frac{2}{\lambda^2} \\
\mathbb{Var}[\tau] = \mathbb{E}[\tau^2] - \mathbb{E}^2[\tau]
$$
Memoryless
$$
\mathbb{P}(\tau > u) = 1 -\mathbb{P}(\tau \leq u) = 1-(1-e^{-\lambda u})=e^{-\lambda u}
$$

$$
\mathbb{P}(\tau > u+v | \tau >v) = \frac{\mathbb{P}(\tau > u+v , \tau >v)}{\mathbb{P}(\tau >v)} = \frac{\mathbb{P}(\tau > u+v) }{\mathbb{P}(\tau >v)} = e^{-\lambda u} 
$$

# Poisson Process

$\tau_1, \tau_1,  \cdots, \tau_n, \cdots$ are $i.i.d.$ $\exp(\lambda)$. $\mathbb{\tau_i} = \frac{1}{\lambda}, i = 1, 2, \cdots$

The first jump occurs at time $\tau_1$, the second jump occurs at time $\tau_1+\tau_2$, the n-th jump occurs at time $\sum\limits_{k=1}^{n}\tau_k$. The $\{\tau_k\}_{k=1}^{\infty}$ is called inter arrival times. $S_k = \sum\limits_{i=1}^{k}\tau_i$ are arrival times. Define $N(t)$ is the number of jumps that occur __at or before__ time $t$, which mean that $N(t)$ is right-continuous. $N(t)$ is called Poisson Process.

## Arrival Times

$S_n = \sum\limits_{i=1}^{n}\tau_i$ are arrival times. $S_n$ is a Gamma Distribution. 
$$
g_{S_n} = \frac{(\lambda s)^{n-1}}{(n-1)!}\lambda e^{-\lambda s}, s \geq 0
$$

The jumps are arriving at an average rate of $\lambda$ per unit time. $\lambda$ is also the intensity of Poisson Process.

## Poisson Distribution

Given $N(t)$, $\lambda$, when the time $t$ is fixed, then $N(t)$ is a Poisson Distribution with parameter $\lambda t$. 
$$
\mathbb{P}(N(t)=k) = \frac{(\lambda t)^k}{k!}e^{-\lambda t}, k = 0, 1, 2, \cdots
$$
__Proof__
$$
N(t) \geq k \Leftrightarrow S_k \leq t
$$

$$
\begin{eqnarray}
\mathbb{P}(N(t) \geq k) &=& \mathbb{P}(S_k\leq t) \\
&=& \int_0^{t}\frac{(\lambda s)^{k-1}}{(k-1)!}\lambda e^{-\lambda s} \\
&=& \frac{\lambda^k}{(k-1)!}\int_0^{t}s^{k-1}e^{-\lambda s}ds \\
\\
\\
\mathbb{P}(N(t) \geq k+1) &=& \mathbb{P}(S_{k+1} \leq t) \\
&=& \int_0^{t}\frac{(\lambda s)^{k}}{k!}\lambda e^{-\lambda s} \\
&=& \frac{\lambda^{k}}{k!} \left(s^ke^{-\lambda s}|_{t}^{0} - \int_t^{0}e^{-\lambda s}ks^{k-1}ds \right) \\
&=& \frac{(\lambda t)^{k}}{k!} e^{-\lambda t} + \frac{\lambda^k}{(k-1)!}\int_0^{t}e^{-\lambda s}s^{k-1}ds  \\
\\
\\
\mathbb{P}(N(t) = k) &=& \mathbb{P}(N(t) \geq k+1) - \mathbb{P}(N(t) \geq k) \\
&=& \frac{(\lambda t)^{k}}{k!} e^{-\lambda t}
\end{eqnarray}
$$

## Properties 

### Increments

Let $0 = t_0 < t_1 < t_2 < \cdots < t_n$ be given. Then $N(t_1) - N(t_0), N(t_2) - N(t_1), \cdots, N(t_n) - N(t_{n-1})$ are stationary and independent, and $N(t_{j+1}) - N(t_j) \sim \text{Poi}((t_{j+1}-t_j)\lambda), j = 1,2,\cdots, n-1$

It means that, given $s < t$, 

+ $N(t)-N(s)$ shares the same distribution with $N(t-s)$: $N(t)-N(s) \sim \sim \text{Poi}((t-s)\lambda)$

+ $\mathbb{E}(N(t)-N(s)) = \lambda(t-s)$
+ $\mathbb{Var}(N(t)-N(s))=\lambda(t-s)$

### Relationship

Poisson Distribution

Exponential Distribution

Poisson Process



# Compensative Poisson Process







# Compound Poisson Process 
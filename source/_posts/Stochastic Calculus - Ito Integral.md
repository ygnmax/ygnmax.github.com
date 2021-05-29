---
title: Ito Integral
date: 2020-08-12
tags: 
	- Probability
	- Stochastic Calculus
categories: 
	- Mathematics
	- Probability
	- Stochastic Calculus
mathjax: true
---

# Ito Integral

## Why do we need Ito Integral

$\int_{0}^{T}\Delta(t)dg(t) = \int_{0}^{T}\Delta(t)g'(t)dt$, but it is not true if we replace $g(t)$ with a Brownian Motion $W(t)$ because $W(t)$ has no derivative:
$$
\int_{0}^{T}\Delta(t)dW(t)
$$
Here, $\Delta(t)$ is $\mathscr{F_t}$-measurable (which is an adapted process). In finance, $\Delta(t)$ is position, $W(t)$ is asset price, and then the integral is a gain during $[0,T]$.

## Ito Integral for simple function

Consider an Integral $I(t) = \int_{0}^{t}\Delta(s)dW(s)$, if $\Delta(s)$ is simple function, then

+ $0 \leq t \leq t_1$: 
  $$
  I(t) = \int_0^{t}\Delta(s)dW(s) = \Delta(0)\int_0^{t}dW(s) = \Delta(0)(W(t)-W(0))
  $$
  
+ $t_1 \leq t \leq t_2$: 
  $$
  I(t)= \int_0^{t}\Delta(s)dW(s) = \Delta(0)(W(t_1)-W(0)) + \Delta(t_1)(W(t)-W(t_1))
  $$

+ $t_k \leq t \leq t_{k+1}$:
  $$
  I(t)= \int_0^{t}\Delta(s)dW(s) = \sum_{j=0}^{k-1}\Delta(t_j)(W(t_{j+1})-W(t_j)) + \Delta(t_k)[W(t)-W(t_k)]
  $$

### Martingale

$0 \leq s \leq t \leq T, \mathbb{E}[I(t)|\mathscr{F_s}] = I(s)$

+ proof: 

  Assume $t_l \leq s \leq t_{l+1} \leq t_k \leq t < t_{k+1}$,
  $$
  \begin{eqnarray}
  I(t) &=& \sum_{j=0}^{k-1}\Delta(t_j)[W(t_{j+1})-W(t_{j})]+\Delta(t_k)[W(t)-W(t_k)] \\
  &=& \sum_{j=0}^{l-1}\Delta(t_j)[W(t_{j+1})-W(t_{j})]+\Delta(t_l)[W(t_{l+1})-W(t_{l})]+\sum_{j=l+1}^{k-1}\Delta(t_j)[W(t_{j+1})-W(t_{j})]+\Delta(t_k)[W(t)-W(t_k)] \\
  &=& A_1 + A_2 + A_4 + A_4
  \end{eqnarray}
  $$
  Then
  $$
  \begin{eqnarray}
  \mathbb{E}[A_1|\mathscr{F_s}] &=& A_1 = \sum_{j=0}^{l-1}\Delta(t_j)[W(t_{j+1})-W(t_{j})] \\
  
  \mathbb{E}[A_2|\mathscr{F_s}] &=& \mathbb{E}[\Delta(t_l)(W(t_{l+1})-W(t_{l}))|\mathscr{F_s}] \\
  &=& \Delta(t_l)(\mathbb{E}[W(t_{l+1})|\mathscr{F_s}] - W(t_l)) \\
  &=& \Delta(t_l)[W(s) - W(t_l)] \\
  
  \mathbb{E}[A_3|\mathscr{F_s}] &=& \mathbb{E}\left[\mathbb{E}\left[\sum_{j=l+1}^{k-1}\Delta(t_j)[W(t_{j+1})-W(t_{j})]|\mathscr{F_{t_j}}\right]|\mathscr{F_s}\right] \text{where $t_j \geq s $} \\
  &=& \mathbb{E}\left[\Delta(t_j)\left[\sum_{j=l+1}^{k-1}\mathbb{E}[W(t_{j+1})|\mathscr{F_{t_j}}]-\mathbb{E}[W(t_{j})|\mathscr{F_{t_j}}]\right]|\mathscr{F_s}\right] \\
  &=& \mathbb{E}\left[\Delta(t_j)\left[\sum_{j=l+1}^{k-1}\mathbb{E}[W(t_{j})]-\mathbb{E}[W(t_{j})]\right]|\mathscr{F_s}\right] = 0 \\
  
  \mathbb{E}[A_4|\mathscr{F_s}] &=& \mathbb{E}[\Delta(t_k)(W(t)-W(t_k))|\mathscr{F_s}] \\
  &=& \mathbb{E}[\mathbb{E}[\Delta(t_k)(W(t_{t}) - W(t_k))|\mathscr{F_{t_{k}}}]|\mathscr{F_s}] \\
  &=& \mathbb{E}[\Delta(t_k)(\mathbb{E}[W(t_{t})|\mathscr{F_{t_k}}] - W(t_k))|\mathscr{F_s}] \\
  &=& 0
  \end{eqnarray}
  $$
  Therefore, 

$$
\mathbb{E}[I(t)|\mathscr{F_s}] = \mathbb{E}[A_1 + A_2|\mathscr{F_s}] =  \sum_{j=0}^{l-1}\Delta(t_j)[W(t_{j+1})-W(t_{j})] + \Delta(t_l)[W(s) - W(t_l)] = I(s)
$$

### Moment	

+ When $s = 0$, $\mathbb{E}[I(t)|\mathscr{F_s}] = I(0) = 0$. Therefore, we have $\mathbb{E}[I(t)] = 0$ for all $t \geq 0$ 

+ __Ito Isometry__: $\mathbb{Var}[I(t)] = \mathbb{E}[I^2(t)] - \mathbb{E}[I(t)]^2 = \mathbb{E}[I^2(t)] = \mathbb{E}[\int_{0}^{t}\Delta^2(u)du]$

  + Proof:
    $$
    I(t) = \sum_{j=0}^{k-1}\Delta(t_j)[W(t_{j+1})-W(t_{j})]+\Delta(t_k)[W(t)-W(t_k)]
    $$
    For $0 \leq j \leq k-1$, let $w(t_{j+1})-w(t_j) = D_j$ and $w(t)-w(t_k) = D_k$, then
    $$
    \begin{eqnarray}
    I(t) &=& \sum_{j=0}^{k}\Delta(t_j)D_j \\
    I^2(t) &=& \sum_{j=0}^{k}\Delta(t_j)^2D_j^2 + 2 \sum_{0 \leq i \leq j \leq k}\Delta(t_i)\Delta(t_j)D_iD_j \\
    \end{eqnarray}
    $$
    Here, $\Delta(t_i), \Delta(t_j), D_i$ are adapted to $\mathscr{F_{t_j}}$ ($\mathscr{F_{t_j}}$-measurable), but $D_j$ is $\mathscr{F_{t_{j+1}}}$-measurable. In addition, they are independent increments. And $ are\Delta(t_i), \Delta(t_j)$ are finite.
    $$
    \begin{eqnarray}
    \mathbb{E}[\Delta(t_i)\Delta(t_j)D_iD_j] &=& \mathbb{E}[\Delta(t_i)\Delta(t_j)D_i]\mathbb{E}[D_j] = 0 \\
    \end{eqnarray}
    $$
    Because
    $$
    \begin{eqnarray}
    \mathbb{E}[\Delta^2(t_j)D_j^2] &=& \mathbb{E}[\Delta^2(t_j)]\mathbb{E}[D_j^2] \\
    \mathbb{E}[D_j^2] &=&  \mathbb{E}[D_j^2] + \mathbb{E}^2[D_j] ~~~\text{where $D_j \sim N(0,t_{j+1}-t_j)$} \\
    &=& \mathbb{Var}[D_j] = t_{j+1} - t_j
    \end{eqnarray}
    $$
    and $\Delta(t)$ is a simple integrand, which means that $\Delta^2(t_j)$ is a constant, we get
    $$
    \begin{eqnarray}
    \mathbb{E}[\Delta^2(t_j)D_j^2] &=& \mathbb{E}[\Delta^2(t_j)](t_{j+1} - t_j) \\
    &=& \begin{cases}
    \int_{t_j}^{t_{j+1}}\mathbb{E}[\Delta^2(u)]du ~~~ (0 \leq j \leq k-1) \\
    \int_{t_k}^{t}\mathbb{E}[\Delta^2(u)]du ~~~ (j = k) \\
    \end{cases}
    \end{eqnarray}
    $$
    Therefore, the Ito Isometry (Variance) is
    $$
    \begin{eqnarray}
    \mathbb{E}[I^2(t)] &=& \mathbb{E}\left[\sum_{j=0}^{k}\Delta^2(t_j)(t_{j+1} - t_j)\right] \\
    &=& \sum_{j=0}^{k-1}\int_{t_j}^{t_{j+1}}\mathbb{E}[\Delta^2(u)]du + \int_{t_k}^{t}\mathbb{E}[\Delta^2(u)]du  \\
    &=& \mathbb{E}\left[\int_{0}^{t}\Delta^2(u)du \right] 
    \end{eqnarray}
    $$
    __Ito Isometry is a constant (expectation).__

### Quadratic Variation

$$
[I,I](t) = \int_{0}^{t}\Delta^2(u)du \\
dI(t)dI(t) = \Delta^2(t)dt
$$



+ proof

  In $[t_j,t_{j+1}]$ and $[t_k,t]$, $t_j = s_0<s_1<\cdots< t_m=t_{j+1}$, $I(s_i) = \int_{0}^{s_i}\Delta(u)dW(u)$, $I(s_{i+1}) = \int_{0}^{s_{i+1}}\Delta(u)dW(u)$
  $$
  \begin{eqnarray}
  \sum_{i=0}^{m-1}[I(s_{i+1})-I(s_i)]^2 &=& \sum_{i=0}^{m-1}\left[\int_{s_i}^{s_{i+1}}\Delta(u)dW(u)\right]^2 \\
   &=& \Delta^2(t_j)\sum_{i=0}^{m-1}\left[W(s_{i+1})-W(s_i)\right]^2
  \end{eqnarray}
  $$
  Let $\max\limits_{0 \leq k \leq m-1}(s_{k+1}-s_k) \to 0$ and $m \to \infty$, according to the quadratic variation of Brownian Motion, we get
  $$
  \begin{eqnarray}
  \lim_{m \to \infty}\Delta^2(t_j)\sum_{i=0}^{m-1}\left[W(s_{i+1})-W(s_i)\right]^2 &=& \Delta^2(t_j)\lim_{m \to \infty}\sum_{i=0}^{m-1}\left[W(s_{i+1})-W(s_i)\right]^2 \\
  &=& \Delta^2(t_j)(t_{j+1}-t_j) \\
  &=& \int_{t_{j}}^{t_{j+1}}\Delta^2(u)du
  \end{eqnarray}
  $$

  therefore, 
  $$
  \begin{eqnarray}
  [I,I](t) &=& \sum_{j=0}^{k-1}\Delta^2(t_j)(t_{j+1}-t_j) + \Delta^2(t_k)(t-t_k) \\
  &=& \sum_{j=0}^{k-1}\int_{t_{j}}^{t_{j+1}}\Delta^2(u)du + \int_{t_{k}}^{t}\Delta^2(u)du \\
  &=& \int_{0}^{t}\Delta^2(u)du
  \end{eqnarray}
  $$
  and
  $$
  dI(t)dI(t) = \Delta^2(t)dt
  $$
  __Quadratic Variation of Ito Integral is a random variable, path by path. It's average level is the variance of Integral integral (Ito Isometry).__

### Notation

$$
I(t) = \int_{0}^{t}\Delta(u)dW(u) \tag{1}
$$

In equation (1), there is an assumption that $I(0) = 0$.
$$
I(t) = I(0) + \int_{0}^{t}\Delta(u)dW(u) \tag{2}
$$
In equation (2), we don't know the value of $I(0)$.
$$
dI(t) = \Delta(t)dW(t) \tag{3}
$$
The differential form of equation (1) and equation (2) are equation (3).



## Ito Integral for general function

In general, $\Delta(t)$ is no longer a simple function. However, it is possible to choose a sequence $\Delta_n(t)$ of simple processes, such that as $n \to \infty$ these processes converge to $\Delta(t)$ in mean square sense. $\Delta(t)$ is continuously varying. $\Delta_n(t)$ can be regarded as an approximation of $\Delta(t)$.

+ __Convergence in Mean Square__

  During the convergence, mean squared error is random because both $\Delta_n(t)$ and $\Delta(t)$ are random. We want to make convergence possible and minimize the 'mean squared error' by defining that
  $$
  \lim_{n\to \infty}\mathbb{E}\left[\int_{0}^{T}|\Delta_n(t)-\Delta(t)|^2dt\right] = 0
  $$
  Here, $\Delta_n(t) \neq \Delta(t)$, but the expectation of the mean squared error is going to 0 when the frequency is going to infinity. In this sense, we call it as convergence in mean square sense (in the stochastic background).

Therefore, ${\Delta_n(t)} \to \Delta(t)$ as $n \to \infty$, $\int_{0}^{t}\Delta_n(u)dW(u)$ has been defined on $0 \leq t \leq T$:
$$
\int_{0}^{t}\Delta(u)dW(u) = \lim_{n \to \infty}\int_{0}^{t}\Delta_n(u)dW(u)
$$

### Martingale

$I(t)$ is martingale.

### Moment

+ Expectation
  $$
  \mathbb{E}[I(t)] = \mathbb{E}[I(t)|\mathscr{F_0}] = I(0) = 0
  $$

+ Ito Isometry
  $$
  \mathbb{E}[I^2(t)] = \mathbb{E}\left[\int_{0}^{t}\Delta^2(u)du\right]
  $$

+ Distribution

  If $\Delta(u)$ is a deterministic function, then 
  $$
  I(t) = \int_{0}^{t}\Delta(u)dW(u) \sim N\left(0,\mathbb{E}\left[\int_{0}^{t}\Delta^2(u)du\right]\right)
  $$

### Quadratic Variation

$[I,I](t) = \int_{0}^{t}\Delta^2(u)du$ 

$dI(t)dI(t) = \Delta^2(t)dt$

### Continuity

$I(t)$ is continuous.

### Adaptivity

$I(t)$ is $\mathscr{F_t}$-measurable

### Linearity

+ $\int_{0}^{t}\Delta(u) \pm \Gamma(u)dW(u) = \int_{0}^{t}\Delta(u)dW(u) \pm \int_{0}^{t}\Gamma(u)dW(u) $

+ $\int_{0}^{t}c\Delta(u) dW(u) = c\int_{0}^{t}\Delta(u)dW(u)$, for every constant $c$





# Stratonovich Integral
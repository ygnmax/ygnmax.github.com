---
title: Parameter Estimation
date: 2020-3-12
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
# Estimator

## Criterion

### unbiased

 For $\hat{\theta}$ which is the estimation of $\theta$, 
$$
E_{\theta}(\hat{\theta})=\theta
$$

### effectiveness

Assume $\hat{\theta_1}$ and $\hat{\theta_2}$ are both unbiased estimation, for $\forall \theta \in \Theta$,
$$
D(\hat{\theta_1}) \leq D(\hat{\theta_2})
$$
then $\hat{\theta_1}$ is more effective than $\hat{\theta_2}$.

### Consistency

For $\hat{\theta},$ $\forall ~ \theta \in \Theta$
$$
\lim\limits_{n \to \infty}P\{|\hat{\theta}-\theta|<\epsilon\}=1
$$


## Moment Estimation

$ A_k = \frac{1}{n}\sum\limits_{i=1}^{n}X_i^k$ is convergent to $\mu_k$ by probability, where $\mu_k$ is k-order moment.

If there are $k$ parameters ($\theta_1, \theta_2,\cdots,\theta_k$), then we could compute $k$ order moment estimation:
$$
\begin{cases}
\mu_1 &=& \mu_1(\theta_1, \theta_2,\cdots,\theta_k) \\
\mu_2 &=& \mu_2(\theta_1, \theta_2,\cdots,\theta_k) \\
&\vdots& \\
\mu_2 &=& \mu_2(\theta_1, \theta_2,\cdots,\theta_k) \\
\end{cases}
$$

## Maximum Likelihood Estimation

### Likelihood Function

$$
L(\theta)=L(x_1, x_2, \cdots, x_n;\theta)=\prod\limits_{i=1}^{n}p(x_i;\theta), \theta\in \Theta
$$

### Log Likelihood Function

$$
\ln L(\theta) =\ln\prod\limits_{i=1}^{n}p(x_i;\theta) = \sum_{i=1}^{n} \ln p(x_i;\theta), \theta\in \Theta
$$

Example:

Assume $X\sim N(\mu,\sigma^2)$, $x_1, x_2, \cdots, x_n$ are samples, $\mu$ and $\sigma$ are unknown.
$$
\begin{eqnarray*}
L(\mu, \sigma^2) &=& \prod_{i=1}^{n}\frac{1}{\sqrt{2\pi} \sigma}e^{-\frac{(x_i-\mu)^2}{2\sigma^2}} \\
&=& \frac{1}{(\sqrt{2\pi} \sigma)^n}e^{-\frac{1}{2\sigma^2}\sum\limits_{i=1}^{n}(x_i-\mu)^2} \\
\ln L(\mu, \sigma^2) &=& -\frac{n}{2} \ln(2\pi)-\frac{n}{2} \ln\sigma^2-\frac{1}{2\sigma^2}\sum\limits_{i=1}^{n}(x_i-\mu)^2
\end{eqnarray*}
$$
Compute the partial derivatives:
$$
\begin{eqnarray*}
\frac{\partial}{\partial\mu}\ln L &=& \frac{1}{\sigma}\left(\sum_{i=1}^{n} x_i-n\mu\right) = 0\\
\frac{\partial}{\partial\sigma^2}\ln L &=& -\frac{n}{2\sigma^2}+\frac{1}{2(\sigma^2)^2}\sum_{i=1}^{n}(x_i-\mu)^2 = 0  \\
\end{eqnarray*}
$$
We can solve
$$
\mu = \frac{1}{n}\sum_{i=1}^{n}x_i = \bar{x} \\
\sigma^2 = \frac{1}{n}\sum_{i=1}^{n}(x_i-\mu)^2 = \frac{1}{n}\sum_{i=1}^{n}(x_i-\bar{x})^2
$$

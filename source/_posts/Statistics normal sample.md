---
title: Normal Sample
date: 2020-3-12
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
# Normal Sample

## Normal Distribution Additivity

### Lemma: Convolution Integral



### Additivity of normal distribution

Suppose $X_i\sim N(\mu_i,\sigma_i^2)$, then 
$$
Z = X_1 + X_2+\cdots+X_n
$$
subjects to the same distribution, and $Z\sim N(\mu_1+\mu_2+\cdots +\mu_n, \sigma_1^2+\sigma_2^2+\cdots+\sigma_n^2)$

Proof:



## Normal Distribution Sample

### Mean distribution

Suppose $X_i\sim N(\mu,\sigma^2)$, then 
$$
\begin{eqnarray*}
\bar{X} & \sim & N(\mu, \frac{\sigma^2}{n}) \\
\frac{\bar{X}-\mu}{\frac{\sigma}{\sqrt{n}}} & \sim & N(0,1)
\end{eqnarray*}
$$

### Variance distribution (variance $\sigma^2$ is unknown)

Suppose $X_i\sim N(\mu,\sigma^2)$, then 
$$
\frac{(n-1)S^2}{\sigma^2} \sim\chi^2(n-1)
$$
$S^2$ is dependent to $\bar{X}$.

### Mean distribution (mean $\mu$ is unknown)

Suppose $X_i\sim N(\mu,\sigma^2)$, then 
$$
\frac{\bar{X}-\mu}{\frac{S}{\sqrt{n}}} \sim t(n-1)
$$
Proof:
$$
\begin{eqnarray*}
\frac{\bar{X}-\mu}{\frac{\sigma}{\sqrt{n}}} & \sim & N(0,1) \\
\frac{(n-1)S^2}{\sigma^2} & \sim & \chi^2(n-1) \\
\frac{\frac{\bar{X}-\mu}{\frac{\sigma}{\sqrt{n}}}}{\sqrt{\frac{(n-1)S^2}{\sigma^2(n-1)}}} &=& \frac{\bar{X}-\mu}{\frac{S}{\sqrt{n}}} \sim t(n-1)
\end{eqnarray*}
$$

### Compare with two random variables (variance $\sigma^2$ is unknown)

Suppose $X_1, X_2, \cdots, X_{n_1} \sim N(\mu_1,\sigma_1^2)$ and $Y_1, Y_2, \cdots, Y_{n_2} \sim N(\mu_2,\sigma_2^2)$ , $X_i$ and $Y_i$ are sample and independent to each other. $\bar{X}$ and $\bar{Y}$ are sample mean, $S_1^2$ and $S_2^2$ are sample  variance, then
$$
\frac{\frac{S_1^2}{S_2^2}}{\frac{\sigma_1^2}{\sigma_2^2}} \sim F(n_1-1,n_2-1)
$$

### Compare with two random variables (mean $\mu $ is unknown)

When $\sigma_1^2 = \sigma_2^2 =\sigma^2$, then
$$
\frac{(\bar{X}-\bar{Y})-(\mu_1-\mu_2)}{S_w\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}} \sim  t(n_1+n_2-2)
$$
with $S_w^2 = \frac{(n_1-1)S_1^2+(n_2-1)S_2^2}{n_1+n_2-2}$

**Proof:**

$\bar{X}-\bar{Y}\sim N(\mu_1-\mu_2,\frac{\sigma_1^2}{n_1}+\frac{\sigma_2^2}{n_2})$

after standardizing:
$$
\frac{(\bar{X}-\bar{Y})-(\mu_1-\mu_2)}{\sqrt{\frac{\sigma_1^2}{n_1}+\frac{\sigma_2^2}{n_2}}} = \frac{(\bar{X}-\bar{Y})-(\mu_1-\mu_2)}{\sigma\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}} \sim N(0,1)
$$
For $\frac{(n_1-1)S_1^2}{\sigma_1^2} \sim\chi^2(n_1-1)$ and $\frac{(n_2-1)S_2^2}{\sigma_2^2} \sim\chi^2(n_2-1)$, then:  
$$
\frac{(n_1-1)S_1^2 +(n_2-1)S_2^2  }{\sigma^2} \sim\chi^2(n_1+n_2-2)
$$
by dividing:
$$
\frac{\frac{(\bar{X}-\bar{Y})-(\mu_1-\mu_2)}{\sigma\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}}}{\sqrt{\frac{(n_1-1)S_1^2 +(n_2-1)S_2^2  }{\sigma^2(n_1+n_2-2)}}} = \frac{(\bar{X}-\bar{Y})-(\mu_1-\mu_2)}{S_w\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}} \sim t(n_1+n_2+2)
$$

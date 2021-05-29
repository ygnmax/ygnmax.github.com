---
title:  Useful Statistics and Sample Distribution
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
# Useful Statistics

## Percentile

For a sample $x_1, x_2,...,x_n,...$, the sample percentile denotes $x_p$:

+ at least $np$ observations less than or equal $x_p$
+ at least $n(1-p)$ observations greater than or equal $x_p$

$$
\begin{eqnarray*}
x_p = \begin{cases} 
x_{[np]+1} \\
\frac{1}{2}[x_{np}+x_{np+1}]
\end{cases}
\end{eqnarray*}
$$

## Sample Mean

$$
E(\bar{X})=\frac{1}{n}\sum_{i=1}^{n}x_i=\frac{n\mu}{n}=\mu
$$



## Sample Variance

$$
\begin{eqnarray*}
S^2
&=&\frac{1}{n-1}\sum_{i=1}^{n}(X_i-\bar{X})^2 \\
&=&\frac{1}{n-1}\left(\sum_{i=1}^{n}X_i^2-n\bar{X}^2\right)
\end{eqnarray*}
$$

$$
\begin{eqnarray*}
S &=&\sqrt{\frac{1}{n-1}\left(\sum_{i=1}^{n}X_i^2-n\bar{X}^2\right)}
\end{eqnarray*}
$$

Check the unbiases:
$$
E(X_i^2)=D(X_i) + E(X_i)^2 = \sigma^2 + \mu^2 \\E(\bar{X}^2)=D(\bar{X})+E(\bar{X})^2 = \frac{\sigma^2}{n}+\mu^2
\\E(X_i)=E(\bar{X}) = \mu
$$

$$
\begin{eqnarray*}
E(S^2) 
&=& E\left[\frac{1}{n-1}\left(\sum_{i=1}^{n}X_i^2-n\bar{X}^2\right)\right] \\
&=& \frac{1}{n-1}E\left[\sum_{i=1}^{n}X_i^2\right]-\frac{n}{n-1}E[\bar{X}^2] \\
&=& \frac{1}{n-1}\sum_{i=1}^{n}(\sigma^2+\mu^2)-\frac{n}{n-1}(\mu^2+\frac{\sigma^2}{n}) \\
&=& \frac{n}{n-1}(\sigma^2-\frac{\sigma^2}{n}) \\
&=&\sigma^2
\end{eqnarray*}
$$


## Moment

### k-origin moment



### k-central moment



# Useful Sampling Distribution

## Chi-square Distribution

$X_1, X_2, ..., X_n$ are from $N(0,1)$, then
$$
\chi^2=X_1^2+X_2^2+\cdots+X_n^2
$$
follows $\chi^2$ distribution with freedom degree $n$ , denotes $\chi^2 \sim \chi^2(n)$

The probability density function is
$$
f(x)=
\begin{cases}
\frac{1}{2^{\frac{n}{2}}\Gamma(\frac{n}{2})}x^{\frac{n}{2}-1}e^{-\frac{x}{2}},&  x>0 \\
0 ,&x \leq 0
\end{cases}
$$
If $\chi^2\sim\chi^2(n)$, then

+ $E(\chi^2)=n$

+ $D(\chi^2)=2n$

## t Distribution

$X \sim N(0,1)$, $Y\sim\chi^2(n)$, $X$ is independent to $Y$, then
$$
t = \frac{X}{\sqrt{\frac{Y}{n}}}
$$
follows t distribution with freedom degree $n$.

The probability density function is
$$
f(x)=\frac{\Gamma\left(\frac{n+1}{2}\right)}{\sqrt{\pi n}\Gamma(\frac{n}{2})}\left(1+\frac{x^2}{n}\right)^{-\frac{n+1}{2}}
$$
If $t \sim t(n)$, then

+ $E[t_{\alpha}(n)]=0$
+ $D[t_{\alpha}(n)]=\frac{n}{n-2}$

## F Distribution

$U \sim \chi^2(n_1)$, $V\sim\chi^2(n_2)$, $U$ is independent to $V$, then
$$
F = \frac{\frac{U}{n_1}}{\frac{V}{n_2}}
$$
follows F distribution with freedom degree $(n_1, n_2)$, denotes $F\sim F(n_1,n_2)$

The probability density function is
$$
f(x)=
\begin{cases}
\frac{\Gamma[\frac{n_1+n_2}{2}](\frac{n_1}{n_2})^{\frac{n_1}{2}}x^{\frac{n_1}{2}-1}}{\Gamma(\frac{n_1}{2})\Gamma(\frac{n_2}{2})[1+\frac{n_1 x}{n_2}]^{\frac{n_1+n_2}{2}}},&  x>0 \\
0 ,&x \leq 0
\end{cases}
$$
If $F\sim F(n_1, n_2)$, then

+ $\frac{1}{F}\sim F(n_2,n_1)$

+ $F_{1-\alpha}(n_1,n_2)=\frac{1}{F_{\alpha}(n_2,n_1)}$
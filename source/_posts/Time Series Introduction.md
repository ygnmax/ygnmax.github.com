---
title: Introduction to Time Series
date: 2020-4-3
tags: 
	- Econometrics
	- Time Series
categories: 
	- Economics
	- Econometrics
	- Time Series
mathjax: true
---

# Introduction

## Ideas behind time series

One of assumptions of any model is:

+ independence of errors / residuals

This means that there should be no pattern in the residuals, and pattern means that we can find a better fit. It can be a not linear model.

Time series is one of these non-linear models. After applying the time series model, the $\sum{e_i^2}$ total error square should be reduced and the patterns on residuals are gone. Compared to the coefficient $b$ in linear regression, coefficient $a$ in time series is just a number without specific meaning.

## type of time series model

There are two types of time series models, one is ARMA model, and other is spectral model.

+ ARMA model:

$$
x_t = a_1x_{t-1} + a_2x_{t-1} + ... + b_1\epsilon_{t-1}+b_2\epsilon_{t_2}+...
$$

+ Spectral model:

$$
\begin{eqnarray*}
x_t &=& a_1\sin(\frac{2\pi}{5}t)+b_1\cos(\frac{2\pi}{5}t) \\
&+& a_2\sin(\frac{2\pi}{7}t)+b_2\cos(\frac{2\pi}{7}t) \\
&+& ...
\end{eqnarray*}
$$

There is also a difference between time series and Brownian motion. Time series is a discrete model with t from negative infinite to positive infinite. However, Brownian motion is a continuous model within finite time.

For ARMA model, there are 3 simple formats:

+ White Noise

$$
\begin{eqnarray*}
x_t &=& w_t \\
w_t &\sim& N(0,\sigma^2) \text{iid}
\end{eqnarray*}
$$

+ Moving Average

$$
x_t = \frac{x_{t+1}+x_{t}+x_{t-1}}{3}
$$

+ Auto Regression

$$
x_t = 0.4 x_{t-1} + 0.4 x_{t-2} + w_t
$$

# Simulation

Ideally, we should simulate the time series for many times (say 100 times). Here, because they are simulated from the same equation, each realization must follow the distribution. And then We compute the expectation and covariance using the simulated data:
$$
\begin{eqnarray*}E(x_{10}) \\E(x_{20}) \\Cov(x_{10}, x_{20})\end{eqnarray*}
$$
And theoretically, we can also compute the expectation and covariance using math, for a moving average series:
$$
\begin{eqnarray*}
E(x_{10}) &=& \frac{1}{3}E(W_9+W_{10}+W_{11}) = 0 \\
E(x_{20}) &=& \frac{1}{3}E(W_{19}+W_{20}+W_{21}) = 0 \\
\end{eqnarray*}
$$

$$
\begin{eqnarray*}
Cov(x_{10},x_{20}) = \frac{1}{9}E(W_9W_{19} &+& W_9W_{20}+W_9W_{21} \\
+W_{10}W_{19}&+&W_{10}W_{20}+W_{10}W_{21} \\
+W_{11}W_{19}&+&W_{11}W_{20}+W_{11}W_{21}) 
\end{eqnarray*}
$$

However, in reality, many things only have one simulation. We cannot compute the expectation and covariance based on one simulation. Then, we find some alternatives: compute the covariance with lag terms.

# Stationary




---
title: Binomial Model
date: 2019-12-15
update: 2019-12-20
tags: 
	- Finance
	- Asset Pricing
categories: 
	- Economics
	- Finance
	- Derivatives
---


## Hedge: Cox-Ross-Robinstein Binomial Tree

### One Period

Consider a portfolio V:

+ long 1 call option, which strike price is 5

+ short $\Delta$ shares of stocks

Then whenever the stock price is increasing (H) or decreasing (T), this should always hold:
$$
V_1(H) - \Delta S_1(H) = V_1(T) - \Delta S_1(T) \\
\Delta = \frac{V_1(H)- V_1(T)}{S_1(H)-S_1(T)}
$$
For example, initially, a stock price is 4. If stock price is increasing, where the risk-neutral probability is $\tilde{p}$, it will reach 8 at the second period. If stock price is decreasing, where the risk-neutral probability is $\tilde{q}$, it will reach 2 at the second period. That is to say, $S_0$ = 4, $S_1(H) = 8$, $S_1(T) = 2$. Therefore, $V_1(H) = \max\{S_1(H)-K, 0\} = 3$, $V_1(T) = \max\{S_1(T) - K, 0\} = 0$. In this way,
$$
\Delta = \frac{V_1(H)- V_1(T)}{S_1(H)-S_1(T)} = \frac{3-0}{8-2} = 0.5
$$
For risk-neutral probability 
$$
\tilde{p} + \tilde{q} = 1 \tag{1}
$$
For stock price, if discounting the price from period 1 to period 0, we get
$$
\frac{8 \tilde{p} + 2 \tilde{q}}{1+r} = S_0 = 4 \tag{2}
$$
For option value, if discounting the price from period 1 to period 0, we get
$$
\frac{3 \tilde{p} + 0 \tilde{q}}{1+r} = V_0 \tag{3}
$$
Three equations solve three parameters.

### 

We can change all the numbers to parameters. Under the condition:
$$
u > e^{r(T-t)}>d
$$
Construct a portfolio which receive risk free rate: 

+  short 1 call option
+ long $\Delta$ stocks

Then 
$$
\Delta S u - f_u = \Delta S d - f_d \\
\Delta = \frac{f_u-f_d}{Su - Sd}
$$
Where $ud = 1$, $u$ is called increasing factor, $d$ is called decreasing factor. Because $S\Delta - f$ is a risk free asset, it will receive risk free rate whenever it increases or decreases:
$$
S\Delta - f = (\Delta S u - f_u)e^{-r(T-t)}
$$
and we can get the formula of $f$:
$$
\begin{eqnarray*}
f &=& S \Delta - (\Delta S u - f_u)e^{-r(T-t)} \\
  &=& e^{-r(T-t)}[e^{r(T-t)}S\Delta - (\Delta Su - f_u)] \\
  &=& e^{-r(T-t)}[(e^{r(T-t)}S-Su)\Delta  + f_u)] \\
  &=& e^{-r(T-t)}[(e^{r(T-t)}S-Su)\frac{f_u-f_d}{Su - Sd}  + f_u)] \\
  &=& e^{-r(T-t)}[\frac{e^{r(T-t)}-u}{u-d}(f_u-f_d)  + f_u)] \\
  &=& e^{-r(T-t)}[(\frac{e^{r(T-t)}-u}{u-d}+1)f_u  +(- \frac{e^{r(T-t)}-u}{u-d})f_d)] \\
  &=& e^{-r(T-t)}[pf_u  +(1- p)f_d] \\
\end{eqnarray*}
$$
where
$$
p =\frac{e^{r(T-t)}-d}{u-d} \\
u = e^{\sigma\sqrt{T-t}}, d = e^{-\sigma\sqrt{T-t}}
$$

### Multiple Period

$$
V_0 = e^{-rT}[\tilde{p}^NG(u^NS_0) + C_{N}^{N-1}\tilde{p}^{N-1}(1-\tilde{p})G(u^{N-1}dS_0)+\cdots + (1-\tilde{p})^{N}G(d^{N}S_0)]
$$


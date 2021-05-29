---
title: Ito Doeblin Formula
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



## Why do we need Ito Doeblin Formula

For ordinary calculus
$$
\frac{d}{dt}f(W(t)) = f'(W(t))W'(t) \\
df(W(t)) = f'(W(t))dW(t)
$$
but for stochastic calculus, $dW(t)$ has no definition, the formula should be revised.

## Ito Doeblin formula for Brownian Motion

Let $f(t,X)$ be a function for which the partial derivatives $f_t(t,X)$ $f_X(t,X)$, $f_{XX}(t, X)$ are defined and continuous. $W(t)$ is Brownian Motion. Then for every $T \geq 0$, we have
$$
f(t, W(t)) = f(0,W(0)) + \int_{0}^{T}f_t(t,W(t))dt + \int_{0}^{T}f_X(t,W(t))dW(t) + \frac{1}{2} \int_{0}^{T}f_{XX}(t,W(t))dt
$$

+ proof

  Because the Taylor Formula is
  $$
  f(t_{j+1},X_{j+1}) - f(t_{j},X_{j}) = f_t(t_{j},X_{j})(t_{j+1}-t_j) + f_X(t_{j},X_{j})(X_{j+1}-X_j) + \frac{1}{2}f_{tt}(t_{j},X_{j})(t_{j+1}-t_{j})^2 +  \frac{1}{2}f_{XX}(t_{j},X_{j})(X_{j+1}-X_{j})^2 + \frac{1}{2}f_{tX}(t_{j},X_{j})(t_{j+1}-t_{j})(X_{j+1}-X_{j}) o((t_{j+1}-t_j)^2) + o((X_{j+1}-X_j)^2)
  $$
  Now consider a partition $\pi = {t_0, t_1, \cdots, t_n}$, $0 = t_0 < t_1 < \cdots < t_n =T$,
  $$
  \begin{eqnarray}
  \sum_{j=0}^{n-1}f(t_{j+1},W_{j+1}) - f(t_{j},W_{j}) &=& \sum_{j=0}^{n-1}f_t(t_{j},W_{j})(t_{j+1}-t_j) \\
  &+& \sum_{j=0}^{n-1}f_X(t_{j},W_{j})(W_{j+1}-W_j) \\
  &+& \sum_{j=0}^{n-1}\frac{1}{2}f_{tt}(t_{j},W_{j})(t_{j+1}-t_{j})^2 \\
  &+& \sum_{j=0}^{n-1}\frac{1}{2}f_{XX}(t_{j},W_{j})(W_{j+1}-W_{j})^2 \\
  &+& \sum_{j=0}^{n-1}\frac{1}{2}f_{tX}(t_{j},W_{j})(W_{j+1}-W_{j})(t_{j+1}-t_{j})
  \end{eqnarray}
  $$
  And take the limit as the max difference in partition $\pi$ goes to 0:
  $$
  \begin{eqnarray}
  \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}f(t_{j+1},W_{j+1}) - f(t_{j},W_{j}) &=& \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}f_t(t_{j},W_{j})(t_{j+1}-t_j) \\
  &+& \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}f_X(t_{j},W_{j})(W_{j+1}-W_j) \\
  &+& \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}\frac{1}{2}f_{tt}(t_{j},W_{j})(t_{j+1}-t_{j})^2 \\
  &+& \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}\frac{1}{2}f_{XX}(t_{j},W_{j})(W_{j+1}-W_{j})^2 \\
  &+& \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}\frac{1}{2}f_{tX}(t_{j},W_{j})(W_{j+1}-W_{j})(t_{j+1}-t_{j})
  \end{eqnarray}
  $$
  

Consider $\lim\limits_{||\pi|| \to 0}\sum\limits_{j=0}^{n-1}\frac{1}{2}f_{tX}(t_{j},W_{j})(W_{j+1}-w_{j})(t_{j+1}-t_{j})$, function $f$ 
$$
\begin{eqnarray}
\lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}\frac{1}{2}f_{tX}(t_{j},W_{j})(W_{j+1}-w_{j})(t_{j+1}-t_{j}) &\leq& \lim_{||\pi|| \to 0}\max_{0 \leq j \leq n-1}(t_{j+1}-t_{j})\sum_{j=0}^{n-1}\frac{1}{2}f_{tX}(t_{j},W_{j})(W_{j+1}-W_{j}) \\
&=& \frac{1}{2} \cdot 0 \cdot \left|\int_{0}^{T}f_{tX}(t,W(t))dW(t)\right| = 0
\end{eqnarray}
$$

+ Example

  consider a function $f(t,X(t)) = \frac{1}{2}W(t)^2$, then $f_t(t,X(t)) = 0$,  $f_X(t,X(t)) = W(t)$,  $f_{XX}(t,X(t)) = 1$, apply the Ito formula
  $$
  df(t,X(t)) = W(t)dW(t) + \frac{1}{2}dt
  $$
  and integral is
  $$
  f(t,X(t)) - f(t,X(0)) = \int_{0}^{t}W(s)dW(s)+\frac{1}{2}\int_{0}^{t}ds \\
  \frac{1}{2}W(t)^2 = \int_{0}^{t}W(s)dW(s)+\frac{1}{2}t \\
  \int_{0}^{t}W(s)dW(s) = \frac{1}{2}W(t)^2-\frac{1}{2}t
  $$





## Ito Process

Define Ito Process as
$$
X(t) = X(0) + \int_{0}^{t}\Delta(u)dW(u) + \int_{0}^{t}\Theta(u)du
$$
$X(0)$ is non-random, $\Delta(u)$, $\Theta(u)$ are adapted process of $\mathscr{F_u}$, $0 \leq u \leq T$ where $\mathscr{F_u}$ is a filtration associated with $W(u)$. The differential form is
$$
dX(t) = \Theta(t)dt + \Delta(t)dW(t)
$$

### Quadratic Variation

$$
\left[X,X\right](t) = \int_{0}^{t}\Delta^2(u)du \\
dX(t)dX(t) = \Delta^2(t)dt
$$

### Integral on the Ito Process

Consider an Ito Process $dX(t) = \Theta(t)dt + \Delta(t)dW(t)$
$$
\begin{eqnarray}
\int_{0}^{t}\Gamma(u)dX(u) &=& \int_{0}^{t}\Gamma(u)[\Delta(u)dW(u)+\Theta(u)du] \\
&=& \int_{0}^{t}\Gamma(u)\Delta(u)dW(u) + \int_{0}^{t}\Gamma(u)\Theta(u)du
\end{eqnarray}
$$

## Ito Doeblin formula for Ito Process

### One Dimension

Consider an Ito process $dX(t) = \Theta(t)dt + \Delta(t)dW(t)$
$$
\begin{eqnarray}
f(T,X(T)) &=&  f(0,X(0)) + \int_{0}^{T}f_t(t,X(t))dt + \int_{0}^{T}f_X(t,X(t))dX(t) + \frac{1}{2}\int_{0}^{T}f_{XX}(t,X(t))dX(t)dX(t) \\
&=& f(0,X(0)) + \int_{0}^{T}f_t(t,X(t))dt + \int_{0}^{T}f_X(t,X(t))[\Theta(t)dt + \Delta(t)dW(t)] + \frac{1}{2}\int_{0}^{T}f_{XX}(t,X(t))\Delta^2(t)dt \\
&=& f(0,X(0)) + \int_{0}^{T}[f_t(t,X(t)) + f_X(t,X(t))\Theta(t) + \frac{1}{2}f_{XX}(t,X(t))\Delta^2(t)]dt + \int_{0}^{T}f_X(t,X(t))\Delta(t)dW(t)\\
\end{eqnarray}
$$

### Two Dimensions

Consider two Ito processes  $dX(t) = \Theta_1(t)dt + \Delta_1(t)dW(t)$,  $dY(t) = \Theta_2(t)dt + \Delta_2(t)dW(t)$
$$
\begin{eqnarray}
df(t,X(t),Y(t)) &=& f_t(t,X(t),Y(t))dt + f_X(t,X(t),Y(t))dX(t) + f_Y(t,Y(t),Y(t))dY(t) \\
&+& \frac{1}{2}f_{XX}(t,X(t),Y(t))dX(t)dX(t) + \frac{1}{2}f_{YY}(t,X(t),Y(t))dY(t)dY(t) +f_{XY}(t,X(t),Y(t))dX(t)dY(t)
\end{eqnarray}
$$


### Ito Production Rule

Consider the production of two Ito processes $f = X(t)Y(t)$
$$
\begin{eqnarray}
df(t,X(t),Y(t)) &=& Y(t)dX(t) + X(t)dY(t) + dX(t)dY(t)
\end{eqnarray}
$$
which is different from the ordinary calculus:
$$
d(uv) = udv + vdu
$$

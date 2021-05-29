---
title: Jump Process
date: 2020-08-15
tags: 
	- Probability
	- Stochastic Calculus
categories: 
	- Mathematics
	- Probability
	- Stochastic Calculus
mathjax: true
---

# Definition

Consider a jump process $X(t)$:
$$
\begin{eqnarray}
X(t) &=& X(0) + I(t) + R(t) + J(t) \\
&=& X^c(t) + J(t) \\ 
&=& X(0) + \int_{0}^{t}\Gamma(s)dW_s + \int_{0}^{t}\Theta(s)ds+J(t)
\end{eqnarray}
$$
where $X^c(t)$ is Ito process and $J(t)$ is a pure jump process

+ no jump at time 0
+ has only finitely many jumps on each finite time interval $[0, T]$

+ constant between jumps

+ right-continuous $J(0) = 0$ and $J(t) = \lim_{s \to t^+}J(s)$ , $t \geq 0$



The jump size is defined as $\Delta J(t) = J(t) - J(t^-)$. And $\Delta J(0) = 0 \Rightarrow J(0) = J(0^-)$, $X(0) = X(0^-)$ 



If $X(t)$ is continuous at time $t$, then $\Delta X(t) = 0$. If $X(t)$ jump at time $t$, then $\Delta X(t) \neq 0$ is the size of the jump: $\Delta X(t) \neq 0$ is the size of the jump: $\Delta X(t) = J(t) - J(t^-) = \Delta J(t)$



The quadratic deviation: 
$$
\begin{eqnarray}
dX^c(t)dX^c(t) = \Gamma^2(t)dt \\
[X^c, X^c](t) = \int_0^t\Gamma^2(s)ds
\end{eqnarray}
$$


Let $X(t)$ be a jump process defined above, and let $\Phi(s)$ be an adapted process. The stochastic integral of $\Phi(s)$ with respect to $X(t)$ is 
$$
\begin{eqnarray}\label{eqn1}
\int_{0}^{t}\Phi(s)dX_s = \int_{0}^{t}\Phi(s)\Gamma(s)dW_s + \int_{0}^{t}\Phi(s)\Theta(s)ds + \int_{0}^{t}\Phi(s)dJ(s)
\end{eqnarray}
$$
Because
$$
\\
dX_s = \Gamma(s)dW_s+\Theta(s)ds + dJ(s)
$$
Here, $dJ(s)$ has no definition at the jump point, but the integral $\int_{0}^{t}\Phi(s)dJ(s)$ is exactly 
$$
\sum_{0 < s \leq t}\Phi(s)\Delta J(s)
$$






Recall that 
$$
I(t) = \int_{0}^{t}\Phi(s)dW_s
$$
is a martingale $s \leq t \Rightarrow E[I(t)|F(s)] = I(s)$. Now, consider 
$$
H(t) = \int_{0}^{t}\Phi(s)dX_s
$$
where $X(s)$ is a jump process. __$H(t)$ is not necessarily a martingale__. For example, $X(t) = N(t) - \lambda t$, $\Phi(s) = \Delta N(s)$
$$
\int_{0}^{t}\Phi(s)dX(s) = \int_0^{t}\Phi(s)dX^c_s + \int_0^{t}\Phi(s)dJ(s)
$$
The first part is 
$$
-\lambda \int_{0}^{t} \Phi(s)ds = 0
$$
the second part is 
$$
\sum_{0<s\leq t} (\Delta N(s))^2 = \sum_{s = 0}^t 1^2 = N(t)
$$
therefore, 
$$
\int_{0}^{t}\Phi(s)dX(s) = N(t)
$$
which is not a martingale.



Theorem: Assume that the jump process $X(s)$ is a martingale, the integrand $\Phi(s)$ is left-continuous and adapted, and $E\left[\int_0^t \Gamma^2(s)\Phi^2(s)ds\right] < \infty$ for all $t \geq 0$, then
$$
\int_{0}^{t}\Phi(s)dX(s)
$$
is also a martingale.

$\Phi(s)$ can be regarded as a position, $X(s)$ can be regarded as a price, then $\int_{0}^{t}\Phi(s)dX(s)$ can be regarded as a gain.
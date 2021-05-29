---
title: Stochastic Differential Equation2
date: 2020-08-14
tags: 
	- Probability
	- Stochastic Calculus
	- Stochastic Differential Equation
categories: 
	- Mathematics
	- Probability
	- Stochastic Calculus
mathjax: true
---

 # Solution of SDE

## Ito SDE 

### Equivalent SDE 

Consider a SDE in two Calculus system:

In Ito Calculus
$$
dX_t = a(t,X_t)dt + b(t,X_t)dB_t
$$
In Stratonovich Calculus
$$
dX_t = \widetilde{a}(t,X_t)dt + \widetilde{b}(t,X_t) \circ dB_t
$$
These two SDEs should give the same solution, which means they are __equivalent SDE__. In practice. We need to find the relationship between $a$ and $\tilde{a}$; $b$ and $\tilde{b}$.

### From Ito to Stratonovich

Consider an Ito SDE
$$
X_T = X_0 + \int_{0}^{T}a(t,X_t)dt + \int_{0}^{T}b(t,X_t)dB_t
$$
Then the transformation formula from Ito Calculus to Stratonovich Calculus is
$$
\int_{0}^{T}f(t,X_t) \circ dB_t = \int_{0}^{T}f(t,X_t)dB_t + \frac{1}{2}\int_{0}^{T}b(t,X_t)f_X(t,X_t) dt
$$


> For example, consider an Ito SDE
> $$
> dX_t = dW_t \\
> f(t,X) = X
> $$
> Here, $b(t,X_t) = 1$, $f_X(t,X) = 1$, then
> $$
> \begin{eqnarray}
> \int_{0}^{T}W_t\circ dW_t &=& \int_{0}^{T}W_tdW_t + \frac{1}{2}\int_{0}^{T}dt \\
> &=& \int_{0}^{T}W_tdW_t + \frac{1}{2}T \\
> &=& \frac{1}{2}W_t^2 - \frac{T}{2} + \frac{1}{2}T \\
> &=& \frac{1}{2}W_t^2
> \end{eqnarray}
> $$

### Solve Ito SDE

Consider an Ito SDE
$$
X_T = X_0 + \int_{0}^{T}a(t,X_t)dt + \int_{0}^{T}b(t,X_t)dB_t
$$
Because
$$
\int_{0}^{T}f(t,X_t)\circ dB_t = \int_{0}^{T}f(t,X_t)dB_t + \frac{1}{2}\int_{0}^{T}b(t,X_t)f_X(t,X_t) dt
$$
where $\int_{0}^{T}f(t,X_t)\circ dB_t$ is Stratonovich Integral. Let $f(t,X_t) \to b(t, X_t)$
$$
\int_{0}^{T}f(t,X_t)\circ dB_t = \int_{0}^{T}b(t,X_t)\circ dB_t = \int_{0}^{T}b(t,X_t)dB_t + \frac{1}{2}\int_{0}^{T}b(t,X_t)b_X(t,X_t) dt \\
\int_{0}^{T}b(t,X_t)dB_t  =  \int_{0}^{T}b(t,X_t)\circ dB_t -\frac{1}{2}\int_{0}^{T}b(t,X_t)b_X(t,X_t) dt
$$
Therefore
$$
\begin{eqnarray}
dX_t &=& a(t,X_t)dt + b(t,X_t)dB_t \\
&=& a(t,X_t)dt+b(t,X_t)\circ dB_t -\frac{1}{2}b(t,X_t)b_X(t,X_t)dt \\
&=& \left[a(t,X_t) - \frac{1}{2}b(t,X_t)b_X(t,X_t)\right]dt + b(t,X_t)\circ dB_t \\
&=& \widetilde{a}(t,X_t)dt + \widetilde{b}(t,X_t) \circ dB_t
\end{eqnarray}
$$
We can get the relationship
$$
\begin{eqnarray}
\widetilde{a}(t,X_t) &=& \left[a(t,X_t) - \frac{1}{2}b(t,X_t)b_X(t,X_t)\right] \\
\widetilde{b}(t,X_t) &=& b(t,X_t)
\end{eqnarray}
$$
Then for each Stratonovich SDE, we can solve the analogue of in ODE. After getting the solution to ODE, we can derive it back to the solution of Stratonovich SDE, which is the equivalent solution to Ito SDE.



## Monte Carlo


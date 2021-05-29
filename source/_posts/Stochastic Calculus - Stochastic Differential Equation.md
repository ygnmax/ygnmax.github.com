---
title: Stochastic Differential Equation
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

# Source of Randomness 

Consider an ordinary differential equation
$$
\begin{eqnarray}
\begin{cases}
dX(t) = a(t,X(t))dt \\
X(0) = X_0
\end{cases}
\end{eqnarray}
$$
There are two kinds of source of randomness if we change it to SDE: 

+ Randomize the initial value
  $$
  \begin{eqnarray}
  \begin{cases}
  dX(t) = a(t,X(t))dt \\
  X_0(\omega) = Y(\omega)
  \end{cases}
  \end{eqnarray}
  $$
  Example:
  $$
  \begin{eqnarray}
  \begin{cases}
  dX_t = X_tdt \\
  X_0 = e^N, N\sim N(0,\sigma)
  \end{cases}
  \end{eqnarray}
  $$
  The solution is 
  $$
  X_t = X_0e^t=e^{N+t}
  $$
  which is a stochastic process.

+ There is an additional Random Noise $B_t$
  $$
  dX_t = a(t,X_t)dt + b(t,X_t)dB_t
  $$
  The Integral form is
  $$
  X_t = X_0 + \int_{0}^{t} a(s,X_s)ds + \int_{0}^{t} b(s,X_s)dB_s
  $$

The Noise term is called driving process. If the driving process is a Brownian Motion, we call it __Ito Stochastic Differential Equation (Ito SDE)__. But it can be other processes, like semi-martingale, Levy process, etc. Brownian Motion is a special semi-martingale.

# Existence of Solution

## Strong Solution

### Definition

A stochastic differential equation 
$$
X_t = X_0 + \int_{0}^{t} a(s,X_s)ds + \int_{0}^{t} b(s,X_s)dB_s
$$
has strong solution if the following conditions are satisfied:

+ $X_t$ is adapted $B_t$, i.e. $X_t$ is a function of $B_s$, $s \leq t$. 
+ $\int_{0}^{t} a(s,X_s)ds$ and $\int_{0}^{t} b(s,X_s)dB_s$ are well defined
+ $X_t$ is a function of the underlying sample path and of $a(t,X_t)$ and $b(t, X_t)$

If we only care about the solution at the distribution level, then it is a weak solution.

### Lipschitz Condition

Assume the initial condition $X_0$ satisfying 

+ $\mathbb{E}[X_0^2] < \infty$

+ independent of $B_t$, $t \geq 0$

If $\forall t \in [0,T]$ and $x,y \in \mathbb{R}$

+ $a(t,X_t)$, $b(t,X_t)$ are continuous
+  $\exists k \in [0,T]$ such that  $|a(t,X_t)-a(t,Y_t)| +|b(t,X_t)-b(t,Y_t)| \leq k|X_t-Y_t| $ 

Then Ito SDE has unique strong solution $S_t$ on $[0,T]$



For example
$$
X_t = X_0 + \int_{0}^{t} (c_1X_s+c_2)ds + \int_{0}^{t} (\sigma_1X_s+\sigma_2)dB_s, s \in [0,T]
$$
then Lipschitz condition shows that 
$$
|c_1||X-Y|+|\sigma_1||X-Y| \leq k|X-Y| \\
k \geq |c_1| + |\sigma_1|
$$
This linear Ito SDE has unique strong solution.

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
> 

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

#### Example 1

Consider an Ito SDE
$$
dX_t = \frac{1}{2}f(X_t)f'(X_t)dt + f(X_t)dB_t
$$
but we want to solve it in Stratonovich Calculus. We can find that
$$
\begin{eqnarray}
\tilde{a} &=& \frac{1}{2}f(X_t)f'(X_t) - \frac{1}{2}f(X_t)f'(X_t) = 0 \\
\tilde{b} &=& f(X_t)
\end{eqnarray}
$$
Therefore, the equivalent Stratonovich SDE is
$$
dX_t = f(X_t) \circ dB_t
$$
Assume the original function of $\frac{1}{f(x)}$ is $g(x)$, the analogue in ODE is 
$$
\begin{eqnarray}
dl_t &=& f(l_t)dc_t \\
\frac{dl_t}{f(l_t)} &=& dc_t \\
\int_{l_0}^{l_t}\frac{du}{f(u)} &=& c_t-c_0 \\
g(l_t)-g(l_0) &=& c_t - c_0 \\
g(l_t) &=& g(l_0) + c_t - c_0 \\
\end{eqnarray}
$$
and we change change it back to Stratonovich SDE:
$$
\begin{eqnarray}
g(X_t) &=& g(X_0) + B_t - B_0 \\
X_t &=& g^{-1}(g(X_0) + B_t - B_0)
\end{eqnarray}
$$
The solution is also for Ito SDE.

#### Example 2

 Solve the SDE
$$
dX_t = \frac{1}{2}nX_t^{2n-1}d_t+X_t^ndB_t
$$
The $f(X) = X^n, \frac{1}{2}f(X)f'(X) = \frac{1}{2}X^{2n-1}$, so the equivalent SDE is
$$
dX_t = X_t^n \circ dB_t
$$
the analogue in ODE is
$$
\begin{eqnarray}
dl_t &=& l_t^ndc_t \\
\frac{1}{l_t^n}dl_t &=& dc_t \\
\int_{l_0}^{l_t}\frac{1}{u^n}du &=& \int_{0}^{t}dc_t \\
\int_{l_0}^{l_t}\frac{1}{u^n}du &=& c_t - c_0 \\
\frac{1}{1-n}u^{1-n}|_{l_0}^{l_t} &=& c_t - c_0 \\
\frac{1}{1-n}(l_t)^{1-n}-\frac{1}{1-n}(l_0)^{1-n} &=& c_t - c_0
\end{eqnarray}
$$
Then transform it back to SDE
$$
\begin{eqnarray}
\frac{1}{1-n}X_t^{1-n}-\frac{1}{1-n}X_0^{1-n} &=& B_t -B_0 \\
X_t^{1-n} &=& B_t(1-n) + X_0^{1-n} \\
X_t &=& [B_t(1-n) + X_0^{1-n}]^{\frac{1}{^{1-n}}}, n \geq 2
\end{eqnarray}
$$

#### Example 3

Solve the SDE
$$
dX_t = [qf(X_t)+\frac{1}{2}f(X_t)f'(X_t)]dt+f(X_t)dB_t
$$
Here, $a(t,X_t) = qf(X_t)+\frac{1}{2}f(X_t)f'(X_t)$, $b(t,X_t)=f(X_t)$

Then 
$$
\begin{eqnarray}
\tilde{a}(t,X_t) &=& a(t,X_t)-\frac{1}{2}f(X)f'(X) \\
&=& qf(X_t) \\
\tilde{b}(t,X_t) &=& b(t,X_t)\\
&=& f(X_t) \\
\end{eqnarray}
$$
Therefore, the corresponding SDE in Stratonovich is
$$
dX_t = qf(X_t)dt+f(X_t) \circ dB_t
$$
Then find the analogue of the Stratonovich SDE in ODE
$$
\begin{eqnarray}
dl_t &=& qf(l_t)dt+f(l_t)dc_t \\
\frac{dl_t}{f(l_t)}  &=& qdt+dc_t \\
\int_{l_0}^{l_t}\frac{du}{f(u)}  &=& qt+c_t -c_0 \\
g(l_t)-g(l_0) &=& qt + c_t - c_0 \\
\end{eqnarray}
$$
And change it back to SDE
$$
\begin{eqnarray}
g(X_t) &=& g(X_0) + qt + B_t - B_0 \\
&=& g(X_0) + qt + B_t \\
X_t &=& g^{-1}(g(X_0) + qt + B_t - B_0)
\end{eqnarray}
$$

#### Example 4 Ornstein-Uhlenbeck Process

$$
X_t = X_0 + c\int_{0}^{t}X_sds + \sigma\int_{0}^{t}dB_s
$$

$X_0$ is not random. It is also called __Langevin Equation__. The differential form is
$$
dX_t = cX_tdt+\sigma dB_t
$$

##### Time-series

If $dt$ = 1, then the Ornstein-Uhlenbeck Process become
$$
X_{t+1}-X_t = cX_t+\sigma(B_{t+1}-B_{t}) \\
X_{t+1} = (c+1)X_t+\sigma(B_{t+1}-B_{t})
$$
if we define $\phi = c+1, \epsilon_t = \sigma(B_{t+1}-B_{t}) \sim N(0,\sigma^2)$, then
$$
X_{t+1}=\phi X_t+\epsilon_t
$$
This is Autoregressive Model with order 1.

##### Solution to Ornstein-Uhlenbeck Process

solve $dX_t = cX_tdt+\sigma dB_t$, $X_0$ is deterministic.

Step 1: Define $Y_t = f(t,X_t) = e^{-ct}X_t$, we can easily get $f_t = -ce^{-ct}X_t$, $f_X = e^{-ct}$, $f_{XX}=0$. 

Step 2: According Ito formula:
$$
\begin{eqnarray}
dY_t = df(t,X_t) &=& -ce^{-ct}X_tdt +  e^{-ct}dX_t + \frac{1}{2} \times0 \times dt \\
&=& -ce^{-ct}X_tdt +  e^{-ct}(cX_tdt+\sigma dB_t) \\
&=& -ce^{-ct}X_tdt +  e^{-ct}(cX_tdt+\sigma dB_t) \\
&=& e^{-ct}\sigma dB_t
\end{eqnarray}
$$

> How to find the function like $e^{-ct}$?
>
> Let $Y_t = f(t,X_t) = P_tX_t$, we can easily get $f_t = X_tP'_t$, $f_X = P_t$, $f_{XX}=0$, then by Ito formula
> $$
> \begin{eqnarray}
> dY_t = df(t,X_t) &=& P'_tX_tdt +  P_tdX_t + \frac{1}{2} \times0 \times dt \\
> &=& P'_tX_tdt +  P_t(cX_tdt+\sigma dB_t) \\
> &=& P'_tX_tdt +  P_t(cX_tdt+\sigma dB_t) \\
> &=& (P'_t + cP_t) X_tdt+ P_t\sigma dB_t
> \end{eqnarray}
> $$
> We want to eliminate the drift term $(P'_t + cP_t) X_tdt$ because we can solve the equation only if there is no $X_t$ in the RHS. The $X_t$ can only appear in the LHS. Therefore, let $P'_t = -cP_t$, we can easily get
> $$
> P_t = \lambda e^{-ct}
> $$

Step3: Integrate both sides
$$
\begin{eqnarray}
\int_{0}^{t}dY_s &=& \sigma\int_{0}^{t} e^{-cs} dB_s \\
Y_t -Y_0 &=& \sigma\int_{0}^{t} e^{-cs} dB_s \\
e^{-ct}X_t -X_0 &=& \sigma\int_{0}^{t} e^{-cs} dB_s \\
X_t &=& e^{ct}X_0 + \sigma e^{ct}\int_{0}^{t} e^{-cs} dB_s \\
\end{eqnarray}
$$

### General Solution to Ito SDE

Consider a general Ito SDE
$$
dX(u) = (a(u)+b(u)X(u))du + (\gamma(u)+\sigma(u)X(u))dW(u)
$$
where $a(u), b(u), \gamma(u), \sigma(u)$ are adapted to $\mathcal{F(u)}$, $u \geq 0$. $\mathcal{F(u)}$ is a generated $\sigma$-algebra, which means that all the events in the Borel set can be found in $\mathcal{F(u)}$. In the finance, this means that it contains all the information at $u$.

Let
$$
\begin{eqnarray}
Z(u) &=& e^{\int_{t}^{u}\sigma(v)dW(v)+\int_{t}^{u}(b(v)-\frac{1}{2}\sigma^2(v))dv} = e^{Q(u)} \\
Y(u) &=& X + \int_{t}^{u}\frac{a(v)-\sigma(v)\gamma(v)}{Z(v)}dv + \int_{t}^{u}\frac{\gamma(v)}{Z(v)}dW(v)
\end{eqnarray}
$$
where $0 \leq t \leq u$.

When $Z(t) = 1$, then
$$
\begin{eqnarray}
dZ(u) &=& de^{Q(u)} = e^{Q(u)}dQ(u) + \frac{1}{2}e^{Q(u)}dQ(u)dQ(u) \\
&=& Z(u)[\sigma(u)dW(u)+(b(u)-\frac{1}{2}\sigma^2(u))du]+\frac{1}{2}Z(u)\sigma^2(u)du \\
&=& Z(u)\sigma(u)dW(u) + Z(u)b(u)du
\end{eqnarray}
$$
which is generalized geometric Brownian Motion.
$$
\begin{eqnarray}
dY(u) &=& \frac{a(u)-\sigma(u)\gamma(u)}{Z(u)}du + \frac{\gamma(u)}{Z(u)}dW(u)
\end{eqnarray}
$$
Because
$$
\begin{eqnarray}
dX(u) &=& d[Y(u)Z(u)] = Z(u)dY(u) + Y(u)dZ(u) + dZ(u)dY(u) \\
&=& (a(u)-\sigma(u)\gamma(u))du + \gamma(u)dW(u) \\
&+& Y(u)Z(u)(\sigma(u)dW(u) +b(u)du) \\
&+& \sigma(u)\gamma(u)du \\
&=& (a(u)-\sigma(u)\gamma(u)+b(u)Y(u)Z(u)+\sigma(u)\gamma(u))du + (\gamma(u)+Y(u)Z(u)\sigma(u))dW(u) \\
&=& (a(u)+b(u)X(u))du + (\gamma(u)+\sigma(u)X(u))dW(u) \\
\end{eqnarray}
$$
The solution is
$$
X(u) = Y(u)Z(u)
$$


According the Lipschitz Condition, let $m(t,X) = a(t)+b(t)X(t)$, $n(t,X) = \gamma(u)+\sigma(u)X(u)$, then solve the inequity:
$$
\begin{eqnarray}
|m(t,X)-m(t,Y)|+|n(t,X)-n(t,Y)| &\leq& k|X-Y| \\
|b(t)+\sigma(t)||X-Y| &\leq& k|X-Y| \\
|b(t)+\sigma(t)| &\leq& k
\end{eqnarray}
$$
In $0 \leq t \leq T$, $b(t)$ and $\sigma(t)$ should be bounded.

Therefore, the solution is the unique strong solution.

## Feynman-Kac Formula
---
title: Optimal Control Introduction
date: 2020-12-14
tags: 
	- Optimization
categories: 
	- Mathematics
	- Applied
	- Optimization
mathjax: true
---
1. $x_0$ is given

$$
\max_{x} \int_{0}^{\infty}f(x(t), x'(t), t)dt
$$

Here we refer to $x$ as the state variable.

2. Optimal control approach:

$u = x'$

We can rewrite out problem as follows:
$$
\max_{x} \int_{0}^{\infty}f(x(t), u(t), t)dt
$$
s.t.
$$
u = x'
$$
$x_0$ is given.

3. We can generalize it as

$$
\max_{x} \int_{0}^{\infty}f(x(t), x'(t), t)dt
$$

s.t.
$$
u = g(x(t), u(t), t)
$$
$x_0$ is given.

4. The problem is transformed into
   $$
   f(x(t), g(x(t), u(t), t), t) = \tilde f(x(t), u(t), t)
   $$



How are we going to solve this? In 3 steps:

### Observation

for any state variable $x$, control $u$ and any continuously differentiable $\lambda$:
$$
\begin{eqnarray*}
\int_{0}^{\infty} f(x(t), u(t), t)dt &=& \int_{0}^{\infty} [f(x(t), u(t), t) + \lambda(t)g(x(t), u(t), t) - \lambda(t)x'(t)] dt \\
&=& \int_{0}^{\infty} [f(x(t), u(t), t) + \lambda(t)g(x(t), u(t), t)]dt -\int_{0}^{\infty} \lambda(t)x'(t) dt
\end{eqnarray*}
$$
Integrate the last term by parts, between $0$ and $T$
$$
\begin{eqnarray*}
-\int_{0}^{T}\lambda(t)x'(t)dt = -[\lambda(t)x(t)]_{0}^{T}+\int_{0}^{T}\lambda'(t)x(t)dt
\end{eqnarray*}
$$

Take the limit as $T \to \infty$
$$
\begin{eqnarray*}
-\int_{0}^{T}\lambda(t)x'(t)dt = [\lambda(0)x(0) - \lambda(T)x(T)] + \int_{0}^{T}\lambda'(t)x(t)dt
\end{eqnarray*}
$$

$$
-\int_{0}^{\infty}\lambda(t)x'(t)dt = [\lambda(0)x(0) - \lim_{T \to \infty}\lambda(T)x(T)] + \int_{0}^{\infty}\lambda'(t)x(t)dt
$$

Therefore,
$$
\begin{eqnarray*}
\int_{0}^{\infty} f(x(t), u(t), t)dt 
&=& \int_{0}^{\infty} [f(x(t), u(t), t) + \lambda(t)g(x(t), u(t), t)]dt -\int_{0}^{\infty} \lambda(t)x'(t) dt \\
&=& \int_{0}^{\infty} [f(x(t), u(t), t) + \lambda(t)g(x(t), u(t), t)]dt \\
&+& [\lambda(0)x(0) - \lim_{T \to \infty}\lambda(T)x(T)] + \int_{0}^{\infty}\lambda'(t)x(t)dt
\end{eqnarray*}
$$

## Optimization

Next, let $x^*$ be an optimal path for $x_1$ and let $u^*$ be the corresponding control variable. Consider some differentiable function $h$, along with some real number $a$. Consider an alternative control variable $u^*+ah$. Call $u^*+ah$ a variation. Let $y(t, a)$ equal the path of the state variable induced by our variation.

Define the value of our objective function as a function of $a$
$$
J(a) \equiv \int_{0}^{\infty}f(y(t,a), u^*(t) + ah(t), t)dt
$$
Now using some $\lambda$ we can rewrite this as follows:
$$
\begin{eqnarray}
J(a) &\equiv& \int_{0}^{\infty} [f(y(t,a), u^*(t) + ah(t), t) +\lambda(t)g(y(t,a), u^*(t)+ah(t), t)] dt \\
&+& \lambda(0)x(0) - \lim_{T \to \infty}\lambda(T)y(T, a) + \int_{0}^{\infty}\lambda'(t)y(t, a)dt
\end{eqnarray}
$$
Since $u^*$ maximizes our objective function, it must be that $J'(0) = 0$.
$$
\begin{eqnarray}
J'(a) &\equiv& \int_{0}^{\infty} [f_x y_a + f_uh_t + \lambda(t)g_xy_a + \lambda(t)g_uh_t ] dt \\
&-& \lim_{T \to \infty}\lambda(T)y_a(T, a) + \int_{0}^{\infty}\lambda'(t)y_a(t, a)dt
\\
&=& \int_{0}^{\infty} [(f_x + \lambda(t)g_x + \lambda'(t))y_a + (f_u + \lambda(t)g_u) h_t ] dt - \lim_{T \to \infty}\lambda(T)y_a(T, a)
\end{eqnarray}
$$
Next we make an intelligent choice of $\lambda(t).$

Define $\lambda$ so that 
$$
\lambda'(t) = -f_x - \lambda(t)g_x
$$

$$
\lim_{T \to \infty}\lambda(T) = 0
$$

where the derivatives are evaluated at $x^*$. Plug this into the expression for $J'(0)$:
$$
\begin{eqnarray}
J'(0) = \int_{0}^{\infty} [(f_u + \lambda(t)g_u) h_t ] dt
\end{eqnarray}
$$
Set it to $0$

We have 
$$
\begin{eqnarray}
J'(0) = \int_{0}^{\infty} [(f_u + \lambda(t)g_u) h_t ] dt = 0
\end{eqnarray}
$$
Next, we make an intelligent choice of $h$, suppose $h(t) = f_u + \lambda g_u$
$$
\int_{0}^{\infty} (f_u + \lambda(t)g_u)^2 dt = 0
$$
The only way this can be true is
$$
\forall  t \\
f_u + \lambda(t)g_u = 0
$$
We have shown that for optimal $x^*$ and $u^*$, there exists a function $\lambda$ such that together they satisfy:

The State equation:
$$
x'(t) = g(x(t), u(t), t)
$$
$x_0$ is given.

The Costate equation
$$
\lambda'(t) = -f_x - \lambda(t)g_x, \lim_{T\to\infty}\lambda(T) = 0
$$
The Optimality condition:
$$
f_u + \lambda(t)g_u = 0 ~~ \forall t
$$
A mnemonic device to recover these conditions: the Hamiltonian:
$$
H(x, u ,t) = f(x, u ,t) + \lambda g(x, u, t)
$$
The solution necessarily satisfies these conditions:
$$
\frac{\partial H}{\partial u} = 0
$$

$$
\frac{\partial H}{\partial x} = -\lambda'
$$

$$
\frac{\partial H}{\partial \lambda} = x'
$$

Solve:
$$
\frac{\partial H}{\partial u} = 0 ~ \Rightarrow ~ f_u + \lambda(t)g_u = 0
$$
This is the optimality condition!
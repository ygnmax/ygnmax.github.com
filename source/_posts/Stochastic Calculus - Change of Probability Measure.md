---
title: Change of Probability Measure
date: 2020-08-13
tags: 
	- Probability
	- Stochastic Calculus
categories: 
	- Mathematics
	- Probability
	- Stochastic Calculus
mathjax: true
---

# Probability Measure Change

## Example

|            | $\mathbb{P(\omega)}$ | $\mathbb{Q(\omega)}$ | $\frac{\mathbb{Q(\omega)}}{\mathbb{P(\omega)}} = Z(\omega)$ |
| ---------- | -------------------- | -------------------- | ----------------------------------------------------------- |
| $\omega_1$ | $\frac{1}{3}$        | $\frac{1}{6}$        | $\frac{1}{2}$                                               |
| $\omega_2$ | $\frac{1}{3}$        | $\frac{1}{12}$       | $\frac{1}{4}$                                               |
| $\omega_3$ | $\frac{1}{3}$        | $\frac{3}{4}$        | $\frac{9}{4}$                                               |
| sum        | $1$                  | $1$                  |                                                             |

$$
\begin{eqnarray}
\mathbb{E}^{\mathbb{P}}[Z(\omega)] &=& \sum_{k=1}^{3}Z(\omega_k)\mathbb{P}(\omega_k) \\
&=& \frac{1}{2} \times \frac{1}{3} + \frac{1}{4} \times \frac{1}{3} + \frac{9}{4} \times \frac{1}{3} \\
&=& 1
\end{eqnarray}
$$

Consider a random variable $X(\omega) \geq 0$, $X(\omega_k) = X_k, k \in \{1,2,3\}$
$$
\begin{eqnarray}
\mathbb{E}^\mathbb{Q}[X] &=& X_1 \times \frac{1}{6} + X_2 \times \frac{1}{12} + X_3 \times\frac{3}{4} \\
\mathbb{E}^\mathbb{P}[XZ] &=&  \frac{1}{3} \times X_1 \times \frac{1}{2} + \frac{1}{3} \times X_2 \times \frac{1}{4} + \frac{1}{3} \times X_3 \times\frac{9}{4}
\end{eqnarray}
$$
We have $\mathbb{E}^\mathbb{Q}[X] = \mathbb{E}^\mathbb{P}[XZ]$. If $Z > 0$, then $\mathbb{E}^\mathbb{P}[X] = \mathbb{E}^\mathbb{Q}\left[\frac{X}{Z}\right]$.



## Equivalent Probability Measure

Two probability measures $\mathbb{P}$ and $\mathbb{Q}$ are defined on $(\Omega, \mathscr{F})$.  $\mathbb{P}$ and $\mathbb{Q}$ are said to be equivalent if they agree which sets in $\mathscr{F}$ have probability zero.



## Radon–Nikodym Derivative

### Definition & Theorem 

Let $(\Omega,\mathscr{F},\mathbb{P})$ be a probability space. Let $Z(\omega) \geq 0$ almost sure, with $\mathbb{E}^{\mathbb{P}}[Z(\omega)] = 1$. For $A \in \mathscr{F}$, define $\mathbb{Q}(A) = \int_{A}Z(\omega)\mathbb{P}(\omega)$. If $Z(\omega)$ is discrete, then $\mathbb{Q}(A) = \sum\limits_{\omega \in A}Z(\omega)\mathbb{P}(\omega)$. Then $\mathbb{Q}$ is a probability measure. 

If $X(\omega) \geq 0$, then 
$$
\mathbb{E}^{\mathbb{Q}}[X] = \mathbb{E}^{\mathbb{P}}[XZ]
$$
If $ Z(\omega) \geq 0$, then 
$$
\mathbb{E}^{\mathbb{P}}[X] = \mathbb{E}^{\mathbb{Q}}\left[\frac{X}{Z}\right]
$$
The $Z(w)$ is called **Radon–Nikodym derivative**. And $Z(\omega)$ denotes 
$$
Z(\omega) = \frac{d\mathbb{Q(\omega)}}{d\mathbb{P(\omega)}}
$$
Note that to change the probability measure, we require the condition  $\mathbb{E}^{\mathbb{P}}[Z(\omega)] = 1$. If we want to change other kind of measure, the expectation don't have to be 1.

### Example

1. __Uniform Distribution__

   $\Omega = [0,1], A = [a,b] \in \mathscr{F},  0 \leq a \leq b \leq 1$, 

+ a uniform measure $\mathbb{P}([a,b]) = b-a$, $P([0,1]) = 1$

+ a new measure $\mathbb{Q}([a,b]) = b^2-a^2$, $Q([0,1]) = 1$ 

  Then

$$
Z(\omega) = \frac{d\mathbb{Q(\omega)}}{d\mathbb{P(\omega)}} = \frac{\mathbb{Q}([\omega, \omega+\Delta\omega])}{\mathbb{P}([\omega, \omega+\Delta\omega])} = \frac{(\omega+\Delta\omega)^2 - \omega^2}{\omega+\Delta\omega - \omega} = 2\omega+\Delta\omega
$$

​		if the small interval is going to 0, we get
$$
Z(\omega) = \frac{d\mathbb{Q(\omega)}}{d\mathbb{P(\omega)}}  = 2\omega
$$
​	__2. Normal Distribution__

+ Under an original measure $\mathbb{P}$, an normal random variable $ Y \sim N^{\mathbb{P}}(\theta,1)$

+ find a new measure $\mathbb{Q}$,  $Y \sim N^{\mathbb{Q}}(0,1)$

  > About the standard normal distribution, the pdf is
  > $$
  > \phi(x) = \frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}, x \in \mathbb{R}
  > $$
  > the cdf is
  > $$
  > \Phi(x) = \int_{-\infty}^{x} \frac{1}{\sqrt{2\pi}}e^{-\frac{s^2}{2}}ds
  > $$

  __Step 1:__ Under the probability space $(\Omega=\mathbb{R}, \mathscr{F}, \mathbb{P})$,  where events $\omega$ are real numbers, $\omega \sim N(0,1)$. Consider a standard normal random variable $X(\omega) = \omega \sim N(0,1)$,
  $$
  \begin{eqnarray}
  \Delta \mathbb{P}(l) &=& \mathbb{P}(l \leq \omega \leq l+\Delta l) \\
  &=& \mathbb{\Phi}(l+\Delta l) - \mathbb{\Phi}(l) \tag{1}
  \end{eqnarray}
  $$
  __Step 2:__ The original random variable $Y(\omega)$ can be regarded as  $Y(\omega) = X(\omega) + \theta = \omega + \theta$ under $\mathbb{P}$.

  __Step 3:__ Under $\mathbb{Q},~ Y \sim N^{\mathbb{Q}}(0,1)$, consider
  $$
  \begin{eqnarray}
  \mathbb{Q}(l \leq Y(\omega) \leq l+\Delta l) &=& \mathbb{\Phi}(l+\Delta l) - \mathbb{\Phi}(l) \\
  \mathbb{Q}(l \leq \omega+\theta \leq l+\Delta l) &=& \mathbb{\Phi}(l+\Delta l) - \mathbb{\Phi}(l) \\
  \mathbb{Q}(l-\theta \leq \omega \leq l+\Delta l-\theta ) &=& \mathbb{\Phi}(l+\Delta l) - \mathbb{\Phi}(l) \\
  \end{eqnarray}
  $$
   Here, $l$ can be any number. 

  __Step 4:__ We change $l \to l+\theta$ and get
  $$
  \begin{eqnarray}
  \mathbb{Q}(l \leq \omega \leq l+\Delta l ) &=& \mathbb{\Phi}(l+\theta+\Delta l) - \mathbb{\Phi}(l+\theta) \\
  \Delta\mathbb{Q}(l) &=& \mathbb{\Phi}(l+\theta+\Delta l) - \mathbb{\Phi}(l+\theta) \tag{2}
  \end{eqnarray}
  $$
  __Step 5:__ do the calculation
  $$
  \begin{eqnarray}
  Z(l) &=& \frac{d\mathbb{Q}}{d\mathbb{P}}(l) = \lim_{\Delta l \to 0}\frac{\Delta \mathbb{Q}}{\Delta \mathbb{P}} \\
  &=&  \lim_{\Delta l \to 0}\frac{\mathbb{\Phi}(l+\theta+\Delta l) - \mathbb{\Phi}(l+\theta)}{\mathbb{\Phi}(l+\Delta l) - \mathbb{\Phi}(l)} \\
  &=&  \lim_{\Delta l \to 0}\frac{\mathbb{\phi}(l+\theta+\Delta l) }{\mathbb{\phi}(l+\Delta l)} \\
  &=&  \frac{\mathbb{\phi}(l+\theta) }{\mathbb{\phi}(l)} \\
  Z(\omega) &=& \frac{\mathbb{\phi}(\omega+\theta) }{\mathbb{\phi}(\omega)} \\
  &=& \frac{\frac{1}{\sqrt{2\pi}}e^{-\frac{(\omega+\theta) ^2}{2}}}{\frac{1}{\sqrt{2\pi}}e^{-\frac{\omega^2}{2}}} \\
  &=& e^{-\frac{(\omega+\theta) ^2}{2}+\frac{\omega^2}{2}} \\
  &=& e^{-\frac{\theta^2}{2}-\omega\theta} \\
  &=& e^{-\frac{\theta^2}{2}-X(\omega)\theta} \\
  \end{eqnarray}
  $$
  This is an exponential martingale. 

# Novikov Condition

A process $\Theta$ satisfies the Novikov Condition if 
$$
\mathbb{E}\left[ e^{\frac{1}{2}\int_{0}^{T}\Theta_s^2ds}\right] < \infty
$$
and if Novikov Condition is satisfied, then the process $M^{\Theta}$ defined as
$$
M_t^{\Theta} = e^{-\int_{0}^{t}\Theta_sdX_s - \frac{1}{2}\int_{0}^{t}\Theta^2_sds}, t \in [0,T]
$$
is a martingale.



# Girsanov's Theorem

## Radon–Nikodym Derivative process

$Z(t) = \mathbb{E}[Z|\mathcal{F}(t)]$, $0\leq t \leq T$. We consider it as a Radon–Nikodym Derivative process.

+ $Z(t)$ is a martingale

> Two ways to prove martingale:
>
> 1. $ \mathbb{E}[W(t)|\mathcal{F}(s)] = W(s)$
> 2. $dX(t) = a(t,X(t))dW(t)$

$$
\begin{eqnarray}
\mathbb{E}[Z(t)|\mathcal{F}(s)] &=& \mathbb{E}[\mathbb{E}[Z|\mathcal{F}(t)]|\mathcal{F(s)}] \\
&=& \mathbb{E}[Z|\mathcal{F}(s)]
\end{eqnarray}
$$

+ $Z(\omega)$ is a Radon–Nikodym Derivative, we have
  $$
  \mathbb{E}^{\mathbb{Q}}[Y] = \mathbb{E}^{\mathbb{P}}[YZ]
  $$
  If $Y$ is $\mathcal{F}(t)$-measurable, then
  $$
  \mathbb{E}^{\mathbb{Q}}[Y] = \mathbb{E}^{\mathbb{P}}[YZ(t)] \\
  $$

+ If If $Y$ is $\mathcal{F}(t)$-measurable, $0 \leq s \leq t \leq T$, then
  $$
  \mathbb{E}^{\mathbb{Q}}[Y|\mathcal{F}(s)] = \frac{1}{Z(s)}\mathbb{E}^{\mathbb{P}}[YZ(t)|\mathcal{F}(s)]
  $$
  __proof:__

  Both $Z(s)$ and $\mathbb{E}^{\mathbb{P}}[YZ(t)|\mathcal{F}(s)]$ are $\mathcal{F}(s)$-measurable. We want to show that it is consistent with the definition of conditional expectation. Therefore, for any $A \in \mathcal{F(s)}$, we have
  $$
  \begin{eqnarray}
  \int_{\Omega} \mathbb{I}_{A}(\omega) \frac{1}{Z(s)}\mathbb{E}^{\mathbb{P}}[YZ(t)|\mathcal{F}(s)]d\mathbb{Q}(\omega) &=& \mathbb{E}^{\mathbb{Q}}\left[ \mathbb{I}_{A}(\omega) \frac{1}{Z(s)}\mathbb{E}^{\mathbb{P}}[YZ(t)|\mathcal{F}(s)]\right] \\
  &=& \mathbb{E}^{\mathbb{P}}\left[ \mathbb{I}_{A}(\omega)\mathbb{E}^{\mathbb{P}}[YZ(t)|\mathcal{F}(s)]\right] \\
  &=& \mathbb{E}^{\mathbb{P}}\left[ \mathbb{E}^{\mathbb{P}}[\mathbb{I}_{A}(\omega)YZ(t)|\mathcal{F}(s)]\right] \\
  &=& \mathbb{E}^{\mathbb{P}}\left[\mathbb{I}_{A}(\omega)YZ(t)\right] \\
  &=& \mathbb{E}^{\mathbb{Q}}\left[\mathbb{I}_{A}(\omega)Y\right] \\
  &=& \int_{\Omega} \mathbb{I}_{A}(\omega) Y(\omega)d\mathbb{Q}(\omega) \\
  &=& \int_{A} Y(\omega)d\mathbb{Q}(\omega) \\
  \end{eqnarray}
  $$
  
+ 





## Girsanov's Theorem in Finance

Let $W(t)$ be a Brownian Motion on $(\Omega, \mathcal{F}, \mathbb{P})$ and let $\mathcal{F}$ be a filtration for the Brownian Motion. Let $\Theta(t)$ be an adapted process and satisfied the _Novikov Condition_. Define
$$
Z(t) = e^{-\int_{0}^{t}\Theta(u)dW(u)-\frac{1}{2}\int_{0}^{t}\Theta^2(u)du} \\
\widetilde{W}(t) = W(t) + \int_{0}^{t}\Theta(u)du
$$
Set $Z = Z(T)$, then $\mathbb{E}Z = 1, Z \geq 0$, and under $\mathbb{Q}$ given by
$$
\mathbb{Q}(A) = \int_{A}Z(\omega)d\mathbb{P}(\omega), \forall A \in \mathcal{F}
$$
the process $\widetilde{W}(t)$ is a Brownian Motion.

__Proof__

Step 1 : prove Z(t) can be a Radon–Nikodym derivative, which means that we need to show the expectation $\mathbb{E}Z = 1$. 

1.1 We want to prove that $Z(t)$ is a martingale:
$$
\begin{eqnarray}
Z(t) &=& e^{-\int_{0}^{t}\Theta(u)dW(u)-\frac{1}{2}\int_{0}^{t}\Theta^2(u)du} = e^{X(t)} \\
dZ(t) &=&  e^{X(t)}dX(t) + \frac{1}{2} e^{X}dX(t)dX(t) \\
&=&Z(t)[-\Theta(t)dW(t)-\frac{1}{2}\Theta^2(t)dt] + \frac{1}{2}Z(t)\Theta^2(t)dt \\
&=&-Z(t)\Theta(t)dW(t)
\end{eqnarray}
$$
Therefore, $Z(t)$ is a $\mathbb{P}$-martingale. $Z(t)= Z(0)+\int_{0}^{t}\Theta(u)Z(u)dW(u)$. 

1.2 And we can verify the expectation
$$
\mathbb{E}^{\mathbb{P}}[Z] =\mathbb{E}^{\mathbb{P}}[Z(T)] = \mathbb{E}^{\mathbb{P}}[Z(T)|\mathcal{F}(0)] = Z(0) = 1
$$
Step 2: prove  $\widetilde{W}(t)$ is a Brownian Motion. We need use the Levy' theorem to show $\widetilde{W}(t)$ is a Brownian Motion.

+ Initial Value:
  $$
  \widetilde{W}(0) = W(0) + \int_{0}^{0}\Theta(u)du = 0
  $$

+ Continuous: obvious

+ Quadratic Variation:

  Because
  $$
  \widetilde{W}(t) = W(t) + \int_{0}^{t}\Theta(u)du \\
  d\widetilde{W}(t) = dW(t) + \Theta(t)dt
  $$
  only $dW(t)$ can accumulate variation. Therefore 
  $$
  [\widetilde{W}, \widetilde{W}](t) = [{W}, {W}](t) = t
  $$
  
+ Martingale: we want to show that $\mathbb{E}^{\mathbb{Q}}[\widetilde{W}(t)|\mathcal{F(s)}] = \widetilde{W}(s)$

  For $0 \leq s \leq t \leq T$
  $$
  \mathbb{E}^{\mathbb{Q}}[\widetilde{W}(t)|\mathcal{F(s)}] = \frac{1}{Z(s)}\mathbb{E}^{\mathbb{P}}[\widetilde{W}(t)Z(t)|\mathcal{F}(s)]
  $$
  Because
  $$
  \begin{eqnarray}
  d\widetilde{W}(t)Z(t) &=& Z(t)d\widetilde{W}(t) + \widetilde{W}(t)dZ(t) + dZ(t)d\widetilde{W}(t) \\
  &=& Z(t)[dW(t) + \Theta(t)dt]+ \widetilde{W}(t)[-Z(t)\Theta(t)dW(t)] + [-Z(t)\Theta(t)dW(t)][dW(t) + \Theta(t)dt] \\
  &=& Z(t)(1-\widetilde{W}(t)\Theta(t))dW(t)
  \end{eqnarray}
  $$
  $\widetilde{W}(t)Z(t)$ is a $\mathbb{P}$-martingale. We have
  $$
  \mathbb{E}^{\mathbb{Q}}[\widetilde{W}(t)|\mathcal{F(s)}] = \frac{1}{Z(s)}\mathbb{E}^{\mathbb{P}}[\widetilde{W}(t)Z(t)|\mathcal{F}(s)] = \frac{1}{Z(s)}[\widetilde{W}(s)Z(s)] = \widetilde{W}(s)
  $$
  And $\widetilde{W}(t)$ is a $\mathbb{Q}$-martingale.

## Giranov's Theorem in General

Consider a SDE 
$$
dX_t = f(X_t)dt + \sigma(X_t)dW_t
$$
Let $f^*(X)$ be a new drift function. Assume $\frac{f^*(X)-f(X)}{\sigma(X)}$ is bounded. Define the measure $P^*$ by 
$$
\frac{d\mathbb{P}^*}{d\mathbb{P}}(\omega)|_{\mathcal{F_t}} = e^{\int_{0}^{t}\frac{f^*(X_u)-f(X_u)}{\sigma(X_u)}dW(u)-\frac{1}{2}\int_{0}^{t}(\frac{f^*(X_u)-f(X_u)}{\sigma(X_u)})^2(u)du}
$$
Then $\mathbb{P}^*$ is equivalent to $\mathbb{P}$. Moreover, the process $W^*$_t 
$$
dW^*_t = -\frac{f^*(X_t)-f(X_t)}{\sigma(X_t)}dt+dW_t
$$
is a Brownian Motion under $\mathbb{P}^*$ and 
$$
dX_t = f^*(X_t)dt + \sigma(X_t)dW^*_t
$$

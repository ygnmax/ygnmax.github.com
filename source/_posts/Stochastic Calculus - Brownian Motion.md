---
title: Brownian Motion
date: 2020-08-11
update: 2020-08-12
tags: 
	- Finance
	- Asset Pricing
	- Brownian Motion
categories: 
	- Mathematics
	- Probability
	- Stochastic Calculus
---

# Definition of Brownian Motion

## Symmetric Random Walk

Consider that we toss a fair coin independently for each time. The initial position  $M_0 = 0$. A random variable $X_j$ is defined as
$$
X_j = \begin{cases}
1 ~~~\text{if H, where $P(H) = \frac{1}{2}$} \\
-1 ~~~\text{if T, where $P(T) = \frac{1}{2}$}
\end{cases}
$$
Then the position after $k$ tosses can be expressed as:
$$
M_k = M_0 + \sum_{i=1}^{k}X_j, k = 1, 2, 3 \cdots
$$
Here, $X_j$ are independent. $\mathbb{E}[X_j] = 0, \mathbb{Var}[X_j] = 1$.

### Independent Increments

+ For $0 = k_0<k_1<\cdots<k_m$, $M_{k_1} - M_{k_0}, M_{k_2} - M_{k_1}, \cdots, M_{k_m} - M_{k_{m-1}}$ are independent.

+ For any two time point $i$ and $i+1$ (toss time $k_{i+1}$ and $k_{i}$), $M_{k_i+1} - M_{k_{i}} = \sum\limits_{j=k_i+1}^{k_{i+1}}X_j$

### Moments

$$
\begin{eqnarray}
\mathbb{E}[M_{k_{i+1}}-M_{k_{i}}] &=& 0 \\
\mathbb{Var}[M_{k_{i+1}}-M_{k_{i}}] &=& \mathbb{Var}\left[\sum\limits_{j=k_i+1}^{k_{i+1}}X_j\right] = \left[\sum\limits_{j=k_i+1}^{k_{i+1}}\mathbb{Var}[X_j]\right] = k_{i+1}-k_i
\end{eqnarray}
$$

### Martingale Property

$ \forall k < l$, 
$$
\begin{eqnarray}
\mathbb{E}[M_l|\mathscr{F_k}] &=& \mathbb{E}[M_l - M_k+M_k|\mathscr{F_k}] \\
&=& \mathbb{E}[M_l-M_k|\mathscr{F_k}] + \mathbb{E}[M_k|\mathscr{F_k}] \\
&=& \mathbb{E}[M_l-M_k] + M_k \\
&=& M_k
\end{eqnarray}
$$
here, $\mathscr{F_k}$ contains all the information at time $k$. Therefore, $\mathbb{E}[M_k|\mathscr{F_k}]$ is a constant $M_k$, $\mathbb{E}[M_l-M_k|\mathscr{F_k}]$ only depends on the time interval $(k,l)$, which is dependent to $(0,k]$. 

### Quadratic Variation

$$
[M,M]_k = \sum\limits_{j=1}^{k}(M_j-M_{j-1})^2 =\sum\limits_{j=1}^{k}(X_j)^2 = \sum\limits_{j=1}^{k}1 = k
$$

+ Quadratic variation is calculated by one path.
+ Variance of the increments is calculated by every path.

$$
\mathbb{Var}[M_{j}-M_{0}] =\mathbb{Var}\left[\sum\limits_{j=1}^{k}X_j\right] = \left[\sum\limits_{j=1}^{k}\mathbb{Var}[X_j]\right] = k
$$

## Scaled Random Walk

Now, we consider to revise the symmetric random walk. If we toss more than one times during a time interval (__speed up time__), let's say $n$ times; and after each toss, the movement is $\frac{1}{\sqrt{n}}$ or $-\frac{1}{\sqrt{n}}$ instead of $1$ or $-1$ (__scale down the step__). W^n(t) \to \text{Normal}, n \to \inftyThen the position is
$$
W^{n}(t) = \frac{1}{\sqrt{n}}M_{nt}
$$
For example,
$$
W^{100}(t) = \frac{1}{10}M_{100t}, ~~ 100t = 1,2,3,\cdots
$$
$t = 0.01, 0.02, 0.03, \cdots$ and 
$$
W^{100}(0.51) = \frac{1}{10}M_{51} = \frac{1}{10}\left(M_0+\sum_{j=1}^{51}X_j\right)
$$

### Moment

$$
\begin{eqnarray}
\mathbb{E}[W^{n}(t)-W^{n}(s)] &=& \mathbb{E}\left[\frac{1}{\sqrt{n}}M_{nt} - \frac{1}{\sqrt{n}}M_{ns}\right] \\
&=& \mathbb{E}\left[\frac{1}{\sqrt{n}}\sum_{j=ns+1}^{nt}X_j\right] \\
&=& \frac{1}{\sqrt{n}}\sum_{j=ns+1}^{nt}\mathbb{E}\left[X_j\right] = 0 \\
\mathbb{Var}[W^{n}(t)-W^{n}(s)] &=& \mathbb{Var}\left[\frac{1}{\sqrt{n}}M_{nt} - \frac{1}{\sqrt{n}}M_{ns}\right] \\
&=& \frac{1}{n}\mathbb{Var}[M_{nt}-M_{ns}] \\
&=& \frac{nt-ns}{n} = t-s
\end{eqnarray}
$$

### Independent Increments

### Martingale Property

$\forall s < t$
$$
\mathbb{E}[W^{n}(t)|\mathscr{F}_s] = W^{n}(s)
$$
$\mathscr{F_s}$ is the $\sigma$-algebra of information available at time $s$, which is the knowledge of the first $ns$ coin tosses. Here, $W^{n}(s)$ depends only on the first $ns$ coin tosses, so $W^{n}(s)$ is $\mathscr{F_s}$-measurable.

### Quadratic Variation

$$
\begin{eqnarray}
[W^{n},W^{n}](t) &=& \sum_{i=1}^{nt}\left(W^{n}\left(\frac{i}{n}\right)-W^{n}\left(\frac{i-1}{n}\right)\right)^2 \\
&=& \sum_{i=1}^{nt}\left[\frac{1}{\sqrt{n}}(M_i-M_{i-1}) \right]^2 \\
&=& \sum_{i=1}^{nt}\left[\frac{1}{\sqrt{n}}X_i \right]^2 = nt \times\frac{1}{n} = t
\end{eqnarray}
$$



## Brownian Motion

Now, when the $n \to \infty$, the scaled random walk is going to be Brownian Motion. That is to say,
$$
W^n(t) \to \text{Normal}, n \to \infty
$$

### Proof

+ Calculate the Moment Generating Function (MGF) of $W^n(t)$
  $$
  \begin{eqnarray}
  \phi_n(u) &=& \mathbb{E}\left[e^{uW^n(t)}\right] = \mathbb{E}\left[e^{u\frac{1}{\sqrt{n}}M_{nt}}\right] \\
  &=& \mathbb{E}\left[e^{\frac{u}{\sqrt{n}}(X_1+X_2+\cdots+X_{nt})}\right] \\
  &=& \mathbb{E}\left[e^{\frac{u}{\sqrt{n}}X_1}e^{\frac{u}{\sqrt{n}}X_2}\cdots e^{\frac{u}{\sqrt{n}}X_{nt}}\right]  
  \end{eqnarray}
  $$
  Here, because $X_j$ are independent, the expectation can be split into each term
  $$
  \begin{eqnarray}
  &=& \mathbb{E}\left[e^{\frac{u}{\sqrt{n}}X_1}\right] \mathbb{E}\left[e^{\frac{u}{\sqrt{n}}X_2}\right] \cdots \mathbb{E}\left[e^{\frac{u}{\sqrt{n}}X_{nt}}\right] \\
  &=& \left[\frac{1}{2}\left( e^{\frac{u}{\sqrt{n}}} + e^{-\frac{u}{\sqrt{n}}}\right)\right]^{nt}
  \end{eqnarray}
  $$

+ Take the limit of MGF of $W^{n}(t)$
  $$
  \phi_n(u) =\left[\frac{1}{2}\left( e^{\frac{u}{\sqrt{n}}} + e^{-\frac{u}{\sqrt{n}}}\right)\right]^{nt}
  $$

  $$
  \ln\phi_n(u) =nt \ln\left[\frac{1}{2}\left( e^{\frac{u}{\sqrt{n}}} + e^{-\frac{u}{\sqrt{n}}}\right)\right]
  $$

  Let $\lambda = \frac{1}{\sqrt{n}}$, then
  $$
  \ln\phi_n(u) =\frac{t}{\lambda^2}\ln\left[\frac{1}{2}\left( e^{u\lambda} + e^{-u\lambda}\right)\right]
  $$
  According to the Taylor Expansion:
  $$
  e^{u\lambda} = 1 + u\lambda + \frac{1}{2}(u\lambda)^2+o(u^2\lambda^2) \\
  e^{-u\lambda} = 1 - u\lambda + \frac{1}{2}(-u\lambda)^2+o(u^2\lambda^2) \\
  \ln\left[1 + \frac{1}{2}u^2\lambda^2\right] = \frac{1}{2}u^2\lambda^2 + o(u^2\lambda^2)
  $$
  We get
  $$
  \begin{eqnarray}
  \ln\phi_n(u) &=&\frac{t}{\lambda^2}\ln\left[1+\frac{1}{2}u^2\lambda^2+o(u^2\lambda^2)\right] \\
  &=& \frac{t}{\lambda^2} \left[\frac{1}{2}u^2\lambda^2+o(u^2\lambda^2)\right] \\
  &=& \frac{1}{2}u^2t + \frac{t}{\lambda^2}o(u^2\lambda^2) \\
  &=& \frac{1}{2}u^2t + o(\lambda^4)
  \end{eqnarray}
  $$
  When $n \to \infty$, $\lambda \to 0$, 
  $$
  \lim_{\lambda \to 0}\ln\phi_n(u) = \frac{1}{2}u^2t
  $$
  Therefore,
  $$
  \lim_{\lambda \to 0}\phi_n(u) = e^{\frac{1}{2}u^2t}
  $$

+ Consider a random variable $Y$ follows a Normal Distribution $N(0,t)$, the pdf is
  $$
  f_Y(x) = \frac{1}{\sqrt{2\pi t}}e^{-\frac{x^2}{2t}}
  $$
  the MGF of $Y \sim N(0,t)$ is
  $$
  \begin{eqnarray}
  \phi_Y(u) &=& \mathbb{E}[e^{uY}] = \int_{-\infty}^{\infty}e^{ux}\frac{1}{\sqrt{2\pi t}}e^{-\frac{x^2}{2t}}dx \\
  &=&\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi t}}e^{-\frac{(x-ut)^2}{2t}}e^{\frac{1}{2}u^2t}dx \\
  &=& e^{\frac{1}{2}u^2t} \int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi t}}e^{-\frac{(x-ut)^2}{2t}}dx \\
  &=& e^{\frac{1}{2}u^2t}
  \end{eqnarray}
  $$

+ The two MGFs are the same, so
  $$
  W^n(t) \to \text{Normal}, n \to \infty
  $$

### Definition

Consider a probability space $(\Omega, \mathscr{F}, \mathbb{P})$ and suppose there is a continuous function $w(t), t \geq 0$ that satisfies $w(0) = 0$ and depends on $w$. Then $w(t)$ is a __Brownian Motion__ if for all $0=t_0<t_1<t_2<\cdots<t_m$, the increments $w(t_1)-w(t_0), w(t_2)-w(t_1),\cdots,w(t_m)-w(t_{m-1})$ are independent and each increment is normal distribution with $\mathbb{E}[w(t_{i+1})-w(t_{i})] = 0$ and $\mathbb{Var}[w(t_{i+1})-w(t_{i})]=t_{i+1}-t_i$.

+ $w(t)-w(s) \sim N(0,t-s)$. The standard deviation is $\sqrt{t-s}$.
+ $w(t) = w(t)-w(0) \sim N(0,t)$. The standard deviation is $\sqrt{t}$.



### Filtration & Adaptivity

A filtration is a collection of $\sigma$-algebras $\mathscr{F_t}, t \geq 0$ satisfying that information accumulates, $\mathscr{F_s} \subset \mathscr{F_t}, ~~\forall s < t$

If we can use the information in $(0,s)$ to determine the $w_s$, then we call it as $\mathscr{F_s}$-measurable, which is also called adapt processes. Adaptivity is always related to a filtration.

+ Let $\Delta(t), t \geq 0$ be a stochastic process. $\Delta(t)$ is __adapted__ to a filtration $\mathscr{F_t}$ if for $\forall t \geq 0$, $\Delta(t)$ is $\mathscr{F_t}$-measurable.

### Independent Increments

$\forall 0 \leq t < u, w(u)-w(t)$ is independent of $\mathscr{F_t}$

### Martingale Property

$0 \leq s \leq t, \mathbb{E}[w(t)|\mathscr{F_s}] = w(s)$
$$
\begin{eqnarray}
\mathbb{E}[w(t)|\mathscr{F_s}] &=& \mathbb{E}[w(t)-w(s) + w(s) |\mathscr{F_s}] \\
&=& \mathbb{E}[w(t)-w(s)|\mathscr{F_s}] + \mathbb{E}[w(s) |\mathscr{F_s}] \\
&=& \mathbb{E}[w(t)-w(s)] + w(s) \\
&=& w(s)
\end{eqnarray}
$$

### Quadratic Variation

+ First-Order Variation means the up and down oscillation:

  for $t \in (0,T)$, consider two time point $t_1$ and $s_2$ satisfying $0 < t_1<t_2<T$

$$
\begin{eqnarray}
FV_T(f) &=& [f(t_1)-f(0)] - [f(t_2)-f(t_1)] + [f(T)-f(t_2))] \\
&=& \int_{0}^{t_1}f'(t)dt + \int_{t_1}^{t_2}-f'(t)dt + \int_{t_2}^{T}f'(t)dt \\
&=& \int_{0}^{T}|f'(t)|dt
\end{eqnarray}
$$

​		in general, choose a partition $\pi = {t_0, t_1,\cdots, t_n}$ where $0=t_0 < t_1<t_2<\cdots<t_n = T$. Define
$$
FV_T(f) = \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}|f(t_{j+1})-f(t_j)|, ~~~||\pi|| = \max_{1\leq j \leq n}(t_j - t_{j-1})
$$
​		As $n \to \infty$, $||\pi|| \to 0$. According to the Mean Value Theorem, $\exists ~ t_j^*$ satisfying
$$
FV_T(f) = \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}|f'(t_{j}^{*})(t_{j+1}-t_j)| = \lim_{||\pi|| \to 0}(t_{j+1}-t_j)\sum_{j=0}^{n-1}|f'(t_{j}^{*})| = \int_{0}^{T}|f'(t)|dt
$$

+ Quadratic Variation
  $$
  [f,f](T) = \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}(f(t_{j+1})-f(t_j))^2, ~~~||\pi|| = \max_{1\leq j \leq n}(t_j - t_{j-1})
  $$

  + Conclusion 1: suppose $f$ has a continuous derivative, then 
    $$
    [f,f](T)=0
    $$
    __Proof__:
    $$
    \begin{eqnarray}
  \sum_{j=0}^{n-1}(f(t_{j+1})-f(t_j))^2 &=& \sum_{j=0}^{n-1}|f'(t_{j}^{*})|^2(t_{j+1}-t_j)(t_{j+1}-t_j) \\
    &\leq& ||\pi||\sum_{j=0}^{n-1}|f'(t_{j}^{*})|^2(t_{j+1}-t_j)
    \end{eqnarray}
    $$
    
    $$
    \begin{eqnarray}
  [f,f](T) &\leq& \lim_{||\pi|| \to 0}||\pi|| \times \lim_{||\pi|| \to 0}\sum_{j=0}^{n-1}|f'(t_{j}^{*})|^2(t_{j+1}-t_j) \\
    &=& 0 \times \int_{0}^{T}|f'(t)|dt
    \end{eqnarray}
    $$
    
    because $f'(t)$ is continuous, then $\exists M>0 \in[0,T]$ s.t. $|f'(t)| \leq M < \infty$
    $$
    [f,f](T) \leq 0
    $$
    and by definition the quadratic variation should be greater than 0, we get
    $$
    [f,f](T) = 0
    $$
    
  + Conclusion 2 (quadratic variation of Brownian Motion): Let $w(t)$ be Brownian motion, then  
    $$
    \left[w,w\right](T) = T
    $$
    $\forall  T \geq 0$ almost surely.

    __Proof__:
    Let $\pi = {t_0, t_1,\cdots, t_n}$ where $0=t_0 < t_1<t_2<\cdots<t_n = T$ be a partition of $[0,T]$, and then define 
    $$
    Q_{\pi} = \sum_{j=0}^{n-1}(w(t_{j+1})-w(t_j))^2
    $$

    + Expectation
      $$
      \begin{eqnarray}
          \mathbb{E}[Q_{\pi}] &=& \sum\limits_{j=0}^{n-1}\mathbb{E}(w(t_{j+1})-w(t_j))^2 = \sum\limits_{j=0}^{n-1}\mathbb{Var}[w(t_{j+1})-w(t_j)] + (\mathbb{E}[w(t_{j+1})-w(t_j)])^2 \\
          &=& \sum\limits_{j=0}^{n-1}\mathbb{Var}[w(t_{j+1})-w(t_j)] + 0^2 \\
          &=& \sum\limits_{j=0}^{n-1}(t_{j+1}-t_{j}) = t_{n}-t_0 = T
          \end{eqnarray}
      $$

    + Variance: 

      because $w(t_{j+1})$ and $w(t_{j})$ are independent, and $w(t_{j+1})-w(t_j) \sim N(0,t_{j+1}-t_j)$ then
      $$
      \begin{eqnarray}
        \mathbb{Var}[Q_{\pi}] &=& \mathbb{Var}\left[\sum\limits_{j=0}^{n-1}(w(t_{j+1})-w(t_j))^2\right] \\
        &=& \sum\limits_{j=0}^{n-1}\mathbb{Var}[(w(t_{j+1})-w(t_j))^2] \\
        &=& \sum\limits_{j=0}^{n-1}\mathbb{E}[(w(t_{j+1})-w(t_j))^4] - \mathbb{E}^2[(w(t_{j+1})-w(t_j))^2] \\
        &=& \sum\limits_{j=0}^{n-1}\mathbb{E}[(w(t_{j+1})-w(t_j))^4] - \mathbb{Var}^2[w(t_{j+1})-w(t_j)]
        \end{eqnarray}
      $$
      Let's $Y_j = w(t_{j+1})-w(t_j) \sim N(0,t_{j+1}-t_j)$, $Q_{\pi} = Y_j^2$, then
      $$
        \begin{eqnarray}
        \mathbb{Var}[Y_j^2] &=& \sum\limits_{j=0}^{n-1}\mathbb{E}[Y_j^4] - \mathbb{Var}^2[Y_j] \\
        &=& \sum\limits_{j=0}^{n-1}\mathbb{E}[Y_j^4] - (t_{j+1}-t_j)^2
      \end{eqnarray}
      $$
      and
      $$
      \mathbb{E}[Y_j^4] = 3\mathbb{Var}^2[Y_j] = 3(t_{j+1}-t_j)^2
      $$

        > Proof:
        >
        > Because
        > $$
        > X \sim N(0,1), \mathbb{E}[X^4] = 3 \\
        > $$
        > consider $X \sim N(0,\sigma^2), $ because
        > $$
        > Y = \frac{x-0}{\sigma} \sim N(0,1) \\
        > \mathbb{E}\left[\frac{x^4}{\sigma^4}\right] = 3 \\
        > \mathbb{E}[X^4] = 3\sigma^4 \\
        > $$

      Therefore,
      $$
      \begin{eqnarray}
        \mathbb{Var}[Y_j^2] &=& 2\sum\limits_{j=0}^{n-1}(t_{j+1}-t_j)^2 \\
        &\leq& 2||\pi||\sum\limits_{j=0}^{n-1}(t_{j+1}-t_j) = 2||\pi||T
      \end{eqnarray}
      $$
      According to the Squeeze Theorem
      $$
        \lim_{\pi \to 0} \mathbb{Var}[Q_{\pi}] = 0
      $$

    + Now, we have the expectation $\mathbb{E}[Q_{\pi}] = T$ and variance $\mathbb{Var}[Q_{\pi}] = 0$ of the quadratic variance of Brownian Motion, therefore
  
  $$
  [W,W](T) = Q_{\pi} = T
  $$
  

# Some useful conclusions

## $dw(t)dw(t) = dt$

+ $\mathbb{E}[(w(t_{j+1})-w(t_{j}))^2] = \mathbb{Var}[w(t_{j+1})-w(t_{j})] = t_{j+1}-t_{j}$

+ $\mathbb{Var}[(w(t_{j+1})-w(t_{j}))^2] = 2(t_{j+1}-t_{j})^2$

+ $\lim\limits_{\pi \to 0} \sum\limits_{j=0}^{n-1}(w(t_{j+1})-w(t_j))^2 = T$

Now consider
$$
\begin{eqnarray}
\lim\limits_{\pi \to 0} \sum\limits_{j=0}^{n-1}(w(t_{j+1})-w(t_j))^2 = \lim\limits_{\pi \to 0} \sum\limits_{j=0}^{n-1}(w(t_{j+1})-w(t_j))(w(t_{j+1})-w(t_j)) = T \\
\end{eqnarray}
$$
which can be regarded as Riemann–Stieltjes integral
$$
\int_{0}^{T}dw(t)dw(t) = \int_{0}^{T}dt
$$
Here, $dw(t)$ has no definition rigorously, but it is helpful for calculation.

## $dw(t) = \epsilon \sqrt{dt}$

$dw(t) = \epsilon \sqrt{dt}$ is not a formal expression. The formal expression should be $w(t+\Delta t) - w(t) = \epsilon \sqrt{\Delta t}$

+ In a small time interval $\Delta t$
$$
w(t+\Delta t) - w(t) = \epsilon \sqrt{\Delta t}
$$

$$
w(T) = w(T)-w(0) = \epsilon\sqrt{T}
$$
+ $dw(t)$ has no definition rigorously.

## $dw(t)dt = 0$
$$
\begin{eqnarray}
\left| \sum_{j=0}^{n-1}(t_{j+1}-t_j)(w(t_{j+1})-w(t_{t_j})) \right| &\leq& \sum_{j=0}^{n-1}|t_{j+1}-t_j||w(t_{j+1})-w(t_{t_j})| \\
&\leq& \max_{0 \leq j\leq n-1}|w(t_{j+1})-w(t_{t_j})|\sum_{j=0}^{n-1}t_{j+1}-t_j
\end{eqnarray}
$$
as $||\pi|| \to 0$, $\max_{0 \leq j\leq n-1}|w(t_{j+1})-w(t_{t_j})| \to 0$
$$
\lim_{||\pi|| \to 0} \sum_{j=0}^{n-1}(t_{j+1}-t_j)(w(t_{j+1})-w(t_{t_j})) = 0 \\
\int_{0}^{T}dtdw(t) = 0 \\
$$

## $dtdt = 0$



# Levy's Theorem

Let $M(t), t \geq 0$ be a martingale, relative to $\mathcal{F}, t \geq 0$. Assume $M(0) = 0$, $M(t)$ has continuous paths and the quadratic variation of $M(t)$ equals $t$ for all $t > 0$. Then $M(t)$ is a Brownian Motion.

That is to say, any process can be Brownian Motion if the above 4 conditions are satisfied
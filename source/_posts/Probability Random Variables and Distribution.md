---
title: Random Variables and Distribution
date: 2019-2-14
tags: 
	- Probability
	- Statistics
categories: 
	- Mathematics
	- Probability
	- Probability Theory
mathjax: true
---
This note contains basic knowledge of random variables and distribution, including random variables, expected values, variance, covariance, and other characteristic values. Except the covariance, other conceptions are about one random variable.

# Random Variables and Distribution

## Random Variables

Numerical quantities whose values are determined by the outcome of the experiment are known as *random variables*. Hence, we can assign probabilities to their possible values. (The set of this probabilities is *distribution*.)

A random variable $X$ can be defined as:
$$
X: \Omega \to \mathbb{R} ~~~ \text{s.t.} ~~~ X^{-1}(B) = \{ \omega \in \Omega; X(\omega) \in B\} \in \mathcal{F} ~~ \text{for} ~~\forall B \in \mathscr{B}(\mathbb{R})
$$
where $B$ is a Borel set. $X^{-1}(B)$ is an inverse mapping. Therefore, __a random variable is a function from sample space $\Omega$ to real number set $R$.__  For example, let $X$ be the number of Head in 2 tosses. Then
$$
\{\omega_1:HH\} \to 2, ~\{\omega_2:HT\} \to 1, ~\{\omega_3:TH\} \to 1, ~\{\omega_4:TT\} \to 0
$$
If we let $X(\omega) \in (0.5, 1.5)$, then $X^{-1}(B) = \{\omega_2, \omega_3\}$. For another example, let $X \sim \exp(1)$, if we want to compute the probability $P(1 \leq X \leq 2)$, then $B = [1,2]$, $X^{-1}(B) = \{\omega \in \Omega : 1 \leq x(\omega) \leq 2\}$. The purpose of defining a Borel set is to make sure that the corresponding events are measurable (the probability exists). 

In fact, random variables can be *discrete* or *continuous*. The possible values of ***discrete random variables*** constituted sets of discrete values, whereas ***continuous random variables*** whose set of possible values is instead a continuous region can take on any value within some interval.

Actually, the distribution differs random variables from general variables in calculus. A random variable must have its own distribution.

## Distribution

For discrete variables, the distribution is a sequence form. If $X$ is a discrete random variable whose possible values are $x_1, x_2,...,x_n$, then the set of probabilities $P\{X=x_j\}$$(j=1,...,n)$ is called the *probability distribution of discrete random variable*. Since $X$ must assume one of these values, it follows that
$$
\begin{equation*}
\displaystyle{\sum_{j=1}^{n}}~P\{X = x_j\} = 1.
\end{equation*}
$$

For continuous variables, the distribution is a function form. Every continuous random variable $X$ has a function $f$ associated with it. This function $f$ is called the *probability density function* of $X$. For any numbers $a<b$, the area under $f$ between $a$ and $b$ is equal to the probability that $X$ assumes a value between $a$ and $b$.
$$
P\{a \leq X \leq b \} = area ~ under ~ f ~ between ~ a ~ and ~ b
$$

## Distribution Function

If $X$ is a random variable, for any real number x, we define
$$
F(x) = P(X \leq x)
$$
as the **distribution function** of random variable $X$, which is also called $X$ is denoted by $F(x)$, or $X \sim F(x)$. Sometimes, $F_{X}(x)$ is the same meaning. Sometimes it is also called **cumulative distribution function**(**CDF**).

Any random variable has its own distribution function, no matter it is discrete or continuous. And here are three fundamental properties.

+ monotonicity

  $F(x)$ is a monotonic and  nondecreasing function on the $(-\infty, \infty)$. that is to say, for any $x_1<x_2$,
  $$
  F(x_1) \leq F(x_2)
  $$

+ boundedness

  For any $x$, $0 \leq F(x) \leq 1$, and
  $$
  \begin{align*}
  F(-\infty)=\lim_{x \to -\infty}F(x)=0 \\
  F(\infty)=\lim_{x \to \infty}F(x)=1
  \end{align*}
  $$

+ right continuity

  $F(x)$ is the right-continuous function of $x$, that is to say, for any $x_0$,
  $$
  \lim_{x \to x_0}F(x)=F(x_0) \\
  F(x_0+0)=F(x_0)
  $$

These three fundamental properties are necessary and sufficient conditions whether a function is a distribution function.

## Mass & Density Function

For a discrete random variable $X$, the probability can be values like $x_1, x_2,...,x_n,...$, then the probability of $X$ equals $x_i$:
$$
p_i = p_i(x_i)=P(X=x_i),~~i=1,2,...,n,...
$$
is called the sequence of probability distribution, or the **probability mass function** of $X$. The abbreviation is **PMF**. 

And the cumulative distribution function of $X$ is:
$$
F(x)=\sum_{x_i \leq x}p(x_i)
$$
For a continuous random variable $X$, the cumulative distribution function of is $F(x)$, if $\exists$ a nonnegative integrable function $p(x)$, such that for any real number $x$,
$$
F(x)=\int_{-\infty}^{x}p(t)dt
$$
then $p(x)$ is called the **probability density function** of $X$, sometimes the a shorter name is **density** or **PDF**.

And here are two fundamental properties to determine whether a function is a probability density function or not.

+ non-negativity

$$
p(x) \geq 0
$$

+ regularity

$$
\int_{-\infty}^{\infty}p(x)dx=1
$$

# Expectation

If X is a random variable whose possible values are $x_1, x_2,...,x_n$, then the expected value of $X$, denoted by $E[X]$, is defined by
$$
\begin{equation*}
E[X] = \displaystyle{\sum_{j=1}^{n}}~{x_j}P\{X = x_j\}
\end{equation*}
$$

$E[X]$ also has alternative names: *expectation* or the *mean* of $X$. It is a kind of weighted average of possible values of $X$, where the weight given to a value is equal to the probability that $X$ assumes that value.

Actually we can define it more accurately. For an infinite sequence of discrete random variables $p(x_i)=P(X=x_i), i=1,2,...,n,...$, if 
$$
\sum_{i=1}^{\infty}|x_i|p(x_i)<\infty
$$
then
$$
E(x)=\sum_{i=1}^{\infty}x_ip(x_i)
$$
is called the **expected values**. If $\sum_{i=1}^{\infty}|x_i|p(x_i)$ is not convergent, then the expected values of $X$ is not existent.

For continuous random variables $X$, its density function is $p(x)$. If
$$
\int_{-\infty}^{\infty}|x|p(x)dx<\infty
$$
then
$$
E(X)=\int_{-\infty}^{\infty}xp(x)dx
$$
is called the **expected values**. If $\int_{-\infty}^{\infty}|x|p(x)dx$ is not convergent, then the expected values of $X$ is not existent.

If PMF or PDF of a random variable $X$ is $p(x_i)$ or $p(x)$, then the expected value of a function $g(X)$ of $X$ is:
$$
E[g(X)]= \left\{
\begin{align*}
&\sum_{i}g(x_i)p(x_i) ~~~ &\text{for discrete } \\
&\int_{-\infty}^{\infty}g(x)p(x)dx ~~~ &\text{for continuous}
\end{align*}\right.
$$


Here are some attributes of expectation. The first one is the linear attribute, which means that, for constants $a$ and $b$,
$$
E[aX+b]=aE[X]+b
$$
To verify it, let $Y = aX + b$. Since $Y = ax_j + b$ when $ X = x_j $, it follows that
$$
\begin{align*}
E[Y] &= \sum_{j=1}^{n} (ax_j + b) P\{X = x_j\} \\
	 &= \sum_{j=1}^{n}  ax_j P\{X = x_j\} ~ + ~ \sum_{j=1}^{n}b P\{X = x_j\} \\
	 &= a\sum_{j=1}^{n}  x_j P\{X = x_j\} ~ + ~ b\sum_{j=1}^{n} P\{X = x_j\} \\
	 &= aE[X] + b
\end{align*}
$$
And similarly, for random variables $X_1, ..., X_k$,
$$
E\left[\sum_{j=1}^{k} X_j \right] = \sum_{j=1}^{k}E[X_j]
$$

If $X$ and $Y$ are independent, then
$$
E[g(X)h(Y)]=E[g(X)]E[h(Y)]
$$



More rigorously, because random variable $X$ is a function of events $\omega_i$. We define $X(\omega_1) = X_1, X(\omega_2) = X_2, \cdots, X(\omega_n) = X_n$. Therefore, the expectation is 
$$
\mathbb{E}X = \sum_{\omega \in \Omega}X(\omega)\cdot\mathbb{P}(\omega)
$$
For finite $\Omega = \{w_1,\cdots,w_m\}$, 
$$
\mathbb{E}X = \sum_{k=1}^{m}X(\omega_k)\cdot\mathbb{P}(\omega_k)
$$
For countably infinite $\Omega = \{w_1,\cdots,\}$,
$$
\mathbb{E}X = \sum_{k=1}^{\infty}X(\omega_k)\cdot\mathbb{P}(\omega_k)
$$
For uncountably infinite $\Omega$,
$$
\mathbb{E}X = \int_{\Omega} X(\omega)d\mathbb{P}(\omega)
$$
which contains continuous random variables.

If $A \subset \Omega, B \subset \Omega, A, B \in \mathcal{F}, A\bigcap B = \empty $, then
$$
\begin{eqnarray}
\int_{A\bigcup B} X(\omega)d\mathbb{P}(\omega) &=& \int_{\Omega} \mathbb{I}_{\{A\bigcup B\}}X(\omega)d\mathbb{P}(\omega) \\
&=& \int_{\Omega} \mathbb{I}_AX(\omega)d\mathbb{P}(\omega) + \int_{\Omega} \mathbb{I}_BX(\omega)d\mathbb{P}(\omega) \\
&=& \int_{A} X(\omega)d\mathbb{P}(\omega) + \int_{B} X(\omega)d\mathbb{P}(\omega)
\end{eqnarray}
$$

## Conditional Expectation

Consider a probability space $(\Omega, \mathcal{F}, \mathbb{P})$, $\mathcal{G}$ is a sub-$\sigma$-algebra of $\mathcal{F}$. The conditional expectation of $X$ given $\mathcal{G}$ denotes 
$$
\mathbb{E}[X|\mathcal{G}]
$$
is any random variable that satisfies

+ $\mathbb{E}[X|\mathcal{G}]$ is $\mathcal{G}$-measurable
+ Partial Averaging: $\int_{A}\mathbb{E}[X|\mathcal{G}]d\mathbb{P}(\omega) = \int_{A}Xd\mathbb{P}(\omega)$ for all $A \in \mathcal{G}$

### Take out what is known

If $X$ is $\mathcal{G}$-measurable, then $\mathbb{E}[XY|\mathcal{G}] = X\mathbb{E}[Y|\mathcal{G}]$.

### Iteration (Tower Property)

$\mathcal{H}$ is a sub-$\sigma$-algebra of $\mathcal{G}$, 
$$
\mathbb{E}[\mathbb{E}[X|\mathcal{G}]|\mathcal{H}] = \mathbb{E}[X|\mathcal{H}]
$$

# Variance

The *variance* of $X$, denoted by $Var(X)$, which measure the spread of a random variable, is defined by
$$
\begin{align*}
Var(X) &= E[(X - E(X))^2] \\
	   &= E[X^2]-E[X]^2
\end{align*}
$$
If a and b are constants, then 
$$
\begin{align*}
Var(aX+b) &= E[(aX+b- E[aX+b])^2] \\
		  &= E[(aX - aE[X])^2] \\
		  &= E[a^2(X-E[X])^2] \\
		  &= a^2Var(X)
\end{align*}
$$
And if the ***random variables are independent***, the variance of the sum of random variables is equal to the sum of their variances ($X_1,...X_k$ are *independent random variables*)
$$
Var\left(\sum_{j=1}^{k} X_j \right) = \sum_{j=1}^{k} Var(X_j)
$$

The square root of the variance is called the *standard deviation*. A random variable tend s to lie within a few standard deviations of its expected value.

# Covariance

The covariance of any two random variables $X$ and $Y$, denoted by $Cov(X,Y)$, is defined by
$$
\begin{align*}
Cov(X,Y) &= E[(X-E[X])(Y-E[Y])] \\
		 &= E[XY-YE[X]-XE[Y]+E[X]E[Y]] \\
		 &= E[XY]-E[Y]E[X]-E[X]E[Y]+E[X]E[Y \\
		 &= E[XY]-E[X]E[Y]
\end{align*}
$$
A positive value of the covariance indicates that X and Y both tend to be large at the same time, whereas a negative value indicates that when one is large the other tends to be small. Independent random variables have covariance equal to 0. 

The following are some useful properties of covariance. For random variables $X$ and $Y$, and constant $c$:
$$
\begin{align*}
Cov(X,Y) &= Cov(Y,X) \\
Cov(X,X) &= Var(X) \\
Cov(cX,Y) &= c~Cov(X,Y) \\
Cov(c, Y) &= 0
\end{align*}
$$
Covariance also satisfies a linearity property, namely,
$$
\begin{align*}
Cov(X_1+X_2,Y) = Cov(X_1,Y)+Cov(X_2,Y)
\end{align*}
$$
which is easily generalized to yield the following identity:
$$
Cov\left( \sum_{i=1}^{n} X_i, \sum_{j=1}^{m}Y_j \right) = \sum_{i=1}^{n}\sum_{j=1}^{m}Cov(X_i,Y_j)
$$
This yields a useful formula for **the variance of the sum of random variables**:
$$
\begin{align*}
Var\left(\sum_{i=1}^{n} X_i \right) &= Cov\left( \sum_{i=1}^{n} X_i, \sum_{j=1}^{n}X_j \right) \\
&= \sum_{i=1}^{n}\sum_{j=1}^{n}Cov(X_i,X_j) \\
&= \sum_{i=1}^{n}Cov(X_i,X_i)+\sum_{i=1}^{n}\sum_{j \neq i}Cov(X_i,X_j) \\
&= \sum_{i=1}^{n}Var(X_i)+\sum_{i=1}^{n}\sum_{j \neq i}Cov(X_i,X_j)
\end{align*}
$$
The degree to which large values of $X$ tend to be associated with large values of $Y$ is measured by the *correlation* between $X$ and $Y$, denoted as $\rho(X,Y)$ and defined by
$$
\rho(X,Y) = \frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}
$$
It can be shown that
$$
-1 \le \rho(X, Y) \le 1
$$
If X and Y are linearly related by the equation $Y = a + bX$ , then $\rho(X,Y)$ will equal 1 when $b$ is positive and -1 when $b$ is negative.





# Coefficient of Variation

Provided the 2-order moment of $X$ exists, then
$$
C_{v}(X)=\frac{\sqrt{Var(X)}}{E(X)}=\frac{\sigma(X)}{E(X)}
$$
is called the **coefficient of variation** of $X$.

# Quantile

If the distribution function of a continuous random variable of $X$ is $F(x)$, the density function is $p(x)$, for $\forall ~ p \in (0,1)$, then call the $x_p$ which satisfies
$$
F(x_p)=\int_{-\infty}^{x_p}p(x)dx=p
$$
is the **$p$ quantile** of this distribution, also the **lower $p$ quantile**.  In fact, the left area of the density function which is divided into two part by the $x_p$ equals exactly $p$. Similarly, if $x'_p$ satisfies
$$
1-F(x'_p)=\int_{x'_p}^{\infty}p(x)dx=p
$$
it is called the **higher $p$ quantile**. They have such a relationship:
$$
x'_p=x_{1-p} \\
x_p=x'_{1-p}
$$




# K-Order Moment

Considering a random variable $X$, $k$ is a positive integer, if the expected values below both exist, then
$$
\mu_{k}=E(X^k)
$$
is called **$k$-order origin moment of $X$**.
$$
v_k=E(X-E(X))^k
$$
is called **$k$-order central moment of $X$**.

Obviously, the one-order origin moment is the expected value, and the two-order central moment is the variance. Because of $|X|^{k-1} \leq |X|^k+1$, if a k-order moment exists, a k-1-order moment also exists.

There is a simple equation between the origin moment and the central moment:
$$
v_k=E(X-E(X))^k=E(X-\mu_1)^k=\sum_{i=0}^k\left(_i ^k\right)\mu_i(-\mu_1)^{k-i}
$$

## Moment generating function

There is a moment generating functions for both discrete and continuous distribution:
$$
\begin{align*}
M(t)=E \left[ e^{tX}\right] = 
\end{align*}
$$
Sequentially taking derivatives of $M(t)$, we get one frequently used property of $M(t)$:
$$
\begin{align*}
M'(t) \\
M''(t) \\
M^{n}(t)
\end{align*}
$$

# Median

If the distribution function of a continuous random variable of $X$ is $F(x)$, the density function is $p(x)$, we call $x_p$ which satisfy the $p= 0.5$ as median, that is to say, $x_{0.5}$ satisfy:
$$
F(x_{0.5})=\int_{-\infty}^{x_{0.5}}p(x)dx=0.5
$$

# Skewness

If all the first 3-order moments of a random variable $X$ exist, then
$$

$$


# Kurtosis








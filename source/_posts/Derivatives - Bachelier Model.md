---
title: Bachelier Model
date: 2020-08-13
tags: 
	- Finance
	- Asset Pricing
categories: 
	- Economics
	- Finance
	- Derivatives
---

This is from a lecture of Prof. Peter Carr

## Bachelier Put Pricing Formula

### Assumptions

+ No frictions, no default, 
+ no arbitrage 
  + there exists a risk-neutral probability measure $\mathbb{Q}$ such that all security prices are martingales under it.
+ no carry costs (storage costs, convenience yields, dividends) 
  + therefore no early option exercise 

under the risk-neutral probability measure $\mathbb{Q}$, the spot price $s$ of the underlying security follows driftless arithmetic Brownian motion:
$$
s_t = s_0 + a(t)W_t, t\in[t_0,T]
$$
where $s_0$ is known real-valued initial spot price of the underlying security $a(t)>0$ is the known deterministic positive instantaneous normal volatility of the underlying security, and $W$ is a $ \mathbb{Q} $ standard Brownian motion. $T$ is the option's fixed maturity date. Let $\tau = T-t_0$ be the time to maturity of the option at the valuation time $t_0$. The standard deviation of $s_\tau$ is
$$
b(\tau) = \sqrt{\int_{0}^{\tau}a^2(t_0+u)du}, ~~ \tau > 0
$$
$b$ captures the investor's bewilderment at $t_0$ surrounding the future spot price $s_T$ at $T$. Here $b(\tau)$ is an increasing deterministic function of $\tau > 0$ with $\lim\limits_{\tau \to 0} = 0$.

### Probability Method

+ binary put

A binary put struck at $k \in \mathbb{R}$ pays $1(s_{\tau} < k)$ when it matures at $T$. The arbitrage-free binary put value in the Bachelier model is given in closed-form by
$$
bp^{b}(k,b(\tau),s) = \mathbb{E}^{\mathbb{Q}}1[s_{\tau}<k|s_t=s] = N\left(\frac{k-s}{b(\tau)}\right)
$$
where $N(z) = \int_{-\infty}^{z}\frac{e^{-\frac{y^2}{2}}}{\sqrt{2\pi}}dy$ is standard normal distribution function

+ vanilla put

A vanilla put struck at $k \in \mathbb{R}$ pays $(k - s_T)^+$ dollars when it matures at $T$. When the underlying real-valued, the payoff of a vanilla out is:
$$
(k - s_T)^+ = \int_{-\infty}^{k}1(s_T<L)dL
$$
Taking conditional expectations, the arbitrage-free value of the vanilla put in the Bachelier model is given by
$$
\begin{eqnarray}
vp^{b}(k,b(\tau),s) &=& \int_{-\infty}^{k}\mathbb{E}^{\mathbb{Q_b}}[1(s_T<L)|s_0 = s]dL \\
&=&  \int_{-\infty}^{k}bp^{b}(L,b(\tau),s)dL 
\end{eqnarray}
$$
where the $bp^{b}(L,b(\tau),s) = N\left(\frac{L-s}{b(\tau)}\right)$.

By Integrating by parts, the closed-form Bachelier model put pricing formula is
$$
vp^{b}(k,b(\tau),s) = (k-s)N\left(\frac{k-s}{b(\tau)}\right) + b(\tau)N'\left(\frac{k-s}{b(\tau)}\right)
$$
Let $x = k-s$ be the excess of strike k over spot s.
$$
vp^{b}(x,b(\tau)) = xN\left(\frac{x}{b(\tau)}\right) + b(\tau)N'\left(\frac{x}{b(\tau)}\right)
$$
The vanilla put value function $vp_b(x,b(\tau))$ is increasing in $x \in \mathbb{R}$ and the first derivative with regard to $x$ is the probability of the put finishing in the money.
$$
\frac{\partial}{\partial x}vp(x,b(\tau)) = N\left(\frac{x}{b(\tau)}\right)
$$


### Convex Duality Method

#### What's driving the uncertainty? 

+ The probability of finishing in the money itself.
  + It shows that how deep in the money we are. It is not determined by the difference between strike and spot, but by the probability we are going to finish in the money in maturity.

+ In currency liquid markets and there is a binary option. You can see this probability directly.

+ or just pick a dynamics for it not knowing where it is now

Define the probability
$$
\frac{\partial}{\partial x}vp(x,b(\tau)) = N\left(\frac{x}{b(\tau)}\right) = \pi
$$
as $\pi$

Since the standard normal CDF $N(x)$ is increasing, $\exists$ a function $N^{-1}(x)$ $s.t.$
$$
\frac{x}{b(\tau)} = N^{-1}(\pi)
$$
Now, let's consider $\pi$ as a new independent variables. Define a tangency portfolio value function $tp(x,\pi,b(\tau))$ by
$$
tp(x,\pi,b(\tau)) = x\pi + b(\tau)N'(N^{-1}(\pi)), \pi \in [0,1]
$$
The right hand side can be interpreted as the cost of holding $\pi$ short forward contracts with each short forward contract worth $x=k-s$ and also keeping $b(\tau)N'(N^{-1}(\pi))$ dollars in a cash reserve. The second term depends on $\pi$, which can be interpreted as the probability of the binary put finishing in the money.

#### What happens if we maximize it over $\pi$

$$
\sup_{\pi \in [0,1]}[x\pi+bN'(N^{-1}(\pi))]
$$

The first order condition is
$$
x+bN'(N^{-1}(\pi))[-N^{-1}(\pi)]\frac{1}{N'(N^{-1}(\pi))} = 0
$$
simplifying it implies that
$$
x = bN^{-1}(\pi)
$$
while inverting implies
$$
\pi^* = N\left(\frac{x}{b}\right)
$$
Therefore, the maximized cost is
$$
tp(x,\pi^*,b(\tau)) = x\pi + b(\tau)N'(N^{-1}(\pi)) = vp(x,b)
$$
This result means that the option value can be a supreme over supporting lines. The lines are the tangency portfolio. When replicating the option, one always holds the tangency portfolio, and in order to stay tangent, one has to change the slope and intercept of the portfolio. Maximizing the slope makes tangency line transform to a curve.



#### Martingale

$x = s - k$ is a martingale, because $k$ is just a constant. $\pi$ is also martingale because it is the price of a binary put. These two martingales have positive correlation: $x$ goes up and $\pi$ goes up; $x$ goes down and $\pi$ goes down. It can be interpreted that it costs money if one holds $\pi$ units of $x$.

The second term is a cash reserve that you need to charge when selling a put as well as the constant like buying $\pi$ units of $x$. And cash reserve is actually rated every unit of time to finance and push forward of the product of the martingales $x$ and $\pi$. As long as the right volatility is used in the Bachelier model, the cash reserve is depleted just as the put matures. The holding of $\pi_T = 1(x_T > 0)$ short forward contracts each worth $x_T$ delivers the vanilla put payoff, $1(x_T>0)x_T = x_T^+$



### Logistics Alternative using Convex Duality

Generalize the tangency portfolio value function in the Bachelier model to
$$
tp(x, \pi, b) = x\pi + C(\pi,b), \pi \in[0,1]
$$
where $C(\pi,b)$ are the cash holdings needed to push the pair of martingales $x$ and $\pi$ forward to maturity. Instead of setting $C = bN'(N^{-1}(\pi))$, we model the cash reserves by
$$
C(\pi,b) = b_{\tau}H(\pi)
$$
where $H(\pi)$ is the Shannon entropy of a Bernoulli random variable defined by
$$
H(\pi) = -\pi ln\pi - (1-\pi)\ln(1-\pi) \geq 0,~~\pi \in [0,1]
$$
Therefore,
$$
tp(x, \pi, b) = x\pi - b(\pi ln\pi + (1-\pi)\ln(1-\pi)] \geq 0,~~\pi \in [0,1]
$$
The truth is that the more uncertainty you are about the final price, the more you need to charge in cash reserves upfront. As before, consider maximizing the combined cost over $\pi \in [0,1]$
$$
\sup_{\pi \in [0,1]} x\pi - b(\pi ln\pi + (1-\pi)\ln(1-\pi)
$$
the first-order condition is
$$
x - b\ln\left(\frac{\pi}{1-\pi}\right) = 0
$$
the $\pi^*$ is
$$
\pi^* = \frac{e^{\frac{x}{b}}}{1+e^{\frac{x}{b}}}
$$
which is the logistic CDF. Substituting in the objective function at the top implies that the maximized cost is
$$
tp(x,\pi^*(x,b),b) = b \ln(1+e^{\frac{x}{b}})
$$
which is our candidate for a new put option pricing formula.

The logistic mo-nicker arises from differentiating w.r.t x:
$$
\frac{\partial}{\partial x}vp(x,b(\tau)) = (1+e^{-\frac{x}{b}})^{-1} = \pi^*(x,b)
$$
which is the logistic CDF.

The price change $s_T - s_0$ in the bachelier model is normally distributed with mean $0$ and standard deviation $b(\tau)$. In constrast, the price change $s_T - s_0$ in the logistic model is logistically distributed with mean 0 and scale parameter $b(\tau)$. Hence, the standard deviation of the price change $s_T - s_0$ in the logistic model is $\frac{b(\tau)\pi}{\sqrt{3}}$.

#### validate the model

+ validate it is arbitrage free

+ find the supporting Dynamics
  + there are two supporting dynamics for the logistic model
    + logistic
    + pure-jump
  + Bachelier model also has two supporting dynamics, which deliver the very same formula 



### Comparison of the Two Pricing Formulas

#### Logistic is sampler

It only contains elementary function of the two inputs $x$ and $b$. but in Bachelier model, the probabilty density function is not a elementary function.

#### Convexity

Both put prcing formulas are convex in $x$ and hence arise via maximizing over $\pi$

put premium is convex, which is not true in the black scholes model

#### Greeks

By the envelop theorem
$$
\frac{\partial}{\partial x}vp_b(x,b) \\
\frac{\partial}{\partial x}vp_l(x,b) \\
\frac{\partial}{\partial b}vp_b(x,b) \\
\frac{\partial}{\partial b}vp_l(x,b) \\
$$

#### Implied Volatility by Delta

Dividing each vanilla put value by $b = b(\tau) > 0$ causes each normalized put price, $\frac{vp(x,b)}{b}$ to depend on a single variable $\frac{x}{b}$

#### Put Premium

When the options are at the money $x = 0$, the second derivative in $b$ vanishes. At the money opton prices are actually positively proportional to $b > 0$:
$$
vp_b(0,b) \approx 0.3989b
$$

$$
vp_l(0,b) = b\ln2 \approx0.69b
$$



The normalizing divisions by $b > 0$ can be interpreted as a change of numeraire. At the money strike derivatives are both $\frac{1}{2}$. The ratios of away from the money option prices to at the money option prices just depends on the deviation of $\pi$ from $\frac{1}{2}$.


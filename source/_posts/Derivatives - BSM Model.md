---
title: Black Scholes Model
date: 2019-11-23
update: 2019-11-25
tags: 
	- Finance
	- Asset Pricing
categories: 
	- Economics
	- Finance
	- Derivatives
---

# Black-Scholes-Merton Formula

European Call
$$
C_t = S_t N(d_1) - Ke^{-r(T-t)}N(d_2)
$$
where
$$
\begin{eqnarray}
d_1 &=& \frac{ln\frac{S_0}{K}+(r+\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}} \\
d_2 &=& d_1 - \sigma\sqrt{T-t}
\end{eqnarray}
$$
European put
$$
P_t = C_t - S_t + Ke^{-r(T-t)}
$$

## Assumptions

The stock price follows the Geometric Brownian Motion
$$
dS_t = \mu S_tdt + \sigma S_tdW_t
$$
There are two directions to continue:

+ eliminate the random term $dW_t$, which is partial differential equation (hedging) method
+ eliminate the drift term $dt$, which is the equivalent martingale (risk-neutral) method

# Partial Differential Equation

## Construct the PDE

### Method 1: Risk-Free Gain

This method is from the class of Prof. Zheng, Zhenlong

Assumptions:

+ The short-term interest rate is known and is constant through time. (The interest term structure is flat.) (not restrict)

+ The stock price follows a random walk in continuous time with a variance rate proportional to the square of the stock price. Thus the distribution of stock prices is log-normal. The variance rate of the return on the stock is constant.(Geometric Brownian Motion.) ($\mu$ is a constant, and $\sigma$ is a constant.) (not restrict)
  $$
  dS = \mu S d t + \sigma S d W_t
  $$

+ Pays no dividends (not restrict)

+ No transaction costs. (restrict)

+ European

+ possible to borrow money to buy stocks / no penalties to short selling.

Deduction:

$S$ is the stock price, $W_t$ is Standard Brownian Motion, $\mu$ is drift, $\sigma $ is volatility, $f$ is the price of a derivative of Stock.
$$
\Delta S = \mu S \Delta t + \sigma S \Delta W_t
$$
According to Ito lemma,
$$
\begin{eqnarray*}
df &=& \frac{\partial f}{\partial t}dt + \frac{\partial f}{\partial S}dS + \frac{1}{2}\frac{\partial^2 f}{\partial S^2}dS \times dS \\
&=& \frac{\partial f}{\partial t}dt + \frac{\partial f}{\partial S}(\mu S d t + \sigma S d W_t) + \frac{1}{2}\frac{\partial^2 f}{\partial S^2}\sigma^2 S^2 dt \\
&=& (\frac{\partial f}{\partial t} + \frac{\partial f}{\partial S}\mu S + \frac{1}{2}\frac{\partial^2 f}{\partial S^2}\sigma^2 S^2) dt + \frac{\partial f}{\partial S}\sigma S d W_t
\end{eqnarray*}
$$
therefore, in discrete form
$$
\Delta f = (\frac{\partial f}{\partial t} + \frac{\partial f}{\partial S}\mu S + \frac{1}{2}\frac{\partial^2 f}{\partial S^2}\sigma^2 S^2) \Delta t + \frac{\partial f}{\partial S}\sigma S \Delta W_t
$$
Now that the stock and the derivative both have uncertainty term $\Delta W_t$, we want to  build a portfolio of stock and derivative to eliminate the uncertainty in a short time:

+ $\text{short} ~ 1 ~ \text{derivative} ~ (f)$

+ $\text{long} ~ \frac{\partial f}{\partial S} ~ \text{shares} ~ (S)$

 In a short time, it is a risk-free portfolio, the value of which is
$$
\Pi = -f + \frac{\partial f}{\partial S} S
$$
On the one hand, it has to have the risk-free return:
$$
\begin{eqnarray*}
\Pi_t &=& \Pi_0 e ^{rt} \\
\mathbb{ln}\Pi_t &=& \mathbb{ln}\Pi_0 + rt \\
\frac{d\Pi}{\Pi} &=& rdt
\end{eqnarray*}
$$
Therefore,
$$
\Delta \Pi = r \Pi \Delta t
$$
On the other hand, the change of its value is:
$$
\Delta \Pi = - \Delta f + \frac{\partial f}{\partial S} \Delta S
$$
Then we can get an equation, 
$$
r \Pi \Delta t =- \Delta f + \frac{\partial f}{\partial S} \Delta S
$$
with substituting for $\Delta f$, $\Delta S$ and $\Pi$
$$
\begin{eqnarray*}
r\Delta t (-f + \frac{\partial f}{\partial S} S) = &-&(\frac{\partial f}{\partial t} + \frac{\partial f}{\partial S}\mu S + \frac{1}{2}\frac{\partial^2 f}{\partial S^2}\sigma^2 S^2) \Delta t + \frac{\partial f}{\partial S}\sigma S \Delta W_t \\
&+&  \frac{\partial f}{\partial S}(\mu S \Delta t + \sigma S \Delta W_t)
\end{eqnarray*}
$$
After simplifying the equation, we get the famous differential equation
$$
\frac{\partial f}{\partial t} + rS\frac{\partial f}{\partial S}+\frac{1}{2}\sigma^2S^2\frac{\partial^2 f}{\partial S^2} = rf
$$
We need to find a $f$ which satisfies the above equation.

### Method 2: Discount Processes

This method is from the Shreve's book _Stochastic Calculus for Finance_

Assume stock price is $S(t)$, at time $t$ the position is $\Delta(t)$ shares, which is $\mathscr{F_t}$-measurable. We need to build a self-financing portfolio replicate the European call option.

+ long $\Delta(t)$ shares
+ short 1 call option

The portfolio value is $X(t)$. The change of portfolio value is
$$
dX(t) = \Delta(t)dS(t) + r(X(t)-\Delta(t)S(t))dt \tag{1}
$$
where $\Delta(t)dS(t)$ is the value change of the stock, $r(X(t)-\Delta(t)S(t))dt$ is the value change of cash

Because stock price is a Geometric Brownian Motion
$$
dS(t) = \alpha S(t)dt+\sigma S(t)dW(t) \tag{2}
$$
we get
$$
\begin{eqnarray}
dX(t) &=& \Delta(t)[\alpha S(t)dt+\sigma S(t)dW(t)] + r(X(t)-\Delta(t)S(t))dt \\
&=& (\alpha-r)\Delta(t)S(t)dt+ rX(t)dt + \Delta(t)\sigma S(t)dW(t) \tag{3}
\end{eqnarray}
$$
In equation (3), the first term $(\alpha-r)\Delta(t)S(t)dt$ is __excess returns__, the second term $rX(t)dt$ is __risk-free returns__, and the third term $\Delta(t)\sigma S(t)dW(t)$ is risk.

When we consider the discount of these two processes:
$$
\begin{eqnarray}
d(e^{-rt}S(t)) &=& d(e^{-rt})S(t) + e^{-rt}dS(t)+d(e^{-rt})dS(t) \\
&=& -rS(t)e^{-rt}dt + e^{-rt}[\alpha S(t)dt+\sigma S(t)dW(t)] + 0 \\
&=& (\alpha - r)S(t)e^{-rt}dt + \sigma S(t)e^{-rt}dW(t) \tag{4}
\\
\\
d(e^{-rt}X(t)) &=& d(e^{-rt})X(t) + e^{-rt}dX(t)+d(e^{-rt})dX(t) \\
&=& -rX(t)e^{-rt}dt + e^{-rt}[(\alpha-r)\Delta(t)S(t)dt+ rX(t)dt + \Delta(t)\sigma S(t)dW(t)] + 0 \\
&=& (\alpha - r)\Delta(t)e^{-rt}S(t)dt + \Delta(t) \sigma e^{-rt}S(t)dW(t) \\
&=& \Delta(t)[(\alpha - r)e^{-rt}S(t)dt + \sigma e^{-rt}S(t)dW(t)] \\
&=& \Delta(t)d(e^{-rt}S(t)) \tag{5}
\end{eqnarray}
$$
Here, the increasing value in cash is discount back to the initial state in equation (5).

Let $C(t,S(t))$ be the value of European call option, and $K,r, \sigma$ is invariant. 
$$
\begin{eqnarray}
dC(t,S(t)) &=& C_tdt+C_xdS_t+\frac{1}{2}C_{xx}dS_tdS_t \\
&=& C_tdt+C_x(\alpha S_tdt+\sigma S_tdW_t)+\frac{1}{2}C_{xx}\sigma^2S_t^2d_t \\
&=& (C_t + \alpha C_xS_t+\frac{1}{2}C_{xx}\sigma^2S_t^2)d_t + C_x\sigma S_tdW_t \tag{6} \\
\\
\\
d(e^{-rt}C(t,S_t)) &=& e^{-rt}(C_t + \alpha C_xS_t+\frac{1}{2}C_{xx}\sigma^2S_t^2 -rC)d_t + e^{-rt}C_x\sigma S_tdW_t \tag{7}

\end{eqnarray}
$$
Because the portfolio is the replication of this European call option, we have
$$
\begin{eqnarray}
dC(t,S(t)) &=& dX(t) \\
d(e^{-rt}C(t,S_t)) &=& d(e^{-rt}X_t)
\end{eqnarray}
$$
Therefore, by comparing equation (5) and (7), the first and second term should be equivalent respectively. The random terms shows that
$$
\Delta(t)\sigma e^{-rt}S_tdW_t =e^{-rt}C_x\sigma S_tdW_t \\
\Delta(t) = C_x
$$
and the drift term shows that 
$$
\Delta(t)(\alpha - r)e^{-rt}S_tdt = e^{-rt}(C_t + \alpha C_xS_t+\frac{1}{2}C_{xx}\sigma^2S_t^2-rC) dt \\
C_x(\alpha - r)e^{-rt}S_tdt = e^{-rt}(C_t + \alpha C_xS_t+\frac{1}{2}C_{xx}\sigma^2S_t^2 -rC)dt \\
C_xrS_tdt = (C_t + \frac{1}{2}C_{xx}\sigma^2S_t^2 -rC)dt \\
rC = C_t+rC_x+\frac{1}{2}C_{xx}\sigma^2S_t^2 \tag{9}
$$
Rewrite equation (9) as
$$
rC = \frac{\partial{C}}{\partial{t}}+r\frac{\partial{C}}{\partial{X}}+\frac{1}{2}C_{xx}\sigma^2X^2 \\
$$


## Solve the PDE



# Equivalent Martingale Method

## Construct the Martingale

__Step 1: define three accounts (processes)__

Define $B_t$ is the value of risk-free asset (cash) account,
$$
dB_t = rB_tdt \\
Bt = B_0e^{rt}
$$
$S_t$ is the value of stock
$$
dS_t = \mu S_tdt + \sigma S_tdW_t \\
S_t = S_0e^{(\mu-\frac{1}{2}\sigma^2)t + \sigma W_t}
$$
$V_t$ is the value of self-financing portfolio, $\phi_t^{S}$ is the position of Stock, $\phi_t^{B}$ is the position of risk-free asset. 
$$
dV_t = \phi_t^sdS_t+\phi_t^BdB_t\\
V_t = V_0 + \int_0^{t}\phi_u^sdS_u+\int_{0}^{t}\phi_u^BdB_u = \phi_t^sS_t+\phi_t^BB_t\\
$$
__Step 2: find the discounted processes__

Consider the first discounted process $V_t^* = V_t e^{-rt}$, here $V_t$ is risk-free portfolio, which should receive risk-free return:
$$
\begin{eqnarray}
dV_t^* &=& d(V_t e^{-rt}) \\
&=& d(e^{-rt})V_t + e^{-rt}dV_t \\
&=& (\phi_t^sS_t+\phi_t^BB_t)(-re^{-rt}dt) + e^{-rt}(\phi_t^sdS_t+\phi_t^BdB_t) \\
&=& \phi_t^s(-rS_te^{-rt}dt + e^{-rt}dS_t) + \phi_t^B(-rB_te^{-rt}dt + e^{-rt}dB_t) \\
&=& \phi_{t}^{s}d(S_te^{-rt}) 
\end{eqnarray}
$$
Now consider the second discounted process $S_t^* = S_t e^{-rt}$ which shows above:
$$
\begin{eqnarray}
dS_t^* &=& d(S_t e^{-rt}) \\
&=& d(e^{-rt})S_t + e^{-rt}dS_t+d(e^{-rt})dS_t \\
&=& -rS_te^{-rt}dt + e^{-rt}[\mu S_tdt+\sigma S_tdW_t] + 0 \\
&=& (\mu - r)S_te^{-rt}dt + \sigma S_te^{-rt}dW_t
\end{eqnarray}
$$
In general $\mu -r > 0$, we can not get martingale in the current measure. Therefore, we want to find a new probability measure $\mathbb{Q}$ such that $S_t^*$ is a $\mathbb{Q}$-martingale.

__Step 3: change the measure to construct the martingale__

According to the __Girsanov's Theorem__, we can find a process $\theta_s$ which satisfies the Novikov condition and define a new probability measure $\mathbb{Q}$, in which the process $X$ defined as
$$
W_t^{\mathbb{Q}} = W_t + \int_{0}^{t}\theta_sds, t\in[0,T]
$$
is a standard Brownian Motion.

Here, each $\theta$ will generate a new probability measure and we want to find a best (the most helpful) measure for pricing, which means that in the new measure $\mathbb{Q}$ the discounted process $S_t^*$ is a martingale.

Now, we need to find the $\theta$. Under $\mathbb{P}$
$$
\begin{eqnarray}
dS_t^* &=& (\mu - r)S_t^*dt + \sigma S_t^*dW_t \\
&=& (\mu - r)S_t^*dt + \sigma S_t^*(dW_t^{\mathbb{Q}} -\theta_tdt) \\
&=& (\mu - r - \sigma \theta_t)S_t^*dt + \sigma S_t^*dW_t^{\mathbb{Q}} \\
\end{eqnarray}
$$
Now it is under $\mathbb{Q}$. We want it to be a martingale, and let
$$
\mu - r - \sigma \theta_t = 0
$$
we get
$$
\theta_t = \frac{\mu - r}{\sigma}
$$
which is also called __Sharpe ratio__. Therefore, $dS_t^* = \sigma S_t^*dW_t^{\mathbb{Q}} $ is a $\mathbb{Q}$-martingale.

Therefore, the first discounted process should be
$$
\begin{eqnarray}
dV_t^* &=& \phi_{t}^{s}d(S_te^{-rt}) \\
&=& \phi_{t}^{s}dS_t^* \\
&=& \phi_{t}^{s}\sigma S_t^*dW_t^{\mathbb{Q}}
\end{eqnarray}
$$
Therefore, $V_t^* = \phi_{t}^{s}\sigma S_t^*dW_t^{\mathbb{Q}}$ is also a $\mathbb{Q}$-martingale. 

__Step 4: derivative pricing formula under risk-neutral measure__

Now let $C(t,S_t)$ be value of derivative. Our self-financial portfolio replicates the pay-off of the derivative. Therefore, 
$$
C(t,S_t) = V(t,S_t)
$$
According to the __martingale property__:
$$
\mathbb{E}^{\mathbb{Q}}[V_T^*|\mathcal{F}_t] = V_t^{*} \tag{a}
$$
In addition, if $G(S_T)$ is the payoff of the option, the discounted value of the portfolio at maturity $T$ equals to the discounted value of the option payoff at maturity $T$
$$
\mathbb{E}^{\mathbb{Q}}[V_T^*|\mathcal{F}_t] = \mathbb{E}^{\mathbb{Q}}[G(S_T)e^{-rT}|\mathcal{F}_t] \tag{b}
$$
Therefore, according to the equation $(a)$ and $(b)$, we have
$$
V_t^{*} =\mathbb{E}^{\mathbb{Q}}[G(S_T)e^{-rT}|\mathcal{F}_t]
$$
And 
$$
V_t = e^{-r(T-t)}\mathbb{E}^{\mathbb{Q}}[G(S_T)|\mathcal{F_t}]
$$
__Step 5: derivative the Black-Scholes Formula__

If the derivative is European Call, then
$$
\begin{eqnarray}
C(t,S_t) &=& e^{-r(T-t)}\mathbb{E}^{\mathbb{Q}}[(S_T-K)^+|\mathcal{F_t}] \\
&=& e^{-r(T-t)}\mathbb{E}^{\mathbb{Q}}[(S_T-K)\mathbb{I}_{S_T \geq K}|\mathcal{F_t}] \\
&=& e^{-r(T-t)}\mathbb{E}^{\mathbb{Q}}[S_T \cdot \mathbb{I}_{S_T \geq K}|\mathcal{F_t}] - e^{-r(T-t)}\mathbb{E}^{\mathbb{Q}}[K\cdot\mathbb{I}_{S_T \geq K}|\mathcal{F_t}] \\
\end{eqnarray}
$$

> A lemma
>
> if $\epsilon \sim N(0,1)$, $m, \lambda, a$ are constant, then
> $$
> \begin{eqnarray}
> \mathbb{E}[e^{m+\lambda\epsilon}\mathbb{I}_{\epsilon \geq a}] &=& \int_{-\infty}^{\infty}e^{m+\lambda x}\mathbb{I}_{x \geq a} \cdot \frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx \\
> &=& \int_{a}^{\infty}e^{m+\lambda x}\cdot \frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}dx \\
> &=& \int_{a}^{\infty} \frac{1}{\sqrt{2\pi}} e^{-\frac{(x-\lambda)^2}{2}}e^{m+\frac{\lambda^2}{2}}dx \\
> &=& \int_{a-\lambda}^{\infty} \frac{1}{\sqrt{2\pi}} e^{-\frac{y^2}{2}}e^{m+\frac{\lambda^2}{2}}dy \\
> &=& e^{m+\frac{\lambda^2}{2}}[\Phi(\infty) - \Phi(a-\lambda)] \\
> &=& e^{m+\frac{\lambda^2}{2}}[1 - \Phi(a-\lambda)] \\
> &=& e^{m+\frac{\lambda^2}{2}}\Phi(\lambda-a) \\
> \end{eqnarray}
> $$

Because 
$$
S_T =S_te^{(r-\frac{1}{2}\sigma^2)(T-t)+\sigma\epsilon\sqrt{T-t}}
$$
The first term
$$
\begin{eqnarray}
e^{-r(T-t)}\mathbb{E}^{\mathbb{Q}}[S_T \cdot \mathbb{I}_{S_T \geq K}|\mathcal{F_t}] &=& e^{-r(T-t)}\mathbb{E}^{\mathbb{Q}}\left[S_te^{(r-\frac{1}{2}\sigma^2)(T-t)+\sigma\epsilon\sqrt{T-t}} \cdot \mathbb{I}_{S_te^{(r-\frac{1}{2}\sigma^2)(T-t)+\sigma\epsilon\sqrt{T-t}} \geq K}|\mathcal{F_t}\right] \\
&=& e^{-r(T-t)}S_te^{(r-\frac{1}{2}\sigma^2)(T-t)}\mathbb{E}^{\mathbb{Q}}\left[e^{\sigma\epsilon\sqrt{T-t}} \cdot \mathbb{I}_{S_te^{(r-\frac{1}{2}\sigma^2)(T-t)+\sigma\epsilon\sqrt{T-t}} \geq K}|\mathcal{F_t}\right] \\
&=&S_te^{-\frac{1}{2}\sigma^2(T-t)}\mathbb{E}^{\mathbb{Q}}\left[e^{\sigma\epsilon\sqrt{T-t}} \cdot \mathbb{I}_{\epsilon \geq \frac{\ln(\frac{K}{S_t})-(r-\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}}|\mathcal{F_t}\right] \\
&=& S_te^{-\frac{1}{2}\sigma^2(T-t)} e^{\frac{1}{2}(\sigma\sqrt{T-t})^2}\Phi\left(\sigma\sqrt{T-t} - \frac{\ln(\frac{K}{S_t})-(r-\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right) \\
&=& S_t\Phi\left(\frac{\ln(\frac{S_t}{K})+(r+\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right) \\
\end{eqnarray}
$$
Then second term
$$
\begin{eqnarray}
e^{-r(T-t)}\mathbb{E}^{\mathbb{Q}}[K\cdot\mathbb{I}_{S_T \geq K}|\mathcal{F_t}] &=&  e^{-r(T-t)}K\cdot\mathbb{E}^{\mathbb{Q}}[\mathbb{I}_{S_T \geq K}|\mathcal{F_t}] \\
&=&  e^{-r(T-t)}K\cdot[1\cdot\mathbb{Q}(S_T \geq K)+0\cdot\mathbb{Q}(S_T < K)] \\
&=&  e^{-r(T-t)}K\cdot\mathbb{Q}(S_T \geq K) \\
&=&  e^{-r(T-t)}K\cdot\mathbb{Q}\left(\epsilon \geq \frac{\ln(\frac{K}{S_t})-(r-\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right) \\
&=& e^{-r(T-t)}K\cdot\Phi\left(-\frac{\ln(\frac{K}{S_t})-(r-\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right) \\
&=& e^{-r(T-t)}K\cdot\Phi\left(\frac{\ln(\frac{S_t}{K})+(r-\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right)
\end{eqnarray}
$$
Therefore, the price formula is
$$
C(t,S_t) = S_t\Phi\left(\frac{\ln(\frac{S_t}{K})+(r+\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right) -e^{-r(T-t)}K\cdot\Phi\left(\frac{\ln(\frac{S_t}{K})+(r-\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right)
$$
According to the Put-Call Parity $P+S_t = C + Ke^{-r(T-t)}$, we have 
$$
\begin{eqnarray}
P(t,S_t) &=& S_t\Phi\left(\frac{\ln(\frac{S_t}{K})+(r+\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right) -e^{-r(T-t)}K\cdot\Phi\left(\frac{\ln(\frac{S_t}{K})+(r-\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right) - S_t + Ke^{-r(T-t)} \\
&=& Ke^{-r(T-t)} \Phi\left(-\frac{\ln(\frac{S_t}{K})+(r-\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right) - S_t\Phi\left(-\frac{\ln(\frac{S_t}{K})+(r+\frac{1}{2}\sigma^2)(T-t)}{\sigma\sqrt{T-t}}\right)\\
\end{eqnarray}
$$

---
title: American Options
date: 2021-06-08
tags: 
	- Finance
	- Asset Pricing
categories:
	- Economics
	- Finance
	- Derivatives Pricing
---



# Perpetual American Put

## Definition

Perpetual means that there is no maturity. The payoff at $t$ will be: 
$$
(K-S_t)^{+} = \max\{0, K-S_t\}
$$
The price at time $0$ and time $t$ will be the same (time-homogeneity).

### Stopping time

1. If a random variable $\tau$ satisfies $\{\tau \leq t\} \in \mathcal{F}(t)$ for any $t \geq 0$, then $\tau$ is a stopping time.
   + example: $\tau_L = \inf\{u \geq 0: S_u \leq L\}$ is a stopping time

2. Definition of a Stopped Process, $X_t$ is

$$
X_{t \and \tau} = 
\begin{cases}
X_t, ~~~ 0 \leq t \leq \tau \\
X_{\tau}, ~~~ t \geq \tau
\end{cases}
$$

3. stopping-time martingale theorem: 
   + A martingale (super-martingale or sub-martingale) stopped at a stopping time, is still a martingale (super-martingale or sub-martingale).  
   + $M_t$ is martingale, $\tau$ is stopping time of $M_t$, then $M_{t \and \tau}$ is also a martingale.
   + $\mathbb{E} [M_{t \and \tau}|\mathcal{F}_s] = M_{s \and \tau}, s \leq t$

### Dominated Convergence

$X_1, X_2, ..., X_n, ...$ is a sequence of random variable and $X_n \to X$ almost surely. If $\exist ~ Y$, $\mathbb{E} Y < \infty$ and $|X_n| \leq Y$ almost surely for each $n$, then 
$$
\mathbb{E}X = \mathbb{E}\lim_{n \to \infty}X_n = \lim_{n \to \infty}\mathbb{E}X_n 
$$

## Pricing

Recall the value of an European put is
$$
V(t, S_t) = \mathbb{E}^{Q}\left[e^{-r(T-t)}(K-S_T)^{+}|\mathcal{F}_t \right]
$$
Define $f(t, S_t)$ as the value of perpetual American Put at time $t$, assume the put will be exercised at $t = \tau$, $T(t)$ is a set of all the stopping time (greater or equal to $t$), then
$$
f(t, S_t) = \sup_{\tau \in T(t)} \mathbb{E}^{Q} \left[e^{-r(\tau-t)}(K-S_{\tau})^{+}|\mathcal{F}_t \right]
$$
Because $\mathcal{F}_t$ means the information of the underlying price before $t$ and the underlying price is a geometric Brownian motion which has Markov property, we have:
$$
f(t, S_t) = \sup_{\tau \in T(t)} \mathbb{E}^{Q} \left[e^{-r(\tau-t)}(K-S_{\tau})^{+}|S_t \right].
$$

### Step 1

Define a price level $L < K$, at any time $t$, the put will be exercised if and only if $S_t \leq L$. If $L < S_t < K$ or $S_t \geq K$, don't exercise and wait until the first hitting time $\tau_L = \inf\{u \geq t: S_u \leq L\}, S_{\tau_L} \leq L$ and then exercise the option if $\tau_L \leq \infty$. If $\tau_L = \infty$, the option value should be zero because it will never be exercised. 

+ if $L \leq S_t < K$ or $K \leq S_t$, the option will not be exercised and we have to wait. Here $0 \leq t \leq \tau_L$.

  payoff is $K - S_t$, then put value is a function of $L, t, S_t$:
  $$
  \begin{eqnarray*}
  f_L(t, S_t) &=& \sup_{\tau_L \in T(t)} \mathbb{E}^{Q} \left[e^{-r(\tau_L-t)}(K-S_{\tau_L})^{+}|S_t \right] \\
  &=& \mathbb{E}^{Q} \left[e^{-r(\tau_L-t)}(K-S_{\tau_L})^{+}\mathbb{I}_{\tau_L < \infty}|S_t \right] \\
  &=& \mathbb{E}^{Q} \left[e^{-r(\tau_L-t)}(K-L)^{+}\mathbb{I}_{\tau_L < \infty}|S_t \right] \\
  &=& (K-L)\mathbb{E}^{Q} \left[e^{-r(\tau_L-t)}\mathbb{I}_{\tau_L < \infty}|S_t \right] \\
  &=& (K-L)\mathbb{E}^{Q} \left[e^{-r(\tau_L-t)}|S_t \right] \\
  &=& (K-L)\mathbb{E}^{Q} \left[e^{-r(\tau_L)}|S_0 \right] \\
  &=& (K-L)\mathbb{E}^{Q} \left[e^{-r(\tau_L)}\right] \\
  &=& (K-L)\mathbb{E}^{Q} \left[e^{-r\tau_L} \mathbb{I}_{\tau_L< \infty}\right] \\
  &=& (K-L)\mathbb{E}^{Q} \left[S^{-\lambda}_{\tau_L} S^{\lambda}_{\tau_L} e^{-r\tau_L} \mathbb{I}_{\tau_L< \infty}\right] \\
  &=& (K-L)L^{-\lambda} \mathbb{E}^{Q} \left[S^{\lambda}_{\tau_L} e^{-r\tau_L} \mathbb{I}_{\tau_L< \infty}\right] \\
  \end{eqnarray*}
  $$
  Considering the time homogeneity, the put option value will be the same at any time $t$, therefore we can change the $t$ to $0$. Because there is no additional information at time 0, we can leave the filtration alone. The $\lambda$ is a parameter we want to choose based on the property of a stochastic exponential process. 

+ if $S_t \leq L < K$, the option will be exercised and the value is $K-S_t$. 

### Step 2:

Because the underlying price is a geometric Brownian motion:
$$
S_t = S_0 e^{(r-\frac{1}{2}\sigma^2)t + \sigma W^Q_t}
$$
$\forall \lambda \in \mathbb{R}$, we have:
$$
S_t^{\lambda} = S_0^{\lambda} e^{(r-\frac{1}{2}\sigma^2)\lambda t + \sigma \lambda W^Q_t}.
$$
We can define a stochastic exponential:
$$
Z_t^{(\lambda)} = S_0^{\lambda} e^{-\frac{1}{2}\sigma^2\lambda^2t + \sigma \lambda W^Q_t}.
$$
Then the differential of $Z_t^{(\lambda)}$ is
$$
\begin{eqnarray*}
dZ_t^{(\lambda)} &=& S_0^{\lambda} d(e^{X_t}) \\
&=& S_0^{\lambda} e^{X_t}\left[dX_t + \frac{1}{2}dX_tdX_t\right] \\
&=& S_0^{\lambda} e^{X_t}\left[\lambda\sigma dW_t^Q-\frac{1}{2}\sigma^2\lambda^2dt + \frac{1}{2}\left(\lambda\sigma dW_t^Q-\frac{1}{2}\sigma^2\lambda^2dt\right)\left(\lambda\sigma dW_t^Q-\frac{1}{2}\sigma^2\lambda^2dt\right)\right] \\
&=& S_0^{\lambda} e^{X_t}\left[\lambda\sigma dW_t^Q-\frac{1}{2}\sigma^2\lambda^2dt+\frac{1}{2}\sigma^2\lambda^2dt \right] \\
&=& S_0^{\lambda} e^{X_t} \lambda\sigma dW_t^Q
\end{eqnarray*}
$$
Therefore $Z_t^{(\lambda)}$ is a Q-martingale.
$$
\begin{eqnarray}
Z_t^{(\lambda)} &=& S_0^{\lambda} e^{-\frac{1}{2}\sigma^2\lambda^2t + \sigma \lambda W^Q_t} \\
&=& S_0^{\lambda} e^{(r-\frac{1}{2}\sigma^2)\lambda t + \sigma \lambda W^Q_t -(r-\frac{1}{2}\sigma^2)\lambda t -\frac{1}{2}\sigma^2\lambda^2t} \\
&=& S_t^{\lambda} e^{[-r\lambda+\frac{1}{2}\sigma^2\lambda (1-\lambda)]t} \\
\end{eqnarray}
$$
In order to match with $S^{\lambda}_{\tau_L} e^{-r\tau_L}$, we can let 
$$
[-r\lambda+\frac{1}{2}\sigma^2\lambda (1-\lambda)]t = -rt \\
(1-\lambda)\left(\frac{1}{2}\sigma^2\lambda + r\right) = 0,
$$
therefore $\lambda_+ = 1$, $\lambda_{-} = -\frac{2r}{\sigma^2}$. We can choose $\lambda = \lambda_{-} = -\frac{2r}{\sigma^2}$, and then
$$
Z_t^{(\lambda)} = Z_t^{(\lambda_{-})} = S_t^{\lambda_{-}}e^{-rt}
$$
Because $L \leq S_t$, $\lambda_{-} = -\frac{2r}{\sigma^2} < 0$ and $0 \leq t \leq \tau_L$: 
$$
0 \leq Z_t^{(\lambda_{-})} = S^{\lambda_{-}}_{t} e^{-rt} \leq L^{\lambda_{-}}e^{-rt} \leq L^{\lambda_{-}}
$$
if $\tau_L = \infty$, then $Z_t^{(\lambda_{-})}$, $0 \leq t \leq \tau_L$:
$$
0 \leq \lim_{t \to \infty} Z_t^{(\lambda_{-})} \leq \lim_{t\to\infty}L^{\lambda_{-}}e^{-rt} = 0
$$
if $\tau_L < \infty$, then we should consider the stopped process $Z_{t\and \tau_L}^{(\lambda_{-})}$ rather than $Z_t^{(\lambda_{-})}$ because the support of stopped process $Z_{t\and \tau_L}^{(\lambda_{-})}$will include $\infty$:
$$
\lim_{t \to \infty} Z_{t\and \tau_L}^{(\lambda_{-})} = Z_{\tau_L}^{\lambda_{-}}
$$

### Step 3:

Consider the put value function $f_L(t,S_t)$ again. Because we have let $\lambda = \lambda_{-}$, then:
$$
\begin{eqnarray*}
f_L(t, S_t) &=&(K-L)L^{-\lambda} \mathbb{E}^{Q} \left[S^{\lambda}_{\tau_L} e^{-r\tau_L} \mathbb{I}_{\tau_L< \infty}\right] \\
&=& (K-L)L^{-\lambda_{-}} \mathbb{E}^{Q} \left[Z_{\tau_L}^{\lambda_{-}} \mathbb{I}_{\tau_L< \infty}\right] \\
&=& (K-L)L^{-\lambda_{-}} \mathbb{E}^{Q} \left[\mathbb{I}_{\tau_L< \infty}\lim_{t \to \infty} Z_{t\and \tau_L}^{(\lambda_{-})} \right] \\
&=& (K-L)L^{-\lambda_{-}} \left\{ \mathbb{E}^{Q} \left[\mathbb{I}_{\tau_L< \infty}\lim_{t \to \infty} Z_{t\and \tau_L}^{(\lambda_{-})} \right] + 0 \right\} \\
&=& (K-L)L^{-\lambda_{-}} \left\{ \mathbb{E}^{Q} \left[\mathbb{I}_{\tau_L< \infty}\lim_{t \to \infty} Z_{t\and \tau_L}^{(\lambda_{-})} \right] + \mathbb{E}^{Q} \left[\mathbb{I}_{\tau_L= \infty}\lim_{t \to \infty} Z_{t}^{(\lambda_{-})} \right] \right\} \\
&=& (K-L)L^{-\lambda_{-}} \left\{ \mathbb{E}^{Q} \left[\mathbb{I}_{\tau_L< \infty}\lim_{t \to \infty} Z_{t\and \tau_L}^{(\lambda_{-})} \right] + \mathbb{E}^{Q} \left[\mathbb{I}_{\tau_L= \infty}\lim_{t \to \infty} Z_{t\and \tau_L}^{(\lambda_{-})} \right] \right\} \\
&=& (K-L)L^{-\lambda_{-}} \mathbb{E}^{Q} \left[\lim_{t \to \infty} Z_{t\and \tau_L}^{(\lambda_{-})} \right]
\end{eqnarray*}
$$
Because $Z_t^{(\lambda_{-})}$ is a Q-martingale, $Z_{t\and \tau_L}^{(\lambda_{-})}$ is also a Q-martingale. According to the Dominated Convergence Theorem (DCT), 
$$
\left|Z_{t\and \tau_L}^{(\lambda_{-})}\right| = Z_{t\and \tau_L}^{(\lambda_{-})} \leq L^{\lambda_{-}} \\
\lim_{t \to \infty} Z_{t\and \tau_L}^{(\lambda_{-})} = Z_{\tau_L}^{\lambda_{-}}
$$
we can change the order between the expectation and limit. Therefore, we have 
$$
\begin{eqnarray*}
f_L(t, S_t) &=& (K-L)L^{-\lambda_{-}} \mathbb{E}^{Q} \left[\lim_{t \to \infty} Z_{t\and \tau_L}^{(\lambda_{-})} \right] \\
&=& (K-L)L^{-\lambda_{-}} \lim_{t \to \infty} \mathbb{E}^{Q} \left[ Z_{t\and \tau_L}^{(\lambda_{-})} \right] \\
&=& (K-L)L^{-\lambda_{-}} \lim_{t \to \infty} Z_{0\and \tau_L}^{(\lambda_{-})} \\
&=& (K-L)L^{-\lambda_{-}} Z_{0\and \tau_L}^{(\lambda_{-})} \\
&=& (K-L)L^{-\lambda_{-}} Z_{0}^{(\lambda_{-})} \\
&=& (K-L)L^{-\lambda_{-}} S_{0}^{\lambda_{-}} \\
&=& (K-L) \frac{S_{0}^{\lambda_{-}}}{L^{\lambda_{-}}} \\
\end{eqnarray*}
$$
In total:
$$
f_L(S) = 
\begin{cases}
K-S, ~~~S \leq L \\
(K - L)\left(\frac{S}{L}\right)^{-\frac{2r}{\sigma^2}}, ~~~ S > L
\end{cases}
$$

### Step 4:

The formula above contains $L$, which is not the final answer. If every investors are rational, then we can continue to find maximum of $f_L(S)$ in term of $L$:
$$
\begin{eqnarray}
\frac{d f}{d L} &=& -\left(\frac{S}{L}\right)^{-\frac{2r}{\sigma^2}}+(K - L)\left({-\frac{2r}{\sigma^2}}\right)\left(\frac{S}{L}\right)^{-\frac{2r}{\sigma^2}-1}S\left(-\frac{1}{L^2}\right) \\
&=& \left(\frac{S}{L}\right)^{-\frac{2r}{\sigma^2}}\left[-1-(K - L)\left({-\frac{2r}{\sigma^2}}\right)\left(\frac{1}{L}\right)\right] = 0
\end{eqnarray}
$$
Therefore,
$$
L^* = \frac{2rK}{2r+\sigma^2}
$$
we have the final fomula:
$$
f_L(S) = 
\begin{cases}
K-S, ~~~S \leq \frac{2rK}{2r+\sigma^2} \\
\frac{\sigma^2K}{2r+\sigma^2}\left(\frac{S(2r+\sigma^2)}{2rK}\right)^{-\frac{2r}{\sigma^2}}, ~~~ S > \frac{2rK}{2r+\sigma^2}
\end{cases}
$$

---
title: Asset Pricing - Derivatives
date: 2020-1-30
tags: 
	- Asset Pricing
	- Papers
categories: 
	- Economics
	- Literature Review
	- Asset Pricing
---
# Option
## Option Profit and Loss Attribution and Pricing: A New Framework
21 February 2020 from JF
https://onlinelibrary.wiley.com/doi/pdfdirect/10.1111/jofi.12894
This paper develops a new top‐down valuation framework that links the pricing of an option investment to its __daily profit and loss attribution__. The framework uses the Black‐Merton‐Scholes option pricing formula to attribute the short‐term option investment risk to __variation in the underlying security price__ and the __option's implied volatility__. 
Taking risk‐neutral expectation and demanding no dynamic arbitrage results in a pricing relation that links __an option's fair implied volatility level__ to the __underlying's volatility level__ with corrections for the implied volatility's own expected direction of movement, its variance, and its covariance with the underlying security return.

## Static and semistatic hedging as contrarian or conformist bets
12 March 2020 From MF
http://arxiv.org/pdf/1902.02854
In this paper, we argue that, once the costs of maintaining the hedging portfolio are properly taken into account, __semistatic portfolios should more properly be thought of as separate classes of derivatives, with nontrivial, model‐dependent payoff structures__. 
+ We derive new integral representations for payoffs of exotic European options in terms of payoffs of vanillas, different from the Carr–Madan representation, and suggest approximations of the idealized static hedging/replicating portfolio using vanillas available in the market. 
+ We study the dependence of the hedging error on a model used for pricing and show that the variance of the hedging errors of static hedging portfolios can be sizably larger than the errors of variance‐minimizing portfolios. 
+ We explain why the exact semistatic hedging of barrier options is impossible for processes with jumps, and derive general formulas for variance‐minimizing semistatic portfolios. 
+ __We show that hedging using vanillas only leads to larger errors than hedging using vanillas and first touch digitals__. In all cases, efficient calculations of the weights of the hedging portfolios are in the __dual space__ using new efficient numerical methods for calculation of the Wiener–Hopf factors and Laplace–Fourier inversion.

## Real-Option Valuation in Multiple Dimensions Using Poisson Optional Stopping Times
28 January 2020 from JFQA
http://pdfs.semanticscholar.org/94a1/56cdc6359a0c90061bb678fa9ef32ed5be6c.pdf
We provide __a new framework for valuing multidimensional real options__ where opportunities to exercise the option are generated by an exogenous Poisson process, which can be viewed as a liquidity constraint on decision times. This approach, which we call the Poisson optional stopping times (POST) method, finds the value function as a monotone sequence of lower bounds. 
+ In a case study, we demonstrate that the frequently used quasi-analytic method yields a suboptimal policy and an inaccurate value function. 
+ The proposed method is demonstrably correct, straightforward to implement, reliable in computation, and broadly applicable in analyzing multidimensional option-valuation problems.

# Credit

## Ruin probabilities for a Lévy-driven generalised Ornstein–Uhlenbeck process
04 December 2019 from FS
http://link.springer.com/article/10.1007/s00780-019-00413-3?utm_source=researcher_app&utm_medium=referral&utm_campaign=RESR_MRKT_Researcher_inbound

We study the asymptotics of the ruin probability for a process which is the solution of a linear SDE defined by a pair of independent Lévy processes. Our main interest is __a model describing the evolution of the capital reserve of an insurance company__ selling annuities and investing in a risky asset. 

+ Let $\beta > 0$  be the root of the cumulant-generating function ${H}$ of the increment $V_1$ of the log-price process. We show that the ruin probability admits the exact asymptotic  $Cu^{-\beta}$ as the initial capital $u \to \infty$, assuming only that the law of $V_{T}$ is non-arithmetic without any further assumptions on the price process.

## Is the Credit Spread Puzzle a Myth?
20 February 2020 from JFE
https://www.sciencedirect.com/science/article/pii/S0304405X20300428?dgcid=rss_sd_all&utm_source=researcher_app&utm_medium=referral&utm_campaign=RESR_MRKT_Researcher_inbound
We revisit Feldhütter and Schaefer (FS, 2018), who report evidence of a "credit spread puzzle" for high-yield but not investment-grade bonds. We show their results are reversed when their model is calibrated to market values of debt (as required by theory) rather than book values. 
We then demonstrate that using credit spreads rather than historical default rates to identify the default boundary provides the statistical power necessary to reject their assumption that firm dynamics follow geometric Brownian motion. A large market price of jump risk is required to match historical default rates, which generates a credit spread puzzle for investment-grade but not high-yield bonds.

## Robust XVA
12 March 2020 from MF
https://onlinelibrary.wiley.com/doi/abs/10.1111/mafi.12260?af=R&utm_source=researcher_app&utm_medium=referral&utm_campaign=RESR_MRKT_Researcher_inbound
We introduce an __arbitrage‐free framework for robust valuation adjustments__. An investor trades a credit default swap portfolio with a risky counterparty, and hedges credit risk by taking a position in defaultable bonds. The investor does not know the exact return rate of her counterparty's bond, but she knows it lies within an uncertainty interval. 
+ We derive both __upper and lower bounds for the XVA process__ of the portfolio, and show that these bounds may be recovered as solutions of nonlinear ordinary differential equations. The presence of collateralization and closeout payoffs leads to important differences with respect to classical credit risk valuation. 
+ The value of the super‐replicating portfolio cannot be directly obtained by plugging one of the extremes of the uncertainty interval in the valuation equation, but rather depends on the relation between the XVA replicating portfolio and the closeout value throughout the life of the transaction. 
+ Our comparative statics analysis indicates that credit contagion has a nonlinear effect on the replication strategies and on the XVA.
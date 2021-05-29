---
title: Credit Products
date: 2020-03-04
tags: 
	- Risk Management
	- NYU
	- FRM
categories: 
	- Economics
	- Finance
	- Risk Management
mathjax: true
---

This notes is based on the class Financial Risk Management of NYU MFE, including basic conceptions of Credit Product and risks.

# Credit Market

Credit market risk reflects the yield spread over the benchmark or risk free rate for a specific issuer, which is a gauge of the probability of default and/or changes in the expected loss given default.
In order to properly evaluate, classify and understand credit market risk drivers, it is important to have insight into the types of credit instruments available, distinguish between securitized and non securitized forms of credit risk and understand direct and indirect credit exposures

## Loan

### Floating rate notes


$$
\begin{eqnarray*}
PV &=& \frac{\frac{(\text{Index}+\text{QM})\times \text{FV}}{m}}{1+\frac{\text{Index} + \text{DM}}{m}} + \frac{\frac{(\text{Index}+\text{QM})\times \text{FV}}{m}}{(1+\frac{\text{Index} + \text{DM}}{m})^2} +... +\frac{\frac{(\text{Index}+\text{QM})\times \text{FV}}{m}+\text{FV}}{(1+\frac{\text{Index} + \text{DM}}{m})^N}
\end{eqnarray*}
$$



### Mortgage

$$
x = F_0 \times\frac{r(1+r)^n}{(1+r)^n-1}
$$


$$
F_t = F_{t-1}+\frac{R}{12}\times F_{t-1}-x
$$
Principle:
$$
F_t - F_{t-1}
$$



## Securitization

### Benefit of Securitization

Cost Efficiency for Issuers Firms

Asset Related Risk Transfer

Investor Diversification, Risk Sharing and Liquidity



### Risk of Securitization

Transaction Complexity

Credit / Default Risk

Prepayment Reinvestment Early Amortization

Moral Hazard Conflicts of Interest



## Credit Default Swap





## CXA

### CVA

__Credit valuation adjustment (CVA) is the present value of credit risk for a loan, bond or derivative obligation__. The CVA calculation for a financial exposure is a function of __expected exposure (EE)__, __recovery rate (RR)__, __loss given default (LGD)__, the __probability of default (POD)__ to arrive at an __expected loss (EL)__, and a discount factor to arrive at the present value of expected loss. Steps in the process are as follows:

![cva.png](https://i.loli.net/2020/03/05/1SO9Qxo54Ywkp27.png)

### Example:

Consider exposure to a borrower who must deliver a zero-coupon government bond with a yield of 5% maturing in four years, assuming a recovery rate of 40% and probability of default per period of 1.25%. Following the steps on our prior slide:

Expected Exposure:

Recovery:

Loss given Default:

Probability of Default:

Expected Loss

PV of Expected Loss:

| EE   | Recovery | LGD  | POD  | POS  | EL   | DF   | PV   |
| ---- | -------- | ---- | ---- | ---- | ---- | ---- | ---- |
|      |          |      |      |      |      |      |      |
|      |          |      |      |      |      |      |      |
|      |          |      |      |      |      |      |      |



## Credit Scoring

**Credit scores and ratings** are used by lenders in deciding whether to extend credit to a borrower and in determining contract terms Credit scores are used primarily by lenders for small and medium sized enterprises as well as retail customers Credit ratings are used by credit rating agencies in the wholesale market for bonds issued by private and public entities as well as for asset backed securities (ABS)



### advantage

shortcut to avoid risk 

### disadvantage

lag indicator



## Sovereign credit risk

Key differences in sovereign credit risk include the protection against bankruptcy, protections
against creditors as well as unique sources of repayment such as the ability to tax Bankruptcy.
versus sovereign debt restructuring renegotiation Bankruptcy is typically protected by national law and most defaults are resolved via debt restructuring and/or renegotiation.

**Debt/GDP Ratio** Similar to ratios for private borrowers, this statistic is widely seen as a barometer for a country’s ability to service its interest and repay debts given that GDP may be as a proxy for a country’s “balance sheet” measuring overall economic activity subject to taxation



# Credit Portfolio Management

Credit portfolio management involves aggregating information across obligors to classify, quantify, manage, report and mitigate (or securitize) risks

The key question is to estimate default probabilities, which can be estimated via:

+ Historical data
+ Credit Spreads
+ Structural Credit / Reduced form model
  + Structural Model
  + Reduced Form Model
  + Market Consolidation
    + MSCI: Risk-Metrics
    + Moody: KMV

## Z-score

### Altman's Z-Score Model



### Accounting Ratios

$X_1 = \frac{\text{Working Capital}}{\text{Total Assets}}$

$X_2 = \frac{\text{Working Capital}}{\text{Total Assets}}$

$X_3 = \frac{\text{Working Capital}}{\text{Total Assets}}$

$X_4 = \frac{\text{Working Capital}}{\text{Total Assets}}$

$X_5 = \frac{\text{Working Capital}}{\text{Total Assets}}$

$Z = 1.2X_1 + 1.4X_2 +3.3X_3 +0.4X_4 +0.99X_5$

### Conclusion

$Z>3.0$

$2.7<Z<3.0$

$1.8<Z<2.7$

$Z<1.8$



## Default Probabilities

### Historical Default Probabilities

unconditional



### Hazard Rate

$$
Q(t)=1-e^{-\lambda(t)t}
$$



### Ratings Migration

Example:

The rating agencies report transition matrices based on historical experience The example below shows the probabilities of a rating migrating over the course of the next twelve months For example, an A rated issuer has a 91.8% probability of remaining at that level, a 0 1 probability of moving up to AAA, a 1.4% probability of moving up to AA, a 3.6% probability of moving down to BBB, 2.4% down to BB and 0.7% to B

|      |      |      |      |      |      |      |      |      |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|      |      |      |      |      |      |      |      |      |
|      |      |      |      |      |      |      |      |      |
|      |      |      |      |      |      |      |      |      |
|      |      |      |      |      |      |      |      |      |
|      |      |      |      |      |      |      |      |      |
|      |      |      |      |      |      |      |      |      |
|      |      |      |      |      |      |      |      |      |
|      |      |      |      |      |      |      |      |      |


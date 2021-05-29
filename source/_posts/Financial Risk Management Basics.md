---
title: Risk Management Basics
date: 2020-02-02
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

This notes is based on the class Financial Risk Management of NYU MFE, including basic conceptions of Risk Management.

# Basic Questions

## What is risk

risk is a **material adverse** financial or non financial outcome for any public or private enterprise, authority or individual

address the risk by

+ identify primary risks
+ classify other risks which are incidental to the business
+ maximize return for a given level of risk

## Whose risk

__Banks and other financial institutions__ act as __intermediaries__ between consumers, businesses and public not for profit entities

Sources of risk and return directly indirectly derived from financial markets

+ Bank
  + taking deposits and extending loans

+ Non-bank financial institutions:
  + Asset managers
  + Asset owners
  + Insurance companies
  + Hedge funds

+ Non-financial institutions(corporations)
  + Sources of risk and return are conversion of inputs (labor and raw materials) into intermediate or final goods services
    + operating cycle (short)
    + capital investment cycle (long)

## What is Financial Risk Management

+ Formal treatment based upon Modern Portfolio Theory
  + Mean - variance optimization based upon __asset-liability management__
+ Financial Instrument Characteristics
  + exchange or over the counter
  + frequently or never, what is cash or liquidation value
  + bow are prices distributed under various market scenarios
  + how assets and liabilities interact in a portfolio
+ difference in risk management among:
  + banks
  + non-bank financial institutions
  + non-financial companies

## Why and how to manage financial risk

### Why

+ Society and the domestic and global economies depend upon a stable financial system
+ Prudent financial risk management in non financial firms can enhance firm value, avoid bankrupt.

### How

Quantitative Risk Management

+ Introduce a more rigorous mathematical basis in current practice
+ Establish techniques and tools to go beyond current practice and address deficiencies

# Financial Return

## Returns on Financial Assets

### Definition

two forms of return:

+ Periodic cash flows
+ capital gain or loss

further adjustment based on fees, taxes, inflation, functional currency or leverage

### Single Period:

$$
\begin{eqnarray*}
R &=& \frac{P_t-P_{t-1}+D_t}{P_{t-1}} = \frac{P_t}{P_{t-1}}-1+\frac{D_t}{P_{t-1}} \\
 &=& \text{capital gain} ~ + ~ \text{dividend or coupon yield} 
\end{eqnarray*}
$$

### Multiple Period:

+ Arithmetic (mean) return for asset $i$

$$
\begin{eqnarray*}
\bar{R_i} = \frac{R_{i1}+R_{i2}+...+R_{i,{T-1}}+R_{iT}}{T} = \frac{1}{T}\sum_{t=1}^{T}R_{it}
\end{eqnarray*}
$$

+ Geometric mean return:

$$
\begin{eqnarray*}
\overline{R_{Gi}} &=& \sqrt[T]{(1+R_{i1})*(1+R_{i2})*...*(1+R_{i,T-1})*(1+R_{iT})}-1 \\
&=& \sqrt[T]{\prod_{t=1}^{T}(1+R_{it})}-1
\end{eqnarray*}
$$

+ Generalized / Power Mean:

for not all equivalent positive number $x_i$, 
$$
M_p(x_1, x_2, ..., x_n) = \left(\frac{1}{n}\sum\limits_{i=1}^{n}x_{i}^{p}\right)^{\frac{1}{p}}
$$
is a monotone increasing function. Then
$$
M_{-\infty}(x) \leq...\leq M_{-1}(x) \leq M_{0}(x) \leq M_{1}(x) \leq M_{2}(x) \leq ...\leq M_{+\infty}(x)
$$
Here,
$$
\begin{eqnarray*}
M_{-\infty}(x) &=& \lim_{p \to -\infty}M_{p}(x) = \min(x_1, ..., x_n) \\
M_{-1}(x) &=& \frac{n}{\frac{1}{x_1}+...+\frac{1}{x_n}}               \\ 
M_{0}(x) &=& \lim_{p \to 0}M_{p}(x) = \sqrt[n]{x_1...x_n}             \\
M_{1}(x) &=& \frac{x_1+...+x_n}{n} \\
M_{2}(x) &=& \sqrt{\frac{x_1^2+...+x_n^2}{n}} \\
M_{+\infty}(x) &=& \lim_{p \to \infty}M_{p}(x) = \max(x_1, ..., x_n)
\end{eqnarray*}
$$

### Multiple Periods with intermediate cash flows

Money-weighted returns (internal rate of return)
$$
\sum_{t=0}^{T}\frac{CF_t}{(1+IRR)^t}=0
$$
Usually, when $t=0$, $CF$ is negative, without discounting.

### Varying Periods of Return:

convert daily, weekly, monthly or quarterly returns to annual:
$$
r_{annual} = (1+r_{period})^c-1
$$

### Return on Multiple Assets:

Portfolio returns are a weighted average, for asset $i$ with a return of $R_i$ and a percentage weight of $w_i$: 
$$
R_p = \sum_{i=1}^{N}w_iR_i,~ \sum_{i=1}^{N}w_i = 1
$$

### Financial Asset Risk:

Variance $\sigma^2$ and standard deviation $\sigma $ measure:
$$
\sigma^2=\frac{\sum\limits_{t=1}^{T}(R_t-\mu)^2}{T}
$$
Sample variance $S^2$and standard deviation $S$ measure:
$$
S^2=\frac{\sum\limits_{t=1}^{T}(R_t-\overline{R})^2}{T-1}
$$

### Portfolio Risk and Return Measure:

$$
\sigma_{p}^2=\left(\sum_{i=1}^{N}w_i^2\sigma_{i}^2 + \sum_{i,j=1,i \not= j}^{N}w_iw_j\rho_{ij}\sigma_i\sigma_j \right), ~ \sum_{i=1}^{N}w_i = 1
$$

### Value at Risk (VaR)

Statistical measurement of expected loss with a given level of confidence over a given time period 

+ Basic VaR models rely on historical return and risk and assume normally distributed returns
+ Time period and confidence level for VaR are important.

$$
\begin{eqnarray*}
\text{VaR} &=& \text{Volatility} \times \text{Unit Value} \times \text{Position Size} \times \text{Time} \times \text{Confidence} \\
&=& (\%) \times (\$) \times (\text{w/o leverage}) \times (\sqrt{\text{time}}) \times (\text{standard deviations})
\end{eqnarray*}
$$

__Example: 1-month 99% VaR for 20000  S&P 500 equivalents:__
$$
1.50\% \times 1200 \times 20000 \times \sqrt{30} \times 2.326 = 4586410
$$
which means __1% chance of losing more than $4,586,410 in one month__

Key Assumptions and Limitations:

+ Assumed Homoskedasticity of Markets
+ Liquidity Risk
+ Danger of Generalized Use
+ Computational Issues

+ Source of Volatility
+ Derivative Based Exposures

# Risk Management Process

+ identification
+ measurement
+ monitoring
+ reporting

# Risk Categorization

## Market Risk

### Definition

Change in value of securities or derivatives whose value is derived from market prices. 

### Categories of market risk

+ __(Market) Liquidity Risk__
+ __Asset-Liability Management Risk__
+ Direct Risk
  + price / market value decrease
+ indirect
  + Implied Volatility
  + Implied Correlation
    + Correlation within Asset Classes
    + Correlation Across Asset Classes
    + Cash versus Derivative Risks
+ Mark to market versus accrual

## Credit Risk

### Definition

Financial performance under a contractual relationship, repayment of principal, interest or another obligation under a financial agreement (bond or derivative)

+ Performance risk encompasses credit and non credit elements (commercial dispute)
+ Borrower’s non performance affect similar claims to various creditors

+ Lenders and bondholders are compensated via a spread derived from the probability of default and the loss given default

### Categories of credit risk

+ Lending Risk (loan)
  + Unsecured Lending Risk (credit card with high interest, rely on borrower cash flow)
  + Secured Lending Risk (mortgage with purchasing house, collateral pledged to lender)

+ Default Risk (Bond)
  + Standardized instrument issued by public or private entities
  + Bond credit provisions in an indenture
+ Sovereign Risk
+ (Credit) Liquidity Risk (take money back at the same time)
+ Counterparty Risk (Derivative)
+ __Combination of credit and market risk securities__: collateral value falls and secured exposure becomes partially secured or unsecured

### Lender protect themselves in three ways:

+ Prevent increases in debt or diversion of assets elsewhere
+ Avoid favoring another class of creditors
+ Ensure that borrower maintains enough assets to repay interest and principal

## Operational Risk

How institutions put strategies into practice by employing professionals, developing best practices and establishing infrastructure to achieve strategic objectives

+ people
  + Key person risk
  + employee or trader risk
+ processes
  + Procedural breakdowns
  + Review controls and incentives
+ systems

## Other Risks

### Strategic Risk

### Regulatory Risk

### Legal, political or environmental Risk



# Key elements in risk management

+ Compliance
  + Regulatory reporting requirements

+ Controls
  + Ensuring a bank can maintain standards and prevent errors, fraud or data breaches
+ Portfolio Management
  + Properly balancing risk and reward in trading, lending or investments
+ Communication
  + Disclosure to rating agencies, counterparties and other stakeholders (investor day)
+ Planning
  + Understanding specific risk scenarios for contingency planning

Failure to: 

+ Accurately measure known risks

+ Adequately take risks into account
+ Communicate risks to top management
+ Adequately and consistently monitor of risks
+ Manage risks properly
+ Use appropriate risk metrics
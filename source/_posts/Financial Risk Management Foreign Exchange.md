---
title: Foreign Exchange
date: 2020-02-14
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

This notes is based on the class Financial Risk Management of NYU MFE, including basic conceptions.

# Foreign Exchange Overview

## Foreign Exchange Market

The global foreign exchange (FX) market represents the highest trading volume of any financial asset class (over $5 trillion daily) and has been historically dominated by large international banks trading in a decentralized, over-the-counter manner in what is referred to as the interbank market.

+ history: 

  Modern-day foreign exchange trading was established in the early 1970s following the breakdown of the post-World War II Bretton Woods monetary agreement and subsequent shift from fixed to floating exchange rates among major global economies

+ purpose:

  The ability to exchange currencies is critical in facilitating the cross-border flow of goods, services and financial assets for transactional and investment purposes.

+ scope:

  total daily FX trading volume exceeded $5 trillion in 2016, is dominated by
  USD, EUR and JPY spot and FX swap transactions originated in the UK and US.

+ trends:

  FX trading has declined slightly in recent years due to reduced capital and goods flows following the 2008 financial crisis, reduced activity from hedge funds and less appetite among banks to warehouse risk due to increased capital requirements. Emerging fintech-driven non-bank players have increased market share and the proportion of algorithmic trading is rising.

### Why does the foreign exchange market have such a size and scope

+ Increasing global interdependence amid growing cross-border financial and goods flows
+ Increased wealth and risk appetite drives globalization of investment portfolios
+ Continued emerging market growth attracts cross-border capital and goods flows

### Three primary foreign exchange risk exposure:

+ __transaction risk__: the original functional currency value of the transaction will __change or be recorded at a different value__
+ __translation risk__: Firms face the translation of foreign currency denominated balance sheet and income statement items (revenues and expenses) from a foreign currency into its functional currency.
+ __economic risk__: impact long-term investment decisions

### What drives foreign exchange rates?

Currency movements are commonly considered as random events more readily explained after the fact than predicted on an ex-ante basis. This would suggest investors are unable to generate alpha while hedgers should only manage FX-based balance sheet and income statement volatility as needed.

## Foreign Exchange Rate Framework

### Monetary Approach (Purchasing Power Parity)

Implies an exchange rate should reflect the relative price of the same basket of goods across currencies, or alternatively that the difference in the rate of change in domestic and foreign currency prices (the inflation differential) should equal the percentage depreciation or appreciation of the exchange rate. PPP is too narrow a measure to be used in isolation given the existence of non-standard baskets of goods, non-traded goods and other differences.

Example:

+ undervalued:

  A Big Mac costs 130 RUB in Russia and US$5.74 in the U.S. This implies a RUB/USD exchange rate of 22.65. The actual exchange rate of 63.84 RUB/USD suggests the RUB is 64.5% undervalued 

  ($\frac{63.84 – 22.65}{63.84}$).

+ overvalued:

  A Big Mac costs SFR 6.50 in Switzerland and US$5.74 in the U.S. The implied SFR/USD exchange rate is 1.13. The difference between this and the actual exchange rate of 0.99 SFR/USD suggests the Swiss franc is 14% overvalued 

  ($\frac{0.99 – 1.13}{0.99}$).

### Balance of Payments Approach

Addresses the implications of trade and capital flows for FX rates, focusing on current (goods, services, dividends and interest) versus capital account (investment, portfolio flows or loans) changes which net to zero. Although in theory any current account imbalances are financed via the capital account, in practice changes to certain components are more material than others, for example commodity-led economies (AUD or BRL) respond more to those flows, while emerging Asia is more impacted by business cycles. Flows matter, but do not explain FX volatility.

### Asset Markets Approach

Currencies are highly responsive to current and future fundamentals as embodied in asset prices reflecting the present value of future cash flows denominated in different currencies. Under this explanation, FX prices adjust instantaneously to new information about currency fundamentals. This approach is supported by strong empirical evidence and forms the basis for trading.

### Central bank FX market intervention 

This is an additional overlay, particularly in emerging markets driven by an aim to either address an imbalance, offset volatility or accumulate FX reserves.

# Foreign Exchange Convention

## Inverse and direct quoting

### Inverse quotes

Several major (and a few minor) currencies are quoted as __the number of U.S. dollars required to purchase one unit of currency__.

+ EUR / USD = 1.11
  + __Therefore a stronger EUR will result in a higher EUR/USD__, similar to a stock

+ GBP / USD
+ AUD / USD

+ NZD / USD

### Direct quotes

For all other currencies, __prices are quoted as the number of units of foreign currency which buys one US dollar__

+ USD / JPY = 107.8
  + This figure rises as JPY weakens and the USD strengthens

# Foreign Exchange Tools

## Spot and Forward

### Spot 

#### Spot FX mechanics

Spot transactions are cash transactions usually settled on __the second business
day (T+2) after the trade date__ (CAD, TRY, MXN and RUB settle next day) under an agreement between two parties (one of whom is often a bank) to purchase or sell units of a base currency.

+ Example:

  A EUR/USD quote of 1.1526 [1.15 representing the ‘big figure’, and the 26 expressed as ‘pips’) means a counterparty purchases one EUR in exchange for $1.1526 dollars. 

+ Spot trade exposure is referred to as __settlement risk__, which arises __when one party transfers funds in one currency in anticipation of receiving payment in another currency from another party__.

+ Spot comprises less than half of overall FX volume, as market participants usually manage forecasted transaction risks using FX derivatives.

### Forward

These involve the exchange of one currency for another at a pre-agreed rate on a pre-determined date ranging from T+3 to several weeks or years. This is the formula:
$$
F = S_0 \frac{(1+y_{US})^T}{(1+y_{FC})^T}
$$
In continuous time:
$$
F_t = S_0e^{(r-r_f)t}
$$

+ Example:

  Assume the spot EUR/USD FX rate is 1.10 (i.e., US$ 1.10 buys one euro). If the EUR one  year benchmark rate is -0.4% and an equivalent USD one-year benchmark is 2.00%, solve for the one year EUR / USD forward rate.
  $$
  1.10 \times\frac{1+0.02}{1-0.004}=1.1265
  $$
  Note that the higher the interest rate in USD in this case, the more expensive it is to purchase EUR in one year’s time given that the buyer foregoes one year of the higher USD interest.

#### Forward Contract mechanics

Foreign exchange forward transactions are quoted in ‘__points__’, or the (positive or negative) __difference in the forward and spot quote__ scaled to the last decimal in the corresponding spot quote.

+ Example: 

  the one-year forward rate of +265 points would apply to EUR/USD in our above example, the corresponding forward rate being 1.10 + (265/10,000) = 1.1265. Many firms __hedge transaction exposure for relatively certain forecasted transactions__ such as __accounts receivable__ or __payable__ as well as investment exposures using currency forward transactions.

## Non-deliverable FX forwards, swaps and options

+ Exchange Rate Restrictions 

  Although freely floating currencies are predominant among major industrial nations, only around 30 global currencies are freely floating, with others (mostly emerging markets (EM) currencies) subject to controls such as restrictions on trading or exchanging currencies.

### Non-Deliverable FX Forwards (NDFs)

These are similar to standard forward agreements in that they involve the exchange of one currency’s value for another at a pre-agreed rate on a pre-determined date. However, __given onshore currency restrictions__, they are settled in __a convertible currency (usually USD) offshore without a physical exchange of the hedged currency__.

+ Example:

  A corporation enters into a $1 million NDF to purchase BRL and sell USD for settlement in one month at a forward rate of 3.79 BRL/USD. 

  + In one month, the NDF breaks even if USD 1,000,000 = BRL 3,790,000. 
  + If BRL strengthens to 3.70 instead, the BRL buyer has a gain of BRL 90,000 on the fixing date. 
    + The NDF contract is settled offshore for USD 24,324 (= BRL 90,000 / 3.70).

+ __Forward versus NDF pricing__

  While interest rate parity helps explain forward pricing, it is generally less the case for NDFs, which may diverge due to __expected FX regime change__, __speculative positioning__, capital flows, local onshore rate markets and the relationship between offshore and onshore currency forward markets. 

  If international investors __cannot access onshore rate markets or deposits in local currency__, NDF prices for the currency are based primarily on __the expected future spot exchange rate__.

## FX Swaps

Combines offsetting and simultaneously executed FX spot and forward transactions. In an FX swap, the base currency is purchased (or sold) on a spot basis and sold (or purchased) on a forward basis. 

+ These are distinct from cross-currency interest rate swaps which involve intermediate cash flows to transform a fixed-income exposure from one currency to another (addressed later). 
+ A primary use for FX swaps is to replace or “roll” forward transactions as they approach maturity.

## FX Options

Like options in other asset classes, option transactions involve the purchase or sale of the right, but not the obligation to exchange one currency for another at a pre-determined “strike” price on a pre-determined date in the future. 

+ Many firms hedge the exposure they face for uncertain forecasted transactions in other currencies using options.

## Cross-currency swaps

### cross-currency swaps

__A series of FX forwards__ designed to __convert recurring or periodic cash flows from one currency to another__, or effectively the __exchange of a floating rate note in one currency with that of another__.

+ Example of a JPY investor buying a USD bond:

  | Time | Action                                                       |
  | ---- | ------------------------------------------------------------ |
  | T=0  | Investor must sell JPY, buy USD at spot to pay for USD bond  |
  | T=t  | Investor receives USD coupons and must convert at unknown future JPY/USD spot rate |
  | T=n  | Investor receives final USD coupon and principal and must convert back to JPY at unknown future JPY/USD spot rate |

### floating-floating cross-currency basis swap

involve both initial and final exchange of principal upon inception and maturity at the current spot rate, with a periodic exchange of floating benchmark rates.

### Use of cross-currency swaps

+ common among investors seeking bringing offshore investments back to their home currency and issuers hedging translation risk or foreign currency debt issuance.

+ Pricing and Interest Rate Parity
  + Classical interest rate parity requires that currencies may be invested at risk-free zero-coupon rates, a condition which is not satisfied by instruments based upon swap rates

+ Classical interest rate parity requires that currencies may be invested at risk-free zero-coupon rates, a condition which is not satisfied by instruments based upon swap rates
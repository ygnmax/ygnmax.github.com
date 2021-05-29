---
title: Commodity
date: 2020-02-21
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

# Commodity Overview

## Commodity Market

Commodities are basic, standardized goods which are traded and used in commerce, often distinguished between “__hard__” (natural resources such as metals and energy) and “__soft__” (crops and livestock) commodities. 

Commodity producers and consumers (both end users and those who use them in production processes) often manage commodity price risk assisted by banks.

__Market dynamics__ for individual commodities are unique and specifically linked to the countries, sectors and/or companies which engage in exploration, extraction, refining or production (referred to as producers) and those who use these goods as inputs in production or are end users (known as consumers) and therefore rely on __periodic physical delivery__.

Producers and consumers often seek to manage exposure to price volatility via standardized future and option contracts traded on commodity exchanges as well as through customized over-the-counter instruments. 

Investors on the other hand with no direct physical exposure have increased commodity investments due to low (and sometimes negative) correlation with other asset types. 

Specific commodities such as gold are sought for wealth preservation and inflation protection by investors seeking a safe haven in volatile markets.

## Participants

### Banks and Broker-Dealers

Several large global and U.S. money center banks are engaged in commodity markets, largely as exchange members and OTC derivative and derivatives clearing providers, although some leverage specific credit and industry expertise and client relationships to engage in physical market and structuring opportunities involving financing.

### Exchanges

Exchanges perform a variety of functions across physical and derivative markets to support producer and consumer activities:

+ __Physical markets__ 

  require a global network of warehouses to store and deliver on contracts. Exchanges neither own nor operate this network, but create an infrastructure to ensure efficient and secure delivery under physical contract terms. __Investments in commodities generally embed this ongoing cost of storage (“cost of carry”) for a warehoused commodity__. 

+ __Derivative markets__

  are generally designed to mirror physical trading. Similar to other futures and options exchanges, these offer standardized contracts with pre-specified delivery dates, location and underlying commodity specifications. Unlike trading in a financial asset, futures not offset by an opposite sale or purchase prior to settlement date are physically settled.

__Example: corn futures__

This Chicago Board of Trade contract specifies 5,000 bushels (~ 127 metric tons) of #2 yellow corn traded in USD with a minimum tick size of $12.50 with contracts expiring each March, May, July, September and December.

## Pricing

### Basis

Basis is the difference between the cash and futures price for the same commodity:
$$
\text{Basis} = S_0 - F_{0,t}
$$
where $S_0$ is the current spot price and $F_{0,t}$ is the current futures price for delivery at time t. The basis may be positive or negative at any given time, and as the time to delivery passes, __the futures price will approach the spot price__, resulting in a basis of zero (except for minor differences due to transportation and transaction costs).

+ Example:

  If the current spot price of gold is $\$1,488.53/t ~ oz$. and the December futures contract is trading at $\$1,499.50/t ~ oz$., the basis equals $-\$10.97$, which is $\$1,488.53 - \$1,499.50$.

### Spread

Spread is the price difference between __futures on the same commodity__ for __different maturity dates__:
$$
\text{Spread} = F_{0,t+k} - F_{0,t}
$$
where $F_{0,t}$ is the current futures price for delivery at t (say in 3 months), while $F_{0,t+k}$ is the current futures price for delivery at $t+k$ (say in 6 months). 

+ Example:

  If the wheat futures contract for delivery in 3 months is $\$3.25$ per bushel, while the 6-month contract is $\$3.30$ per bushel, the spread is $\$0.05$. 

### Cost of Carry Model

A simplified way to value a futures contract which assumes futures prices should depend upon the current spot price and the cost of “carrying” or storing (storage, insurance, transportation and financing) the commodity from now until the futures contract matures. 

In its simplest form, it assumes __no transaction costs or margin requirements__, __no restrictions on short selling__ and that investors can __freely borrow and lend at the same rate of interest__*:
$$
F_{0,t} = S_0(1+C_{0,t})
$$
Where $C_{0,t}$ is the percentage cost required to store (or “carry”) the commodity from now until time t

+ __Cash and Carry Arbitrage__
  $$
  F_{0,t} > S_0(1+C_{0,t})
  $$
  If the futures contract price exceeds spot plus carry, a trader can borrow, buy the commodity today for cash, sell futures and carry the goods to the futures expiration date. At time t, she delivers the commodity against the futures contract and repays the loan.

+ __Reverse Cash and Carry Arbitrage__
  $$
  F_{0,t} < S_0(1+C_{0,t})
  $$
  If the spot price plus carry exceeds the futures price, spot plus carry, the trader can sell short a physical asset. The trader purchases a futures contract, which will be used to honor the short sale commitment. Then the trader lends the proceeds at an established rate of interest. At time t, the trader accepts delivery against the futures contract and uses the commodity received to cover the short position. 

Examples:

+ WTI spot oil is $\$55$ per barrel, and a trader notes annualized carry is $5\%$ or $\$2.75$ for $6$ months. If 6-month WTI futures are $\$60$, how can the trader earn a riskless profit? 
  + Cash and carry arbitrage - futures are overpriced versus spot plus carry ($\$60 > \$57.75$)
  + sell $F_{6mo}$ for $\$60$, 
  + buy oil now at $\$55$ and 
  + pay $\$2.75$ carry 
  + earn $\$2.25$ ($\$60 - \$57.75$) 

+ If spot gold is $\$1,450$ /t oz. and the one-year futures contract is at $\$1,460$ with a $3.5\%$ carry cost, how can our trader generate an arbitrage return? 
  + Reverse cash and carry arbitrage - futures are underpriced versus spot plus carry ($\$1,460 < \$1,500.75$), 
  + sell gold short in the cash market, 
  + lend the proceeds 
  + buy the futures contract 
  + Take delivery under the futures contract to cover the short gold position and keep $\$40.75$ or $\$1,500.75 - \$1,460$. 

### Spot and Futures relationship

+ __Expectations__: 
  $$
  F_{0,t}=E{[S_{0,t}]}
  $$
  Futures prices are a function of expected spot commodity prices in the future

+ __Backwardation__:
  $$
  F_{0,t}<E{[S_{0,t}]}
  $$
  suggests __futures markets__ are primarily __driven by hedgers with short positions__ who pay speculators a premium to assume the price risk. __Speculators take long positions__ to assume price risk and are rewarded when futures prices rise to match the spot price at maturity.

+ Contango:
  $$
  F_{0,t}>E[S_{0,t}]
  $$
  Suggests that __futures markets__ are primarily __driven by hedgers who hold long positions__. For example, grain millers may purchase futures contracts to reduce their price risk. __Hedgers pay speculators a premium to assume the price risk__. Speculators take short positions to assume this price risk and are rewarded when the futures price declines to match the spot price at maturity.
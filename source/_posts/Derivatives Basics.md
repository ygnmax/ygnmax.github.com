---
title: Derivatives Basics
date: 2019-1-21
update: 2019-1-22
tags: 
	- Derivatives
	- Finance
categories:
	- Economics
	- Finance
	- Derivatives Pricing
---

This note contains basic conceptions of financial instruments and derivatives including stock, bonds, forward contracts, swaps, options.

# Classification of financial instruments
+ basic securities
	+ fixed income
		+ bonds
		+ bank account
		+ loans
	+ equities
		+ stocks
+ derivatives and contracts
	+ options (nonlinear function of a stock)
		+ calls & pulls
		+ exotic options
	+ swaps
	+ futures & forwards
	+ credit risk derivatives

## stocks
+ issued by firms to finance operations
+ represent ownership of the firm
+ price known today, but not in the future
+ may or may not pay diviends

## bonds
+ price known today
+ future payoffs known at fixed dates
+ otherwise the price movement is random
+ final payoff at maturity: face value/ nominal value/principal
+ intermediate payoffs: coupons
+ exposed to default/credit risk

## derivatives
+ Sell for a **price/value/premium** today.
+ Future value **derived** from the value of the
underlying securities (as a function of
those).
+ Traded at exchanges – standardized
contracts, no credit risk;
+ Over-the-counter (OTC) – a network of
dealers and institutions, can be nonstandard, some credit risk.

### Why derivatives?
+ To hedge risk (primary reason)
+ To speculate
+ To attain “arbitrage” profit
+ To exchange one type of payoff for another
+ To circumvent regulations (flexible)

## Forward Contract
+ An agreement to buy (**long**) or sell (**short**) a given **underlying** asset S:
	+ Underlying asset could be stock or merchandise
	+ At a predetermined future date T (**maturity**).
	+ At a predetermined price F (**forward price**).
+ F is chosen so that the contract has zero value today.
	+ a kind of zero sum game
	+ Today: gain & loss are 0 (different from options)
+ Delivery takes place at maturity T:
	+ Payoff at maturity: 
		+ Long: S(T) - F
		+ Short: F - S(T)
	+ Price F set when the contract is established.
	+ S(T) = spot (market) price at maturity
+ Long position: obligation to buy
+ Short position: obligation to sell
+ **Differences with options**:
	+ Delivery has to take place.
	+ Zero value today.
> **Example**
>
On May 13, a firm enters into a long
forward contract to buy one million euros in
six months at an exchange rate of 1.3. On November 13, the firm pays F=$1,300,000 and receives S(T)= one million euros. How does the payoff look like at time T as a
function of the dollar value of S(T) spot
exchange rate?
>
graphs


## Swaps
Agreement between two parties to exchange two series of payments.

+ Classic interest rate swap:
	+ One party pays fixed interest rate payments on a notional amount.
	+ Counterparty pays floating (random) interest rate payments on the same notional amount.
+ Floating rate is often linked to LIBOR (London Interbank Offer Rate), reset at every payment date.

The two parties may be exposed to different interest rates in different markets, or to different institutional restrictions, or to different regulations.

+ a swap example
	+ New pension regulations require higher investment in fixed income securities by pension funds, creating a problem: liabilities are long-term while new holdings of fixed income securities may be short-term.
	+ Instead of selling assets such as stocks, a pension fund can enter a swap, exchanging returns from stocks for fixed income returns.
	+ Or, if it wants to have an option not to exchange, it can buy **swaptions** instead. 

> Example: Swap Comparative Advantage
US firm B wants to borrow AUD, Australian firm A wants to borrow USD: 
+ Firm B can borrow at 5% in USD, 12.6% AUD
+ Firm A can borrow at 7% USD, 13% AUD
+ Expected gain = (7-5) – (13-12.6) = 1.6%
>
Swaps:
+ Bank gains 1.3% on USD, loses 1.1% on AUD, gain=0.2%
+ Firm B gains (12.6-11.9) = 0.7%
+ Firm A gains (7-6.3) = 0.7%
> 
> Part of the reason for the gain is credit risk involved


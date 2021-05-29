---
title: Fixed Income
date: 2020-02-07
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

This notes is based on the class Financial Risk Management of NYU MFE, including basic conceptions of Fixed Income.

# Fixed Income Overview

## Fixed Income Market

+ identify primary risks
+ classify other risks which are incidental to the business
+ maximize return for a given level of risk

## Compared to Equity Market

### Why equity is special?

+ equity market is with much more volatility
  + because the residuals take over the leftovers and risks of bankruptcy

### Why Debt market size is larger than equity market?

+ Indebtedness outside of the Private Sector
+ __Cost and Other Benefits of Debt Financing__ and Leverage
  + loans / debt financing is cheaper than equity

### Why in emerging market, debt market and equity market is inverse?

+ emerging market is more likely to grow
+ then there is more volatility 
+ more currency to rush in

### Advantage of Fixed Income

+ Time Value of Money Cost of Carry
+ Key Instrument of Monetary Policy
+ Discounting Tool for All Other Asset Classes and Investments
+ Key Factor in the Balance Sheet of Financial Firms

+ for lenders: give your money back

# Bond Pricing

## Value of Bond

Price of a bond is the present value (PV) of the promised cash flows

+ Promised cash flows are __coupons__ and repayment of __principal__ at maturity

+ Coupon payments are on regularly scheduled dates

Market discount = yield

Valuation basics:
$$
PV = \frac{PMT}{(1+r)^1}+\frac{PMT}{(1+r)^2}+...+\frac{PMT+FV}{(1+r)^N}
$$
If $PMT < r$, priced at a discount below par.
$$
94.583 = \frac{2}{(1+3\%)^1}+\frac{2}{(1+3\%)^2}+\frac{2}{(1+3\%)^3}+\frac{2}{(1+3\%)^4}+\frac{2}{(1+3\%)^5}+\frac{102}{(1+3\%)^6}
$$
If $PMT > r$, priced at a premium above par.
$$
107.26 = \frac{6}{(1+4\%)^1}+\frac{6}{(1+4\%)^2}+\frac{6}{(1+4\%)^3}+\frac{106}{(1+4\%)^4}
$$
If $PMT = r$, priced at par
$$
100 = \frac{3}{(1+3\%)^1}+\frac{3}{(1+3\%)^2}+\frac{3}{(1+3\%)^3}+\frac{3}{(1+3\%)^4}+\frac{103}{(1+3\%)^5}
$$

## Yield to Maturity

### Three conditions

+ Holds the bond to maturity
+ Receives all coupon and principal payments (no default)
+ May __reinvest all coupon payments at the same yield__ (hard  to be realistic)

### Relationship between bond price and YTM

+ Inverse Effect: Duration
+ Convexity Effect: convexity
+ Coupon Effect
+ Maturity Effect: prices of a bond converge to par

## Quotes and Conventions

### Full Price and Flat Price

Relation:
$$
\text{Full (“Dirty”) Price} = \text{Flat (“Clean”) Price} + \text{Accrued Interest}
$$

+ Dealers __quote__ clean prices but __settle__ at the dirty price.

+ accrued interest

  $$
  \text{Accrued Interest} = \frac{t}{T} \times PMT
  $$
  where t is days from last coupon date to settlement and T is days in coupon period

  Days conventions:

  + U.S. Treasury notes, bonds (2 - 30 years): Semiannual, Actual / Actual basis
  + U.S. corporate bonds: Semiannual, 30/360 basis
  + European government and corporate bonds: Annual, Actual/Actual basis

Examples: 

+ A U.S. T bond with 5/15 and 11/15 coupon dates trades with settlement on 6/27. Calculate accrued interest based upon a 5% coupon:

  Actual days from 5/15 to 6/27 is 43, Actual days from 5/15 to 11/15 is 184.
  $$
  AI = \frac{43}{184}\times\frac{5.00}{2} = 0.584239 ~~\text{per \$100 of par}
  $$
  

### Discount basis or Add-on basis

Money market instruments are short term $(< 1 ~ \text{year})$ securities with annualized (not compounded) return measures quoted on a __discount__ or __add on__ basis

+ DR: U S commercial paper, Treasury bills and bankers’ acceptances

$$
PV = FV \times (1-\frac{Days}{Year}\times DR)
$$

+ AOR: Bank certificates of deposit (CDs), repurchase agreements and LIBOR / EURIBOR

$$
PV = \frac{FV}{(1+\frac{Days}{Year}\times AOR)}
$$



Example:

+ DR understates investor return / cost of borrowed funds as it divides by the total return at FV versus PV. For example, for a 90 day, $10 MM instrument:

  + T-bill @ DR of 2.25%
    $$
    \begin{eqnarray*}
    PV &=& FV \times (1-\frac{Days}{Year}\times DR) \\
    &=& 10 \times (1-\frac{90}{360}\times 0.0225) \\
    &=& 9943750
    \end{eqnarray*}
    $$

  + Bank CD @ AOR of 2.25%

  $$
  \begin{eqnarray*}
  PV &=& \frac{FV}{(1+\frac{Days}{Year}\times AOR)} \\
  &=& \frac{10}{(1+\frac{90}{360}\times 0.0225)} \\
  &=& 9944065
  \end{eqnarray*}
  $$

### Periodicity conversion

from m to n periods (i.e., from monthly to quarterly):

$$
\left(1 + \frac{APR_m}{m} \right)^{m} = \left(1 + \frac{APR_n}{n} \right)^{n}
$$

### Semiannual Bond Equivalent Yield

Most common periodicity for USD denominated bond yields is two. An annual rate having a periodicity of two is known as a semiannual bond basis yield, or semiannual bond equivalent yield.
Example: 

+ What is the SA bond equivalent for a zero priced at 78 2 maturing in 4 years?
  $$
  78.2 = \frac{100}{(1+r)^8} \\
  r = 0.0167
  $$
  Semiannual yield = 0.0334 

## Matrix Pricing

to price a new issued bond

### Principle of Matrix Pricing

Suppose a BBB rated pharmaceutical corporation intends to __issue a new five year bond__. The firm currently has a four year, 4 annual coupon bond outstanding which is priced at 103.1 (full and flat price with accrued interest of zero) The __four year rate of return rate__ required by investors is 3.16%:
$$
103.1 = \frac{4}{(1+r\%)^1}+\frac{4}{(1+r\%)^2}+\frac{4}{(1+r\%)^3}+\frac{104}{(1+r\%)^4}, ~r = 3.16\%
$$
Without a four year government bond to calculate a more precise yield spread, we look to three year
and five year ‘on the run’ government bonds yielding 2.10 and 2.45 respectively. The average of
the two yields is 2.2750%, which is the estimated four year benchmark yield.

The __estimated yield spread__ is 88.5 bps over the implied benchmark rate $(0.0316-0.02275 =0.00885)$. 

The issuer and underwriter then compare and adjust this four year yield spread based upon recent five year issues for companies __with similar ratings__ and/or in __the same industry__ for a proposed spread for the new issuance.

### Credit spreads

+ __Benchmark spread__ is the spread over the most recently issued government bond of similar maturity
+ __G-spread__ is the spread over actual or interpolated government bond with matched maturity
+ __I-spread__ is the spread over swap rates that match the credit security’s tenor and currency
+ __Z-spread__ is the zero volatility spread measured across each point along the implied spot yield curve
+ __Option adjusted spread (OAS)__ is a generalized Z spread and often most appropriate for portfolios

### Current yield

Current yield is sometimes called the __income or interest yield__ and is the __sum of coupon payments
received__ over the year divided by the __flat price__.

For example, a 10 year, 2 semiannual coupon payment bond is priced at 95 per 100 of par value Its current yield is $\frac{2}{95} = 2.105%$. This crude measure neglects coupon payment frequency in the numerator and accrued interest in the denominator

# Structure of Interest rates

## yield curve

### definition

The yield curve on coupon bonds is a snapshot of rates for non-callable securities with similar risk profile across maturities.

+ Yield curves generally have __a positive slope__ given the __higher risk of holding longer-term securities__
  + Investors typically demand a higher premium to lend for longer
  + The change in price for a given change in yield is higher for longer duration securities
+ Yield curve shape is dynamic, and the term structure is influenced by various factors
  + Short-term policy rates such as U.S. Federal Funds tend to drive short-term yields
  + Long-term Treasury yields are more affected by long-term inflation and growth expectations
  + U.S. Federal Funds have an impact on long-term yield by adjusting short-term yields

+ Term structure theories are driven by __expectations__, __segmentation__ and __liquidity preference__
  + Expectations theories rely solely on investor / issuer expectations of future short-term rates
  + Segmented market theory implies that investors / issuers have limited maturity selection
  + Liquidity preference theory combines risk and return as critical factors for issuers / investors

### shapes - tool to forecast economic activity

+ A positively sloped curve is generally associated with a future increase in real economic activity

+ __Curve flattening or inversion__ where short term yields exceed long term yields portends __a drop in short term rates and an expected decline in GDP__

![yield_curve_invision.png](https://i.loli.net/2020/02/11/t1LvP57m3b2GwrM.png)

Influence Factors:

+ Monetary policy (__tightening tends to slow the economy and flatten (or invert) the curve__) 
+ Investor expectations of future short-term rates as influenced by both credit demand and expected inflation 
+ General financial market conditions

### spot curves

Zero curves represent one cash flow on a pre-determined date. 

+ One example is for zero-coupon government bonds across maturities. This government bond spot curve (or zero or “strip” curve as individual coupons are “stripped” off of coupon bonds) is a set of yields-to-maturity on zero-coupon bonds. While often referred to as “risk-free” yields, this only refers to relative default risk, not inflation or liquidity risk.

### par curves

Par curves represent par value bonds maturing on pre-determined dates. 

+ In addition to the yield curve on coupon bonds and the spot curve on zero-coupon bonds, maturity structure can be assessed using a par curve. A par curve is __a sequence of yields-to-maturity such that each bond is priced at par value__. The bonds have the same currency, credit risk, liquidity, tax status, and annual yields stated for the same periodicity

### forward curves

Forward curves are a series of forward (future delivery) rates derived from spot rates. 

+ Implied forward rates (also known as forward yields) are calculated from spot rates as a break-even reinvestment rate linking return on investment in a shorter-term zero-coupon bond to that of a longer-term zero-coupon bond.

Example:

There are two alternative loans:

+ A is for 1 year at 2%; B is for 2 Years at 3%. Then $F_{1,1}$ is the one-year rate a year from now which equates 102 at year 1 to 106 at year 2:
  $$
  r = \frac{106}{102}-1 = 3.9216\%
  $$
  which means 
  $$
  102 \times 1.039216 = 106
  $$
  The implied forward rate may be checked by investing 102 for 1 year at this rate. This is also the basic principle of forward rate agreement(FRA):
  $$
  (1 + Z_A)^A \times(1+IFR_{A,B-A})^{B-A}=(1+Z_B)^B
  $$
  A is the shorter term bond in A periods. B is longer term bond in B periods.



# Source of bond risk

The market value sensitivity of a bond (or other rate sensitive instrument) to interest rate changes is
based on the bond valuation formula shown below based upon the full (or "dirty") price
$$
MV = \frac{PMT}{(1+y)^{1-\frac{t}{T}}} + \frac{PMT}{(1+y)^{2-\frac{t}{T}}}+ ... +\frac{PMT}{(1+y)^{N-\frac{t}{T}}}
$$
where MV is the full price, PMT is the coupon, FV is principal, y is yield per period and the bond settles t days into the T day period with N periods to maturity. It can be expanded as:
$$
dMV = (\frac{\partial MV}{\partial y}\times dy)+(\frac{1}{2}\frac{\partial^2 MV}{\partial y^2}\times dy^2)
$$
The first expression is a duration and the second term is a convexity, which are often shown divided by 100 on Bloomberg.

## Duration

### Macaulay duration

measures __the sensitivity of the bond’s full price__ (including accrued interest) to changes in the __bond’s yield to maturity__ or, more generally, to changes in __benchmark interest rates__. It assumes variables other than yield or benchmark rates (including time to maturity) are unchanged:
$$
\text{Macaulay Duration} = -\frac{\partial  \text{MV}}{\partial y}\times\frac{1+y}{MV}=-\frac{\frac{\partial  \text{MV}}{MV}}{\frac{\partial y}{1+y}}
$$
Duration measures __instantaneous (or same day) bond price changes__ and may be considered a
__weighted average__ (the share of full price corresponding to each cash flow) of the time to receipt of
promised cash flows. Using an annual coupon example on a coupon date, we can simplify
$$
\sum_{t=1}^{n}\frac{(\text{PV of CF})\times t}{PV^{full}}
$$
Example:

For a 6% annual coupon 5 year bond with 5% yield to maturity, the price is:
$$
\frac{6}{(1+r)^1}+\frac{6}{(1+r)^2}+\frac{6}{(1+r)^3}+\frac{6}{(1+r)^4}+\frac{106}{(1+r)^5} = 104.329477,~ ~ r=5\%
$$

| Period | Cash Flow | Present Value                  | Weight                          | Period $\times$ Weight |
| ------ | --------- | ------------------------------ | ------------------------------- | ---------------------- |
| 1      | 6         | $\frac{6}{(1+5\%)^1}=5.714$    | $\frac{5.714}{104.329}=0.0548$  | 0.055                  |
| 2      | 6         | $\frac{6}{(1+5\%)^2}=5.442$    | $\frac{5.442}{104.329}=0.0522$  | 0.104                  |
| 3      | 6         | $\frac{6}{(1+5\%)^3}=5.183$    | $\frac{5.183}{104.329}=0.0497$  | 0.149                  |
| 4      | 6         | $\frac{6}{(1+5\%)^4}=4.936$    | $\frac{4.936}{104.329}=0.0473$  | 0.189                  |
| 5      | 106       | $\frac{106}{(1+5\%)^5}=83.054$ | $\frac{83.054}{104.329}=0.7961$ | 3.981                  |
|        |           | 104.329                        | **Duration**                    | 4.478                  |

### Modified duration

Modified duration is a minor adjustment to Macaulay duration (dividing by 1 + yield per period) and is
directly related to the percentage change in a bond’s market value:
$$
\text{Modified Duration} = -\frac{\text{Macaulay Duration}}{(1+\frac{r}{c})}
$$
This is a linear estimate of a fixed-rate bond's price change for a given yield to maturity change:
$$
\%\Delta PV = -\text{Modified Duration} \times\Delta\text{Yield}
$$
Example:

How does the bond price in the prior example (6% annual 5 yr coupon bond with a 5% yield to maturity) change if yields decline 100 bps?

Given a Macaulay Duration of 4.478, the Modified Duration is $\frac{4.478}{1.05}=4.265$. Therefore,
$$
-4.265 \times (-100bps) \times \%= 4.265\%
$$
there will be 4.2645% price appreciation.

The error:

For original bond price:
$$
\frac{6}{(1+r)^1}+\frac{6}{(1+r)^2}+\frac{6}{(1+r)^3}+\frac{6}{(1+r)^4}+\frac{106}{(1+r)^5} = 104.329477,~ ~ r=5\%
$$
For the new price estimate:
$$
104.329477 \times (1 + 4.2645\%) = 108.77863
$$
For the Actual new bond price:
$$
\frac{6}{(1+r)^1}+\frac{6}{(1+r)^2}+\frac{6}{(1+r)^3}+\frac{6}{(1+r)^4}+\frac{106}{(1+r)^5} = 108.903645,~ ~ r=4\%
$$
There are $108.90365 - 108.77863 = -.125$ difference in price explained by the non-linearity of the price-yield relationship.

### Effective Duration

Effective Duration is __the sensitivity of a bond’s price__ to __a change in a benchmark yield curve__ such as a __government par curve__, similar to approximate modified duration except it involves a benchmark and also may be used for more complex bonds or portfolios of complex bonds
$$
\text{Effective Duration} = \frac{PV_{-}-PV_{+}}{2\times(\Delta\text{Curve})(PV_0)}
$$

### Money Duration (Dollar Duration)

Dollar Duration is __the price change__ for a given change in yield in units of the currency in which the bond is denominated (as opposed to a percentage change) stated per 100 of par or based upon an actual
portfolio position (known as “dollar duration in the U.S.)
$$
\text{Dollar Duration} = -\frac{\partial MV}{\partial y}=\text{Modified Duration}\times MV
$$

$$
\Delta PV = -\text{Dollar Duration} \times\Delta\text{Yield}
$$

A related statistic is the present value of a basis point:
$$
\text{PV of a Basis Point} = \frac{PV_{-} - PV_{+}}{2}
$$
This is the dollar value (DV01) or present value of a basis point (PV01), which is calculated by increasing and decreasing the yield by 1 bp to get the price change.

### Portfolio Duration

Portfolio duration is __the sum of market value weighted durations__ of component positions.

+ Positive is a long position and negative is a short position 
+ Practitioners use duration and DV 01 PVBP statistics to analyze cash and synthetic positions to gauge net exposure, profitability and/or evaluate trade ideas

Example:

A bond trader holds two 2 year U.S. Treasury notes and one 30 year U S Treasury bond. Each bond has a face value of $1000000 with 2 year duration of 1.94 and the 30 year duration of 19.69.

+ Portfolio duration is $7.86 = \frac{2}{3} \times 1.94 + \frac{1}{3} \times 19.69$

+ Portfolio DV01 equals $7.86 \times \frac{\$3000000}{10 000} = \$2358$

+ If 2 year and 30 year yields rise 10 bps, her portfolio LOSS $\$23580 = \$2358 \times 10 bps$

Coupon: For zero-coupon bonds, duration = maturity. As  Coupons increase, duration decrease.

Maturity: increase as maturity increase.

Time: As maturity decrease to 0, time goes down

Yield: As yields increase, duration decrease.

## Convexity

While modified duration is a linear approximation of price changes for a given change in yield, the true price/yield relationship is a convexity adjusted equation expressed as follows:
$$
\%\Delta PV = -\text{Modified Duration} \times\Delta\text{Yield} + \frac{1}{2}\times\text{Convexity}\times(\Delta Yield)^2
$$
The second convexity term is positive for traditional (option free) fixed rate bond for a yield increase or decrease. Convexity may be calculated with tables, precisely derived or closely approximated:
$$
\text{Convexity} = \frac{PV_-+PV_+}{(\Delta \text{yield})^2\times PV_0}
$$
Example:

Calculate the change in full bond price from the prior example (6% annual 5 yr coupon bond with a 5% yield to maturity) given a 100 bp yield decline with the convexity adjustment?

At a yield of $5\%$, the bond price was $104.329477$ and the Modified Duration is $4.264525$, so
$$
\%\Delta \text{PV}=-4.264525 \times\Delta\text{Yield} = 4.2645\%
$$
The approximate convexity with the bond price at 4.99%, 5.00%, 5.01% ($\Delta \text{Yeild}=0.0001$) as follows:
$$
\frac{6}{(1+r)^1}+\frac{6}{(1+r)^2}+\frac{6}{(1+r)^3}+\frac{6}{(1+r)^4}+\frac{106}{(1+r)^5} = 104.3739805,~ ~ r=4.99\%
$$

$$
\frac{6}{(1+r)^1}+\frac{6}{(1+r)^2}+\frac{6}{(1+r)^3}+\frac{6}{(1+r)^4}+\frac{106}{(1+r)^5} = 104.3294767,~ ~ r=5\%
$$

$$
\frac{6}{(1+r)^1}+\frac{6}{(1+r)^2}+\frac{6}{(1+r)^3}+\frac{6}{(1+r)^4}+\frac{106}{(1+r)^5} = 104.2849973,~ ~ r=5.01\%
$$

According to the formula:
$$
\begin{eqnarray*}
\text{ApproxCon} &=& \frac{\text{PV}_{-}+\text{PV}_{+}-2\text{PV}_{0}}{(\Delta \text{Yield})^2 \times \text{PV}_{0}} \\
&=&\frac{104.3739805 + 104.2849973 -2\times104.3294767}{0.0001^2\times104.3294767} \\
&=& 23.444
\end{eqnarray*}
$$
Therefore, the full price change percent is:
$$
\begin{eqnarray*}
\%\Delta\text{PV} &\approx& -4.264525 \times 0.01 + \frac{1}{2}\times23.444\times0.01^2 \\
&\approx& 0.043817455
\end{eqnarray*}
$$
the convexity-adjusted price increase given -1% in yield is $4.3817455\%$, which is a $0.0026%$ difference compared to the actual price increase.

## Bond Portfolio Risk

### Bond Portfolio Duration and Convexity

__Duration is the primary measure of price risk__ arising from a change in the yield to maturity. 

+ It is most important over short time horizons where investor focus is on price as opposed to coupon reinvestment risk.
+ Duration is also referred to as __repricing risk__, and it is important to note that variable rate instruments with longer maturities have short duration dictated by the timing of that repricing (such as 3 month LIBOR)

__Convexity represents a secondary measure of price risk Investors may benefit from positive convexity__, for example, a 100 year or century bond will exhibit much higher convexity than a 30 year bond despite similar duration, resulting in a larger gain amid declining interest rates.

Callable bond investors expect to be compensated for the uncertainty related to final maturity which these bonds exhibit in terms of negative convexity (i e bond price appreciation amid falling rates is effectively capped by the call feature)

### Portfolio Duration and Convexity

__Duration for a fixed income bond portfolio__ may be calculated in two ways:

+ Weight the average time to receipt of the aggregate cash flows (which is theoretically correct but difficult to put into practice)
+ Weight the average of individual bond durations within the portfolio

$$
\text{MV}=\frac{CF_1}{(1+\text{Yield of Portfolio})^1}+\frac{CF_2}{(1+\text{Yield of Portfolio})^2}+...+\frac{CF_N}{(1+\text{Yield of Portfolio})^N}
$$

Theoretically, the formula above should be based upon a homogenous non-callable bond portfolio where the full and flat price are equal, but in practice, the weighted averages are used:
$$
\begin{eqnarray*}
\text{AvgMacDur of Portfolio} &=& \sum_{j=1}^{J}\text{MacDur}_j\times\left(\frac{\text{MV}_{j}}{\text{MV}}\right) \\
\text{AvgModDur of Portfolio} &=& \sum_{j=1}^{J}\text{ModDur}_j\times\left(\frac{\text{MV}_{j}}{\text{MV}}\right) \\
\text{AvgConvexity of Portfolio} &=& \sum_{j=1}^{J}\text{Convexity}_j\times\left(\frac{\text{MV}_{j}}{\text{MV}}\right)
\end{eqnarray*}
$$

### Source of Bond YTM Changes

Yield changes may originate in either benchmark or spread changes or a combination of the two
components.

__Credit spread example__:

A risk manager is tasked with weighing the relative risk of two spread positions under a recession scenario
Bond 1 has modified duration of 3.00 and a convexity of 24.00 and is expected to face 25 bps of spread
widening, and Bond 2 has modified duration of 5.00 and a convexity of 40.00 and is expected to see
spreads widen by 15 bps in a downturn. Which bond has more price risk? Bond 2 has slightly more risk:
$$
\% \Delta \text{PV}_\text{Full} \approx (-3\times0.0025) + \left[\frac{1}{2}\times24\times(0.0025)^2\right] \approx-0.007425 \\
\% \Delta \text{PV}_\text{Full} \approx (-5\times0.0015) + \left[\frac{1}{2}\times40\times(0.0015)^2\right] \approx-0.007455
$$
__Liquidity example:__

A trader’s boss wants her to gauge the precise bid offer cost of liquidating a thinly traded corporate bond
position The face value is $\$120 000 000$ with a modified duration of 4.5 and convexity of 35 and the bid
offer cost is expected to be 5 bps What is the estimated cost of trading the position?
$$
\%\Delta\text{PV} \approx -4.5 \times 0.0005 + \frac{1}{2}\times35\times0.0005^2 \approx -0.002245625
$$
That means the estimated trading cost using modified duration only is
$$
$120000000\times-0.0022445625 = -$269475
$$


# Other Products

## Risk free rate: Repurchase agreement





## Interest Rate Swap





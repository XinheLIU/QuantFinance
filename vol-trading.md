# Volatility Trading

## Option Pricing in Reality

Black-Scholes equation

$$\frac{1}{2}\sigma^2 S^2 \Gamma + \Theta + r(C = \Delta S ) = 0$$

is more general than the formula. It's very robust, most assumptions could be loosened without hurting too much it's utility. In reality, the option pricing usually is usually based on the formula.

Some general guidance

* option is a non-linear (leveraged), timed (with maturity) bet on price movements.
* "Option Pricing" is a misleading term, it only maps option prices to a simplied, slower changing parameter - implied volaility
* As the formula tells, Gamma and volatility of price change is crutial for instaneous PnL for hedged options, while vega is realized sum of PnL as we rebalances

Deal with B-S Assumptions

* Existence of tradable underlying: real options could be hard to hedge, liquidity issue and proxy hedges are considered in reality
* Dividend/Storage Costs:
  * continous dividend is usually assumed and needs to be carefully examined
  * Short-selling is costly in reality, fake dividend yields can reflect the costs
  * If underlying is future the effective cost to finance is zero
* Ability to short
  * Costs must be accounted
* Single, Constant Rate
  * [Black's formula](https://en.wikipedia.org/wiki/Black_model) is used to calibrate together with forward rates
  * Short-term options are probably ok
* Tax
  * the market price at the cost of marginal investor, each investor, domestic, foreign, could be treated differently
* Underlyings can be traded at Any size
* Transaction Cost
  * Trading Underlyings are costly
* Volatility is Constant
  * Inconsisitency of the model, reflected in "vega"
* Distribution of the return
  * Volatilty is the only measure, impling the return is assumed to be normally distributed, which is unreal, **tail risk** is significant.
  
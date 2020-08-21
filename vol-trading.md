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
  
## Volatility Measurements

* Volatility is unobservable, there are hundreds of different measures for volatility
* The most appropriate measure hinges upon the usage of the measurement
  * In derivatives pricing, the consistency of prices (volatility surface) is most important
  * In portfolio management, the link between risk and smoothness (and covariances) matter most
  * In trading, questions are
    * how far/fast price moves
    * how fast price moves
    * how frequent we trade/gets exposed to risk

### Common Types of Volatility Estimators

See summaries in 

Poon, S. 2005. A Practical Guide to Forecasting Financial Market Volatility. London:
John Wiley & Sons.

* [Unbiased estimation of standard deviation](https://en.wikipedia.org/wiki/Unbiased_estimation_of_standard_deviation) based on close-to-close data
  * Notice estimator is not [efficient](https://en.wikipedia.org/wiki/Efficient_estimator), it converges to real value slowly
* Empircal estimation on daily-return:
  * $$19.896\frac{11}{N} \sum R_i$$
  * assuming normal, $E[|R_i|] = \sqrt{\frac{2}{\pi}} \sigma$
* Popular Estimations based on hign and low to capture price movements
  * Need to capture in drifts, jumps, biases etc, otherwise will be bias downwards
  * Performance degrades to close-to-close volatility
  * Examples
    * Parkinson, M. 1980. ‘‘*The Extreme Value Method for Estimating the Variance of the Rate of Return.*’’ Journal of Business 53:61–68.
    * Garman, M. B., and M. J. Klass. 1980. ‘‘*On the Estimation of Security Price Volatilities from Historical Data.*’’ Journal of Business 53:67–78.
    * Rogers, L., and S. Satchell. 1991. ‘‘Estimating Variance from High, Low and Closing Prices.’’ Annals of Applied Probability 1:504–512.
    * Yang, D., and Q. Zhang. 2000. ‘‘*Drift-Independent Volatility Estimation Based on High, Low, Open, and Close Prices.*’’ Journal of Business 73:477–491.
* Estimation based on stochastic process(Brownian Motion) hitting times
  * Brandt, M. W., and J. Kinlay. 2005. ‘‘*Estimating Historical Volatility.*’’ Research article, Investment Analytics. www.investment-analytics.com.
* Estimation using the information from high-freqency data
  * Need to deal with overnight return (after hours)
  * Nedd to deal with intraday seasonalities
  * Examples
    * Ait-Sahalia, Y., P. Mykland, and L. Zhang. 2005. ‘‘*How Often to Sample a Continuous-Time Process in the Presence of Market Microstructure Noise.*’’ Review of Financial Studies 18:351–416.
  * In fact, lower frequency estimator is a better estimation for higher frequency volatility than vice versa, see
    * Corsi, F. 2009. ‘‘*A Simple Long Memory Model of Realized Volatility.*’’ Journal of Financial Econometrics 7:174–196
    * Lynch, P., and G. Zumbach. 2003. ‘‘*Market Heterogeneities and the Causal Structure of Volatility.*’’ Quantitative Finance 3:320–331.

## Model Volatility

### "Stylized facts" about Volatility

Survey

* Cont, R. 2001. ‘‘*Empirical Properties of Asset Returns: Stylized Facts and
Statistical Issues.*’’ Quantitative Finance 1:223–236.

Some observed feature about volatility, robust with different measure include

* [**Volatility Clustering**](https://en.wikipedia.org/wiki/Volatility_clustering)
  * clustering tends to be longer in developed markets
  * larger and faster decaying autocorrelation in bear market/market crash
* mean-reverting
  * but the mean moves
  * Test mean-reverting: variance ratio test
    * Campbell, J., A. Lo, and A. MacKinlay. 1997. *The Econometrics of Financial Markets*. Princeton, NJ: Princeton University Press.
* Asymetry 
  * The distribution of return is skewed (with excess kurtosis, most from overnight return moves), it has fat tails
* **Leverage Effect** - Volatility increases more when price declines
  * Studies
    * Black, F. 1976. ‘‘Studies of Stock Price Volatility Changes.’’ Proceedings of the Meetings of the American Statistical Association, Business and Economics Section, Chicago, 177–181.
    * Christie, A. 1982. ‘‘The Stochastic Behavior of Common Stock Variances: Value, Leverage and Interest Rate Effects.’’ Journal of Financial Economics 10:407–432
    * Edderington, L., and W. Guan. 2010. ‘‘How Asymmetric Is U.S. Stock Market Volatility?’’ Journal of Financial Markets 13:225–248
    * Abura, S., and N. Wagner. 2010. ‘‘Extreme Asymmetric Volatility, Leverage, Feedback and Asset Prices.’’ Universite de Paris Dauphine working paper.
    * Jensen, M., A. Johansen, and I. Simonsen. 2003. ‘‘Inverse Fractal Statis- tics in Turbulence and Finance.’’International Journal of Modern Physics B 17: 4003–4012.
      * Other measures show same broader effects
* Correlated with Volume (spikes)
  * Tauchen, G., and M. Pitts. 1983. ‘‘*The Price Variability-Volume Relationship on Speculative Markets.*’’ Econometrica 51:485–505.
  * Andersen, T. 1996. ‘‘*Return Volatility and Trading Volume: An Information Flow Interpretation of Stochastic Volatility.*’’ Journal of Finance 51:169–204.
* Distribution of Volatility
  * Log-normal with fat tail (could be modelled by power law distributions), heavily skewed to the right
  * Studies
    * Cizeau, P., Y. Liu, M. Meyer, C. Peng, and H. Stanley. 1997. ‘‘Volatility Distribution in the S&P500 Stock Index.’’ Physica A 245:441–445.
    * Andersen, T., T. Bollerslev, F. Diebold, and H. Ebbens. 2001. ‘‘The Distribution of Stock Return Volatility.’’ Journal of Financial Economics 61:43–76.
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

### Volatility Forecasting

The reason traders build volatility forecasting models is they belief it's more efficient than spot market because of

* Transaction cost and complexity of option products
  * eg.
    * capital structure arbitrage - equity option + credit products to implement
    * index vs component options - complicated to implement
* Options contains inside informations 
  * Bradley, D., B. Cline, and Q. Lian. 2009. ‘‘*Do Insiders Practice What They Preach? Informed Option Exercises around Acquisitions.*’’ Available at www.ssrn.com, SSRN-id1364787.
  * Arnold, T., G. Erwin, L. Nail, and T. Bos. 2000. ‘‘*Speculation or Insider Trading in Option Markets Preceding Tender Offer Announcements.*’’ University of Alabama at Birmingham working paper. Available at http://ssrn.com/ abstract=234797.

#### Forecasting Models

Time-series models

* [EWMA ](https://www.investopedia.com/articles/07/ewma.asp) Models
  * [Half-life](https://quant.stackexchange.com/questions/46194/half-life-of-exponetial-weighted-moving-average#:~:text=The%20half%2Dlife%20is%20the,(12)1%CF%84.)
  * Drawbacks: did not take in consideration of the effect of mean-reverting
* GARCH Family
  * GARCH
    * $$\sigma^2_{t+\tau} = \gamma V + \alpha r^2_{t+\\tau-1} + \beta \sigma^2_{t+\\tau-1} $$
    * $$\sigma^2_{t+\tau} -V = (\alpha + \beta)E[\sigma^2_{t+\\tau-1} - V]$$
    * The long-term variance $\omega = \gamma V$ is usually set to be $(1-\alpha\\beta)$ times sample variance
  * Other extensions see
    * Hansen, P. R., and A. Lunde. 2005. ‘‘*A Comparison of Volatility Models: Does Anything Beat a GARCH (1,1)?*’’ Journal of Applied Econometrics 20:873–889.
      * EGARCH, GJR-GARCH, IGARCH, TGARCH, AGARCH, CGARCH, etc
    * Sato, A. H., and H. Takayasu. 2002. ‘‘*Derivation of ARCH(1) Process from Market Price Changes Based on Deterministic Microscopic Multi-Agent.*’’ In Empirical Science of Financial Fluctuations, edited by H. Takayasu, 172–178. Tokyo: Springer.

[Volatility Cone](https://www.globalcapital.com/article/k6b8kytp99dk/volatility-cones)

* A comparison vs historical volatility
* a rough teller of the edge you have, but must consider other factors (eg. single name bet could be easier than index options)

Research

* Hodges, S., and R. Tompkins. 2002. ‘‘*Volatility Cones and Their Sampling
Properties.*’’ Journal of Derivatives 10:27–42.

Fundamental information based forecasters

* Sridharan, S. 2012. ‘‘Volatility Forecasting Using Financial Statement Informa-
tion.’’ Stanford University Graduate School of Business working paper. Available
at www.ssrn.com, SSRN-id 1984324.

## Implied Volatility

In most cases, trading volatility is trading the difference of implied and realized volatility (eg. Gamma Scalping).

* Technically, the realized volatiltity should be compared with Volatility Swap/[Variance Swap](https://en.wikipedia.org/wiki/Variance_swap) price (weighted average of infinite number of options)
* Practically, the ATM implied volatility is representive of overall volatility level (much more important than shape) so it is used

### [Variance Risk Premium](https://en.wikipedia.org/wiki/Variance_risk_premium#:~:text=Variance%20risk%20premium%20is%20a,the%20realized%20variance%20on%20average.&text=The%20amount%20that%20the%20buyer,as%20the%20variance%20risk%20premium.)

* Selling volatility is like selling insurance, but not likely to be profitable because
  * insurance companies profit by investing the premium, this is not the case for option traders who usually bears a funding cost
  * tail risk is hard to price accurately and tail events can hurt a lot

Relevant Academic works

* Bakshi, G., & Kapadia, N. \(2003\). *Volatility Risk Premiums Embedded in Individual Equity Options. The Journal Of Derivatives*, 11\(1\), 45-54. doi: 10.3905/jod.2003.319210
* Bakshi, G., and N. Kapadia. 2003. ‘‘*Delta-Hedged Gains and the Negative Market Volatility Premium.*’’ Review of Financial Studies 16:527–566.
* Bakshi, G., and D. Madan. 2006. ‘‘*A Theory of Volatility Spreads.*’’ Management Science 52:1945–1956.
* Bollen, N., & Whaley, R. \(2002\). *Does Net Buying Pressure Affect the Shape of Implied Volatility Functions?*. SSRN Electronic Journal. doi: 10.2139/ssrn.319261
* Bondarenko, O. \(2003\). Why are Put Options So Expensive?. SSRN Electronic Journal. doi: 10.2139/ssrn.375784
* Broadie, M., Johannes, M., & Chernov, M. \(2007\). *Understanding Index Option Returns. SSRN Electronic Journal*. doi: 10.2139/ssrn.965739
* Garleanu, N., Pedersen, L., & Poteshman, A. \(2005\). *Demand-Based Option Pricing.* SSRN Electronic Journal. doi: 10.2139/ssrn.676501

### [Implied Volatility Surface](http://faculty.baruch.cuny.edu/jgatheral/ImpliedVolatilitySurface.pdf)

Many researches have been done to reduce the dimensionality/rank the importance (eg. PCA) of volatility movements (eg. level + tilting + curvature change). But overall the level movement is the most important thing

* Derman, E., and M. Kamal. 1997. ‘‘The Patterns of Change in Implied Index Volatilities.’’ Quantitative Strategies Research Notes. Goldman Sachs.
* Skiadopoulos, G., S. Hodges, and L. Clelow. 2000. ‘‘The Dynamics of the S&P
* 500 Implied Volatility Surface.’’ Review of Derivatives Research 3:263–282.
* Alexander, C. 2001b. ‘‘Taming the Skew.’’ Futures and Options World 367:60–65.

### Implied Volatilty Level

* [VIX](https://en.wikipedia.org/wiki/VIX) is the typical representitive
* Modelling
  * Mean-reversion
    * eg. $R_t = \rho(R_{t-1} - \mu) + \mu +\sigma Z_t$
    * Use [Technical Indicators](https://www.investopedia.com/terms/t/technicalindicator.asp#:~:text=Technical%20indicators%20are%20heuristic%20or,to%20predict%20future%20price%20movements.) such as Bollinger Bands  for informal tests
  * Formal time-series models - limited practical use
    * Ahoniemi, K. 2006. ‘‘Modeling and Forecasting Implied Volatility: An Econometric 261 Analysis of the VIX Index.’’ Discussion Paper 129, Helsinki Center of Economic Research.
    * Brooks, C., and M. Oozeer. 2002. ‘‘Modeling the Implied Volatility of Options on Long Gilt Futures.’’ Journal of Business, Finance and Accounting 29:111–137.
  * Fundamental based models
    * Use P/E ratio, P/B ratio, etc to draw conclusions
      * general finding is that when dispersion (disagreements) is large, the volatility is high
    * Research
      * Panos, G. 1997. ‘‘Trading the Unemployment Report.’’ Carr Futures Market Insight,February.
      * He, W., Y. Lee, and P. Wei. 2010. ‘‘*Do Option Traders on Value and Growth Stocks React Differently to New Information?*’’ Review of Quantitative Finance and Accounting 34:371–381.

### Volatility Smile

Two widely used heuristics

* Sticky-strike rule: volatility of given strike not change when underlying moves
  * Delta-neutral call spread (weighted by gamma) will always have positive gains
* Sticky-delta rule: options with given delta percentage will likely to have similar volatility
  * $\frac{dC}{dS} = \Delta_{BSM} + \text{vega} \frac{\partial \sigma}{\partial S}$

Research

* Kamal, M., and E. Derman. 1999. ‘‘Correcting Black-Scholes.’’ Risk 12:82–85.
* Derman, E. 1999. ‘‘Regimes of Volatility.’’ Quantitative Strategies Research Notes. Goldman Sachs.

#### Smile Dynamics

The reason smile exists

* fat-tail distribution: skneness and kurtosis
* buying pressure on different options
  * dealers sell puts buy calls and hedge, stock owners sell calls and buy puts and don't hedge
    * if the market drops, market impact of hedging will increase volatility (momentum)
  * tail risk insurance selling has a premium
  * correlation also spikes when market movements
    * correlation risk premium of index options vs single name options

To model/parameterize smile, normal distribution assumptions are modified with kurtosis and skewness. (by ***Gram-Charlier expansion***) eg. the **Corrado-Su model**.

* Jarrow, R., and A. Rudd. 1982. ‘‘Approximate Option Valuation for Arbitrary Stochastic Processes.’’ Journal of Financial Economics 10:347–369.
* Corrado, C., and T. Su. 1996. ‘‘Skewness and Kurtosis in S&P 500 Index Returns
* Implied by Option Prices.’’ Journal of Financial Research 19:175–192.

negative option prices are possible under such models, some improvements are made on boundary conditions, also it's not hard to expand the idea to American option(tree-based) pricing.

* Rubinstein, M. 1998. ‘‘Edgeworth Binomial Trees.’’ Journal of Derivatives 5:20–27.
* Jondeau, E., and M. Rockinger. 1999. ‘‘Estimating Gram-Charlier Expansions with Positivity Constraints.’’ Working paper, Banque de France.
* Haug, E. 2007b. The Complete Guide to Option Pricing Formulas. New York:
* McGraw-Hill.

### Term Structure

Model instaneous and forward volatility. In practice, the change in back-month contract volatility is much wider than front-month ones (not consisitent v. mean-reversion) it **overracts**.

* Stein, J. 1989. ‘‘Overreactions in the Options Market.’’ Journal of Finance 44:
1011–1023.
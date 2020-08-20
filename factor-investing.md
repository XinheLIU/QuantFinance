# Factor Timing and Crowding

---

### Factor Crowding Analysis

"The Impact of Crowding in Systematic ARP Investing"

#### Goal

Impact of factor crowding for ARP strategies profitabilities and risks

#### Assumptions

* the definition of "crowdness"
  * should be the impact on return \(response variable\) rather than overall ARP size
    * return crash \(factor crash\)
    * market capacity and market impact
  * relevant research
    * equity momentum crash
    * benefit of volatility-targeting overlay
    * valuation spreads as factor timing indicators
* two types of risk premia
  * risk premia/negative feedback loops 
    * \(share risk, eg. **value\(distressed risk\), volatility**\) - compensation for undiversifiable risk
  * investor trading shrinks the valuation spread
    * price anomalies/positive feedback loops, momentum, behavior driven, limits to arbitrage\)
    * investor trading inflates the trading signal
    * unstanstanable - eg.** funding liquidity and momentum **strategy
  * convergence vs divergence
    * convergence: flow in will lead negative feedback strategies to lose alpha
    * divergence flow will lead positive feedback strategies to 
* measure of crowdness
  * pairwise correlation of factor-adjusted returns of assets in the same peer group \(high/low factor score\)
  * motivated by Cahan and Luo\(2013\), Lou and Polk\(2014\) and Huang Lou and Polk\(2018\)

#### Findings

* divergence strategies exhibits lower return and higher volatility after crowding
* convergence strategies exhibits higher return and lower volatility in crowded periods

#### Tests

* two types of risk premia
  * turn over of global equity momentum/value return vs 1y turnover
    * momentum negatively correlated, value positively correlated 
* measure crowdness
  * input to the system: flows data and positioning data 
  * output to the system: price, movement and asset co-movement and valuation spreads
    * positioning data has problem of depth, timeliness of availability and historical and asset coverage problem
    * synchronous asset comovement \(as a portfolio\) might be affected by the inflow of factors
      * Cohan and Luo\(2013\) are the first to use pairwise correlation of a group of U.S. stocks that share a common characteristics \(by factor scores, eg. top momentum\) to indicate factor crowdness
  * measure: 
    * peer group correlations: use a regression to get factor return, then rolling 52 week **co-movement **metrics
    * utilization by securities lending data: for top and bottom tier baskets \(larger utilization of un-attractive basket of stocks, more crowded
* Data
  * single stock universe 
  * cross section of commodities and FX
    * 26 currency pairs against USD, 24 GSCI commodity indices
  * use ARP Allocation mechanism to form factor portfolios
  * return data
    * adjust factor portfolio return by other factors \(eg. in equity, if use a 4 factor model, adjust momentum by market, value and size\)
* Hypothesis \(Oct2005-May2018\)
  * two samples: form a metric \(co-movement\) during periods of higher and lower crowding \(top 20% vs bottom 20%\)
  * Impact on return: 
    * H-0: no impact on subsequent 2y buy-and-hold return
    * Newey and West standard errors
    * 6month period to observe most significant return effect for divergence strategies
    * H1 holds
  * Impact on risk
    * H0: after crowded period: convergence/divergence period t 1y\(t-t+1y\) volatility and skewness is not change
    * divergence: strong evidence more volatile after crowding period
    * convergence: weaker results crowding will stablize the portfolio
    * no statistically strong results on skewness
    * Wilcoxon Rank-Sum effect
  * volatility during transition period
    * test $$\frac{\sigma_{t,t+\Delta t}}{\sigma_{t',t'+\Delta t}}$$ vs next 66-day same ratios
    * strong results for convergence strategies

backtesting

* cometric on alternative risk premia strategies

---

### Factor Timing Methods Review

* Background
  * efficient market does not mean zero predictability - beta factors in equities, bonds, credit, FX, real estate
  * most ARP suffer from overfitting, but shoes some predicatibility
    * in equity "anomalies", FX Carry, bond, etc 
  * business cycle significantly affects value/momentum/carry strategies
* Timing based on economic conditions
  * "nowcasting" 
    * developed market vs emerging market, inflation\(imported, input, wage...\), market stress \(liquidity, spreads, volatility...\)
    * diffusion index + nowcaster
  * business cycle
    * expansion: Momentum, slowdown: min vol quality, contraction: min vol, quality, recovery: size, value

### Factor Timing Effectiveness

Test the statistical possibility of factor timing

* Assumptions: folded normal distribution and p% of time successful timing on return
* Tests
  * Single Strategy
    * normal distribution test
    * t distribution Monte Carlo Simulation
    * test common timing signals **hit ratios**: 
      * commodities, equities, FX, Rates/Credit with hit ratios
  * Multiple Portfolio Test
    * weighting scheme for the active weights, should increase with forecasting skill vs equal weight vs worst\(all wrong\)
    * active weight 20%, constant correlation simulation and **block bootstrap **\(1000 iternations\)
    * parameters \(correlation \(higher the better\)\) active weight \(there is an optimal\)
* Conclusion: 
  * required forecasting skill to outperform \(mean return\) increases substantially with high Sharpe Strategies
  * **diversification** \(low correlation\) raises the bar of timing benefit
  * next step: focus on the magnitude and strategy turnover \(transaction cost\)

### Factor Timing Metrics

* Used Embedded metrics as factor timing indicators
  * valuation/carry/momentum: inner product between weight vector and vector of characteristics
  * co-movement/crowding: average market-adjusted cross-correlation of strategy constituents
  * factor momentum: serial correlation over pre-determined window
* Assumptions - works like technical analysis on factors
  * risk based characteristics: like value and carry, expected to exhibit longer-term predictive ability
  * price-based characteristics, like trend/factor momentum, expected to exhibit short-term predictive ability
  * crowding; expected to have medium term predictive ability
  * relies on mean reversion 
* Analysis
  * in-sample analysis: regression with future strategy performance vs . average monthly metric over multiple horizons
    * linear
    * non-linear: convexity on left tail- rebound, concavity on right tail - crash
  * out-of-sample analysis: timed strategy use the metrics
    * tilt based on capped z-score
* Caveats
  * high-turnover strategies: may not able to use long-term signal
  * hindsight bias and artificial correlation of longer horizons

---

### ESG as a Factor

* S
  * ESG Could be related to productivity \(eg. work-life balance\), Use ESG as a single factor or as a filter \(filter out low scoring ones - overlay\)
* T
  * test the effectiveness as a factor
  * control ESG risk will filter out small caps
* A
  * try ESG as a factor score model and long-short portfolio 
  * test correlation with existing factors
  * make part of another factor 
    * eg. Quality + ESG
  * as a filter \(parameter: thredhold\)
* R
  * no statistical effectiveness as a factor
  * with filtering, can achieve similar risk/return with better ESG Score
* Potential Problems/Challenges
  * no standard/transparent ESG Score
  * data is limited \(new thing\)

---

### Risk-Premia Factor in Strategic Asset Allocation

* Problem: Substitute traditional assets with lower cost and more robustness
* Assumptions: based on PCA \(or KNN\) analysis to cluster risk-return characteristics
  * Eq like: Volatility Carry\(short Vol\) Strategies
  * Duration like: low beta equity, unconstrained bond strategies, etc
  * CTA like: momentum and time series momentum strategies
  * Diversified: Value, Size, Curve
  * Dispersion and Structure imbalance like strategies
* Analysis: Comparing with standard \(risk parity or generalized risk parity\) cross-asset portfolio, with different constraints\( eg. beta control, drawdown control\)
  * substitute similiar strategies
  * compare conditional Sharpe \(or similar\) performance/drawdown




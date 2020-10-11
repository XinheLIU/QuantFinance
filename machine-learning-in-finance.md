# Application of Machine Learning in Finance

## Recommended Readings

- [Advances in Financial Machine Learning\(Course\)](http://www.quantresearch.org/Lectures.htm)
- [Advances in Financial Machine Learning](https://www.amazon.com/Advances-Financial-Machine-Learning-Marcos/dp/1119482089/ref=pd_bxgy_img_2/135-6445280-8934461?_encoding=UTF8&pd_rd_i=1119482089&pd_rd_r=fc9db682-7dce-4526-8ae8-4f973d4b466a&pd_rd_w=RaRsQ&pd_rd_wg=NDtW2&pf_rd_p=4e3f7fc3-00c8-46a6-a4db-8457e6319578&pf_rd_r=36KPG2961YA4J9M0NH0W&psc=1&refRID=36KPG2961YA4J9M0NH0W)
- [Machine Learning for Asset Managers \(Elements in Quantitative Finance\)](https://www.amazon.com/dp/1108792898/ref=sspa_dk_detail_0?psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEyVzBVS0E3TFlOOUNMJmVuY3J5cHRlZElkPUEwNDA0NjQyMjU3VkdKQlQ0OTI4QyZlbmNyeXB0ZWRBZElkPUExMDQxODQyM1VMNEhFMEVDTE1URiZ3aWRnZXROYW1lPXNwX2RldGFpbCZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=)

Use User-specific/demographic data

* Credit Checks
* Customer Loans
* Mortgage Risk Modeling
* Fraud Detection

in Investing

* Fundamental Alternative Data Analysis\(e.g. sentiment, reports and legal docs, satellite imagery\)
* Financial Data Analysis: signal mining and portfolio optimization, challenged by the signal to noise ratio is too low in financial time series than other domains of structured data
  * **Bayesian Methods **- rigorously handling uncertainty in predictions, \(due to the low signal to information ratio, it is imperative to quantify the uncertainty about the predictions. But Bayesian methods make it possible to not just provide point estimates,  but instead to estimate probability distributions that incorporate uncertainty about the chosen model\)
  * Deep Learning - automatic discovery of features\(combining with fundamental data\), such as conuting the number of super-tankes in a harbor on a satellite image
  * Reinforcement Learning - train a model to make a decision in uncertain environments to maximize long-term reward
  * Ensemble Methods: combine many weak learning algorithms, into one more model with higher accuracy
  * Kernel Methods: theoretically sound and robust algorithms, such as SVM, 

#### Bayesian Portfolio Optimization

* Online Optimization

#### Alternative Data Mining

---

## No Regret Learning in Portfolio Management

### Goal

* over T periods, allocate dynamic payoffs, payoff close to the best predictor in hindsight
  * "no regret" - \(best payoff - algo payoff\) grows sublinearly in T \(-&gt; 0 per period\)
  * per step regret diminish -&gt; not too far from optimal strategy

### Assumptions

* Have a set of N “signals” or “predictors”
  * price volume alpha, fundamental alpha, factors
  * Each trading period, each predictor receives an arbitrary payoff
  * not necessarily orthogonal
  * could have side information \(eg, expertise, specialization\)
* The payoff the signals are bounded
* No stochastic assumptions
  * returns of the signals could be uncorrelated with the past

### Findings

* tracking the best, not beating the best 
  * eg. boosting \(with i.i.d assumptions, stochastic assumptions\) to beat the best weak classifier
* Advantage
  * allocate weights based on different source of signals
* Disadvantage
  * multiplicative updates lead to portfolio concentration
  * Unable to add risk constraints - only additive loss functions work
    * negative results if ask for regret on risk-adjusted metrics: Sharpe ratio, mean-variance \(mu-sigma\)
    * volatility introduces switching costs
* Improvement and further work
  * combine no-regret with pursuit-evasion algorithms

### Tests

#### Models

* Multiplicative Weights Algo, Polynomial Weights Algo \(described in reference papers\)
  * Theoretical results guaranteed 
    * $$L_{PW}^T \leq L_{min}^T + 2\sqrt{T ln N}$$
    * penalty for too many to follow

#### High-frequency

* Data: simulated random walk data with U.S. equities parameters from paper
* Signal: Build signal with different level of information leak\(correlation\) to reveal information from price series
* Inventory risk contraint
  * restrict to portfolios with daily standard deviation PNL at most $X historically
* Benchmark: single signal strategies vs risk parity of 3, 5, 8 strategies
* Result: unable to deal with non-inventory weight constraints, significant improvement and fast convergence

#### Mid-frequency

* Data: U.S ETF \(Equity, Fixed Income Commod\) US index \(Dow Jones\) 2002-2014
* Benchmark: equal weight/risk parity portfolios for mid-frequency
* signal: return and Fama-French factor returns \(equities\) as signal
* Result: Sharpe from negative improvement to 0.4 improvement, the less the stocks the better

### Reference

| Paper | Author |
| :--- | :--- |
| Universal Porfolios | Thomas M. Cover, 1991 |
| The multiplicative Weights Update Method: A Meta-Algorithm and Its Applications | Arora, Hazan, Kale, 2012 |
| Learning, Regret Minimization and Equilibria | Blum and Mansour, 2007 |
| Pursuit-Evasion Without Regret, with Application to Trading | Dworkin, K. Nevmyvaka, 2014 |
| Regret to Best vs. Regret to the Average | Even-Dar, K.Mansour, Wortman 2007 |
| Risk-Sensitive Online Learning | Even-Dar, K, Wortman 2006 |

---

## Hierarchical Risk Parity

### Goal

In Asset allocation

* Markowitz's Curse
  * highly concentrated positions: the greater the correlation, the more need for diversification, however, correlation matrix eigen values decreasing faster as more correlated
* Singularity
  * require N\(N+1\)/2 observation to form NxN cov matrix

### Model

1. Tree Clustering 
   * Kernel and distance measure
   * cluster use distance of distance, single linkage
2. Quasi-Diagonalization use clusters
   * replace column with same group column, recursively
   * the matrix is sorted such that large values are at diagonal
3. Recursive bisection to allocate weights
   * bottom-up: define the variance of the group as inverse-variance allocated weights variance
   * top-down: split inverse to group variance then rescale

#### Result

* 10 to 100 simulated time-series
* Reduce variance by 42% \(relatively\) to Markowitz and 29% to Risk Parity in simulation results.

### Implementation

[Here](https://gmarti.gitlab.io/qfin/2018/10/02/hierarchical-risk-parity-part-1.html)

Extended Comparison [here](https://www.quantopian.com/posts/hierarchical-risk-parity-comparing-various-portfolio-diversification-techniques)

### Reference

* Building Diversified Portfolios that Outperform Out-of-Sample
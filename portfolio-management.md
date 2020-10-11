# Portfolio Management

- [Portfolio Management](#portfolio-management)
  - [Covariance Matrix Estimation](#covariance-matrix-estimation)
      - [Key Points](#key-points)
  - [Portfolio Optimization](#portfolio-optimization)

Basic Concepts

- [factor investing](https://en.wikipedia.org/wiki/Factor_investing)
- information ratio
  - Sharpe, [Treynor Ratio](https://www.investopedia.com/terms/t/treynorratio.asp), Sortino, T-Sharpe
- [Information Coefficient](https://www.investopedia.com/terms/i/information-coefficient.asp)
  - [Rule of Thumb](https://financemodelsrevisited.files.wordpress.com/2015/10/fc_rule_am_law2.pdf)
  - Fundamental Law of Active Management
  - Transfer Coefficient\(\-\)
  
## Covariance Matrix Estimation

- Estimating Covariance Matrices - Litterman, Winkelmann 1998
- A wel-conditioned estimator for large-dimensional covariance matrices Ledoit, Wolf 2001
- Evnonential weighting and random matrix theory based filtering of financial cOvariance matrices Pafka et al 20O4
- Seven sins in portfolio optimization - Schmelzer, Hause 2013
- 60 vears of portfolio optimization: practical challenges and current trends - Kolm et al 2014
- Cleaning Correlation Matrices - Bouchaud, Potters 2016

#### Key Points

- returns and volatility are two key components in portfolio construction, while return is not path dependent, volatility is
- exponential decay: overweighting more recent returns in estimation of volatilities and correlations allows portfolio reacts faster to market behavior
- observation periods: to reduce turnover and mitigate issues of observations at different times during the day, there is value in observing overlapping periods on a daily basis
- stability of correlations: the key consideration in risk management. several methods include
  - eigenvalue clipping \(keep larger eigenvalues only\)
  - matrix shrinkage: integrate prior estimate while increase stability of the covariance matrix

## Portfolio Optimization

- 60 years of portfolio optimization - Schemelzer, Hause 2013Ledoit, Wolf, 2001
- Seven Sins in Portfolio Optimization Schemelzer, Hause 2013
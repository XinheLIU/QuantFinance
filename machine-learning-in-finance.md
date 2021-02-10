# Applications of Machine Learning in Finance

- [Application of Machine Learning in Finance](#application-of-machine-learning-in-finance)
  - [Automation](#automation)
    - [Data mining and Learning from User or Company Data](#data-mining-and-learning-from-user-or-company-data)
      - [Fraud Detection](#fraud-detection)
      - [Credit Scoring](#credit-scoring)
  - [Information Processing](#information-processing)
    - [Learning from Limit-order book : Microstructure and High-frequency models](#learning-from-limit-order-book--microstructure-and-high-frequency-models)
    - [Learning from Alternative Data](#learning-from-alternative-data)
    - [Data Driven Decision Making](#data-driven-decision-making)
      - [Derivatives Pricing and Hedging Strategies](#derivatives-pricing-and-hedging-strategies)
    - [New Features and New Models: Detect Hiddne Patterns](#new-features-and-new-models-detect-hiddne-patterns)
      - [Alpha (Pricing Anomaly) Research](#alpha-pricing-anomaly-research)
      - [Portfolio Construction and Factor Investing](#portfolio-construction-and-factor-investing)
  - [Backtesting and Parameter Tuning](#backtesting-and-parameter-tuning)

Recommended Readings

- [Machine Learning for Factor Investing](http://www.mlfactor.com/)
- [Advances in Financial Machine Learning\(Course\)](http://www.quantresearch.org/Lectures.htm)
- [Advances in Financial Machine Learning](https://www.amazon.com/Advances-Financial-Machine-Learning-Marcos/dp/1119482089/ref=pd_bxgy_img_2/135-6445280-8934461?_encoding=UTF8&pd_rd_i=1119482089&pd_rd_r=fc9db682-7dce-4526-8ae8-4f973d4b466a&pd_rd_w=RaRsQ&pd_rd_wg=NDtW2&pf_rd_p=4e3f7fc3-00c8-46a6-a4db-8457e6319578&pf_rd_r=36KPG2961YA4J9M0NH0W&psc=1&refRID=36KPG2961YA4J9M0NH0W)
- [Machine Learning for Asset Managers \(Elements in Quantitative Finance\)](https://www.amazon.com/dp/1108792898/ref=sspa_dk_detail_0?psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEyVzBVS0E3TFlOOUNMJmVuY3J5cHRlZElkPUEwNDA0NjQyMjU3VkdKQlQ0OTI4QyZlbmNyeXB0ZWRBZElkPUExMDQxODQyM1VMNEhFMEVDTE1URiZ3aWRnZXROYW1lPXNwX2RldGFpbCZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=)
- Zuckerman, Gregory. 2019. The Man Who Solved the Market: How Jim Simons Launched the Quant Revolution. Penguin Random House.

## Automation

As in many other fields, the widest and most direct application of machine learning in the financial field is to do the things human can do well, which will significantly reduce cost and boost profit. In addition, with **Big Data** and other infrastructures, machines can boost the same work to the scale and accuracy human workers can hardly reach.

### Data mining and Learning from User or Company Data

Use User-specific/demographic data

- Credit Checks
- Customer Loans
- Mortgage Risk Modeling
- Fraud Detection

#### Fraud Detection

The large amount of labelled/unlabelled data enables powerful applications of data mining and other

Reading

- Ngai, Eric WT, Yong Hu, YH Wong, Yijun Chen, and Xin Sun. 2011. “The Application of Data Mining Techniques in Financial Fraud Detection: A Classification Framework and an Academic Review of Literature.” Decision Support Systems 50 (3): 559–69.
- Baesens, Bart, Veronique Van Vlasselaer, and Wouter Verbeke. 2015. Fraud Analytics Using Descriptive, Predictive, and Social Network Techniques: A Guide to Data Science for Fraud Detection. John Wiley & Sons.
- Bhattacharyya, Siddhartha, Sanjeev Jha, Kurian Tharakunnel, and J Christopher Westland. 2011. “Data Mining for Credit Card Fraud: A Comparative Study.” Decision Support Systems 50 (3): 602–13.
- Abbasi, Ahmed, Conan Albrecht, Anthony Vance, and James Hansen. 2012. “Metafraud: A Meta-Learning Framework for Detecting Financial Fraud.” MIS Quarterly, 1293–1327.

#### Credit Scoring

Use User-specific/demographic data

- Credit Checks
- Customer Loans
- Mortgage Risk Modeling
- Fraud Detection

- Wang, Gang, Jinxing Hao, Jian Ma, and Hongbing Jiang. 2011. “A Comparative Assessment of Ensemble Learning for Credit Scoring.” Expert Systems with Applications 38 (1): 223–30.
- Brown, Iain, and Christophe Mues. 2012. “An Experimental Comparison of Classification Algorithms for Imbalanced Credit Scoring Data Sets.” Expert Systems with Applications 39 (3): 3446–53.

## Information Processing

### Learning from Limit-order book : Microstructure and High-frequency models

With relatively rich data and high chance to profit from it ([Fundamental Law of Active Management](https://jpm.pm-research.com/content/15/3/30)). High-frequency trading firms have been the pinoneers (since 1960's) to use advanced machine learning and quantitative models, way before the popularity of AI and big data (since 2011.). Any small improvement on accuracy or cost means large profit per day.

Main applications include

- Reinforcement Learning
  - optimized execution strategy discovery
  - smart routing
- Predictive Learning
  - predict short-term market move
  - model non-linear relationships in volatility, volume, etc

Papers

- Kearns, Michael, and Yuriy Nevmyvaka. 2013. “[Machine Learning for Market Microstructure and High Frequency Trading](https://www.cis.upenn.edu/~mkearns/papers/KearnsNevmyvakaHFTRiskBooks.pdf).” High Frequency Trading: New Realities for Traders, Markets, and Regulators.
- Sirignano, Justin, and Rama Cont. 2019. “Universal Features of Price Formation in Financial Markets: Perspectives from Deep Learning.” Quantitative Finance 19 (9): 1449–59.

### Learning from Alternative Data

The most state-of-the-art application of big data and machine learning in the financial area.

Most financial data is non-numeric or unstructured: categorical, text, images, recordings, etc.

Financial datasets tend to be high-dimensional, with many variables and few observations

Alternative data include

- textual data from social media
  - eg. positive comment - negative comment = sentiment imbalance
- satellite imagery
- credit card logs (to predict sales)
- earning reports (financial statements)

These new information brings potential alpha or lower transaction cost for financial investing. A large part of these applications leverages **Natural Language Processing (NLP)** techniques

Papers

- Blank, Herbert, Richard Davis, and Shannon Greene. 2019. “Using Alternative Research Data in Real-World Portfolios.” Journal of Investing 28 (4): 95–103.
- Jha, Vinesh. 2019. “Implementing Alternative Data in an Investment Process.” In Big Data and Machine Learning in Quantitative Investment, 51–74. Wiley.
- Ke, Zheng Tracy, Bryan T Kelly, and Dacheng Xiu. 2019. “Predicting Returns with Text Data.” SSRN Working Paper 3388293.

Surveys on NLP

- Loughran, Tim, and Bill McDonald. 2016. “Textual Analysis in Accounting and Finance: A Survey.” Journal of Accounting Research 54 (4): 1187–1230
- Cong, Lin William, Tengyuan Liang, and Xiao Zhang. 2019a. “Analyzing Textual Information at Scale.” SSRN Working Paper 3449822.
- Cong, Lin William, Tengyuan Liang, and Xiao Zhang. 2019b. “Textual Factors: A Scalable, Interpretable, and Data-Driven Approach to Analyzing Unstructured Information.” SSRN Working Paper 3307057.
- Gentzkow, Matthew, Bryan Kelly, and Matt Taddy. 2019. “Text as Data.” Journal of Economic Literature 57 (3): 535–74.

### Data Driven Decision Making

Some examples

#### Derivatives Pricing and Hedging Strategies

### New Features and New Models: Detect Hiddne Patterns

This is also an attracting applications all hedge funds are trying to explore. Combining machine learning techniques and traditional models (economics, financial math, econometrics) in finding pricing anomalies (alpha) or overcome drawbacks of traditional models. For these applications, some notice points are

- financial data are extramely noisy comparing to many other machine learning set ups.
  - People often use signal extraction techniques to gather information and denoise the data. However, No-arbitrage suggests there is no determinstic and persistent patterns should exist for a long term.
  - Feature engineering and data mining are heavily used, data can be more important than the model choices
  - Also due to noise, information leak and outside information impact, cross-validation on financial time-series are more challenging and delicate comparing to other time-series data
- Causality is the key and a challenge in financial machine learning
  - simple correlations have weaker indication in financial settings comparing to many others
- Economic or econometric framing matters a lot. Assumptions and choices made on variables can be decisive ([No-free lunch Theorem](https://en.wikipedia.org/wiki/No_free_lunch_theorem))

Some application examples include

- Financial Data Analysis: signal mining and portfolio optimization, challenged by the signal to noise ratio is too low in financial time series than other domains of structured data
  - **Bayesian Methods** rigorously handling uncertainty in predictions, \(due to the low signal to information ratio, it is imperative to quantify the uncertainty about the predictions. But Bayesian methods make it possible to not just provide point estimates,  but instead to estimate probability distributions that incorporate uncertainty about the chosen model\)
  - Deep Learning: automatic discovery of features\(combining with fundamental data\), such as conuting the number of super-tankes in a harbor on a satellite image
  - Reinforcement Learning - train a model to make a decision in uncertain environments to maximize long-term reward
  - Ensemble Methods: combine many weak learning algorithms, into one more model with higher accuracy
  - Kernel Methods: theoretically sound and robust algorithms, such as SVM, 

#### Alpha (Pricing Anomaly) Research

- Bansal, Ravi, David A Hsieh, and S Viswanathan. 1993. “A New Approach to International Arbitrage Pricing.” Journal of Finance 48 (5): 1719–47.
- Bansal, Ravi, and Salim Viswanathan. 1993. “No Arbitrage and Arbitrage Pricing: A New Approach.” Journal of Finance 48 (4): 1231–62.
- Braun, Helmut, and John S Chandler. 1987. “Predicting Stock Market Behavior Through Rule Induction: An Application of the Learning-from-Example Approach.” Decision Sciences 18 (3): 415–29.
- Freeman, Robert N, and Senyo Y Tse. 1992. “A Nonlinear Model of Security Price Responses to Unexpected Earnings.” Journal of Accounting Research, 185–209.
- White, Halbert. 1988. “Economic Prediction Using Neural Networks: The Case of Ibm Daily Stock Returns.”

#### Portfolio Construction and Factor Investing

## Backtesting and Parameter Tuning

The earliest and probably widest application would be the indirect application of machine learning methods, such as model training, model selection and cross-validation methods. These methods can be used on traditional quantitative financial models for improvements and expansion to online learning/big data application settings.

Machine Learning has tremendous advantages over econometrics in a sense of testing econometric strategies

- Econometric models generally
  - rely on p-values, or so-called “statistical significance,” in violation of ASA protocols
  - are designed to adjudicate variance in-sample (not forecast values out-of-sample)
  - rely on strong assumptions that are not satisfied by financial phenomena
  - do not disentangle the specification search from the variable search
  - pay little or no attention to both forms of overfitting: training set and testing set
- While Machine Learning
  - usually use Out-of-Sample performance as the most important criteria, pay less attention to assumptions and frameworks


Readings

- Arnott, Rob, Campbell R Harvey, and Harry Markowitz. 2019. “A Backtesting Protocol in the Era of Machine Learning.” Journal of Financial Data Science 1 (1): 64–74.
- Wolpert, David H. 1992a. “On the Connection Between in-Sample Testing and Generalization Error.” Complex Systems 6 (1): 47.
- https://amstat.tandfonline.com/doi/pdf/10.1080/00031305.2016.1154108?needAccess=true&

## Chellenges Not Solved by Machine Learning


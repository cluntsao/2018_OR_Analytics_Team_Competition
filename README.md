# 2018_OR_Analytics_Team_Competition

Problem Statement excerpted from the official

Background :

Portfolio optimization refers to the process of finding the optimal proportion of each asset in an investor’s portfolio, given a particular investment objective. The two main criteria are to maximize return for a given level of risk or, equivalently, to minimize risk for a given level of expected return. In order to control risk efficiently an investor will try to construct a portfolio that is well diversified.

Institutional investors are generally required to construct portfolios using additional constraints such as, limits on the number of unique assets in the portfolio or how many assets outside a specified benchmark can or must be added. These additional constraints are designed to control the costs that occur when an asset is bought, sold or held while also creating a portfolio that is concentrated enough to outperform the market.

Principal Global Investors has a large base of asset under management, mainly from our pension and insurance business as well from institutional clients. In order to operate profitably these assets get invested in a wide range of asset classes and strategies. One of those asset classes is equities, where portfolio construction is the main point of focus. The following problem is an accurate representation of what challenges an equity portfolio manager faces on a daily basis. 

Problem Definition : 

Your challenge is to develop an equity portfolio optimization framework that improves risk adjusted excess returns. The optimization framework will minimize the trade-off between risk, in the form of tracking error, and expected excess return through time, subject to several constraints. The portfolio will only consist of long positions, meaning the decision variable (proportion of the portfolio held in each asset) is always positive. The portfolio must also be fully invested at all times. In other words, the proportions of all assets must sum to 100%. In order to avoid concentration in individual assets, we will limit the proportion that can be held in each individual asset. To ensure diversification, there will be constraints on sectors, company sizes (market capitalization), and sensitivity to the equity market (Beta). So far, this represents a basic Markowitz portfolio optimization problem that can be solved using widely open-source or commercial quadratic programming solvers. This Markowitz implementation was also used to create the baseline data that is provided and should serve as a starting point to further add the following extensions to the problem. 

As mentioned before, the number of distinct assets in a portfolio is often a requirement in portfolio construction. Therefore, we would like you to add a constraint to limit the target number of distinct assets in the portfolio to a predefined range. We will also introduce an active share constraint which controls how closely we follow a chosen benchmark index in terms of active weights (equation 1, difference between portfolio weight and benchmark weight), as well as a tracking error (standard deviation of active weights) constraint which also controls how closely we follow a benchmark, but in terms of a risk measure rather than return. These final three extensions to the Markowitz problem alter the problem definition considerably. This formulation can no longer be solved with traditional convex optimization techniques. We therefore challenge you to come up with a creative solution for handling these constraints. You must consider the dimensionality of the preoblem and the associated time it will require to compute a solution. Think about applying heuristics rather than exact implementations as a trade-off for the time it will take to compute a solution.  We also want you to think about scalability of the problem, i.e. what would happen if your input data increased dramatically in size, e.g. 10-20x? This would typically happen if we want to run this problem on a global equity universe.

Datasets : 

Data provided is an extract of the constituents of the S&P500 at pre-specified dates. The data extract is taken every 4 weeks over a 10-year horizon, starting 2007-Jan-03. The number of data points per date will vary slightly.

Time series data includes the following fields:
 -  Date
 -  Identifier (SEDOL (Stock Exchange Daily Official List))
 -  Sector
 -  Beta
 -  Alpha Score
 -	Name
 -  Benchmark (S&P 500) weight 
 -  Market cap quintile
 
 Historical risk model data (upper half of the covariance matrix) used for optimization done on the corresponding date. 
 
 Historical returns for each 4 week period in the 10-year horizon for each stock, in percentage, e.g. 0.05 = 5% (part of the evaluation criteria, see section 7. Included in the results template)

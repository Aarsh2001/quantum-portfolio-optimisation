## What is the mean variance portfolio optimization problem?
In 1952, Markovitz proposed a novel portfolio theory that exploits diversification to engineer a portfolio with higher returns for lower risk, going against conventional beliefs that risk has a positive linear relationship to reward. Mean variance portfolio optimization is a portfolio analysis technique that was born from Markovitz's work. What Markovitz added to the game was the consideration of variance and covariance between individual stocks. The idea is to maximize return by combining assets that are anti-correlated, thus resulting in a lower volatility for the portfolio. 

This is not to say that we want our assets to be in direct opposition with each other (in that case we would never see any gains), but to be anti-correlated enough so that it cancels out the noise in the short term while being positively correlated in the long term such that they both go up. The plot below shows the relationship between risk and returns. The efficient frontier is the optimized portfolio which occupies the "efficient" parts of the risk–return spectrum. This is the portfolio which satisfies the condition that no other portfolio exists with a higher expected return but with the same standard deviation of return.

![](./images/minimum_variance_frontier.jpg)

The mean-variance portfolio optimization problem is a NP-Hard COP, making it computationally expensive for current classical computers to solve. Mathematically, we can represent this quadratic problem for n assets as:  
![](./images/Minimum_variance_problem.png)

where the following notation is used:
![](./images/Minimum_variance_problem_notation.png)

For our implementation, we simplified the conditions such that all of the budget must be spent and normalized all equity values to 1. 

Our equality constraint ![](./images/equality_constraint.png) states that the number of ones in our binary decision variable vector must be equal to the budget (we spend everything). We create a penalty term based upon this constraint ![](./images/penalty_term.png) which is scaled by a parameter and subtracted from the objective function. We map the resulting problem into a Hamiltonian whose ground state corresponds to the optimal solution for the mean-variance portfolio problem. This notebook implements the Variational Quantum Eigensolver (VQE) and the Quantum Approximate Optimization Algorithm (QAOA) to find the optimal solution for a given set of equities. We extend upon this by backtesting each approach against three random stock portfolios from the S&P 500. 
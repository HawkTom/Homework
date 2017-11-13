-  **Consider a logistic regression with two classes**

- **Having a classifier G,  the probabilities are in the case ofen assumed to take form**
  $$
  P(G(x)=0|x, \beta) = p^0(x, \beta) = \frac{exp(\beta^Tx)}{1+exp(\beta^Tx)}  \\
  P(G(x)=1|x, \beta) = p^1(x, \beta) = \frac{1}{1+exp(\beta^Tx)}
  $$

- **Having labels $y_i\in\{0,1\}$, the goal is to maximize the log-likelihood** 

- $$
  l(\beta) = \sum(y_ilog\ p^0(x_i, \beta)+ (1-y_i)log\ p^1(x_i, \beta))
  $$

  **writing respect to $\beta$**

  ​

  **1. Explain the resoning behind maximizing the objective**

  *Sol:*  

  ​	The objective function is the log-likelihood. Because of the monotone increasing of log function, the log-likelihood fucntion will not change the properties of likelihood function. 

  ​	And we maxmimize the likelihood because we maximize fit of our model to data under an implicit assumption that the observed data are at the same time most  likely data.

  **2. Determine whether the objective is concave(since we maximize, we are interested in concavity, not convexity. It is just a multiplication by -1)**

  *Sol:*  

  **3. What does it mean for (the potential) uniqueness of the problem?**

  *Sol:*  fuck
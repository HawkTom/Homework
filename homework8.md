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

  *Sol:*  The likelihood function is concave.[http://web.engr.oregonstate.edu/~xfern/classes/cs534/notes/logistic-regression-note.pdf]

  **3. What does it mean for (the potential) uniqueness of the problem?**

  *Sol:*  The existence, finiteness, and uniqueness of maximum likelihood estimates  for the logistic regression model depend on the patterns of data points in the observaation space. The maximum likelihood estimation for logistic regression can break down when training on linearly separable data. This means that maximum likelihood eatimation will select parameter values of infinite magnitude,  and wil allow for many different possible parameter values. [https://www.cs.ubc.ca/~arnaud/cs340/HW5_q2.pdf]
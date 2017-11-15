### AAI Homework 

---

Student ID: 11749248 

Name: TongHao  

---

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

  ​	And we maximize the likelihood because we maximize fit of our model to data under an implicit assumption that the observed data are at the same time most  likely data.

  **2. Determine whether the objective is concave(since we maximize, we are interested in concavity, not convexity. It is just a multiplication by -1)**

  *Sol:*  
  $$
  L_i(w) = log(x_i, w)^{y_i}(1-g(x_i, w))^{1-y_i} = y_ilog\ g(x_i, w)  + (1-y_i)log(1-g(x_i, w)) 
  $$
  where $g(x, w) = \frac{1}{1+e^{-w^Tx}}$

  Taking gradient of $L_i$ with respect to w, we have
  $$
  \begin{align}
  \bigtriangledown _\textbf wL_i &=\frac{y_i}{g(\textbf x_i,\textbf w)}\bigtriangledown _\textbf wg-\frac{1--y_i}{1-g(\textbf x_i, \textbf w)}\bigtriangledown _\textbf wg\\
  & = \frac{y_i}{g}g(1-g)\textbf x_i - \frac{1-y_i}{1-g}g(1-g)\textbf x_i\\
  & = (y_i(1-g)-(1-y_i)g)\textbf x_i \\
  & = (y_i - y_ig-g+y_ig)\textbf x_i \\
  & = (y_i-g(\textbf x_i, \textbf w))\textbf x_i
  \end{align}
  $$
  Consider all training examples, we have:
  $$
  \bigtriangledown_\textbf wL = \sum_{i=1}^{N}(y_i-g(\textbf x_i,\textbf w))\textbf x_i
  $$
  The likelihood function is **concave**.

  *reference*:  http://web.engr.oregonstate.edu/~xfern/classes/cs534/notes/logistic-regression-note.pdf
  *refernece*:  https://homes.cs.washington.edu/~marcotcr/blog/concavity/

  **3. What does it mean for (the potential) uniqueness of the problem?**

  *Sol:* 

  The existence, finiteness, and uniqueness of maximum likelihood estimates  for the logistic regression model depend on the patterns of data points in the observation space. The maximum likelihood estimation for logistic regression can break down when training on linearly separable data. This means that maximum likelihood estimation will select parameter values of infinite magnitude,  and will allow for many different possible parameter values. 

  reference: https://support.sas.com/documentation/cdl/en/statug/63347/HTML/default/viewer.htm#statug_logistic_sect035.htm

  reference : https://www.cs.ubc.ca/~arnaud/cs340/HW5_q2.pdf

  ​

  **Attention: answer only represent my own idea, but not the true answer. **

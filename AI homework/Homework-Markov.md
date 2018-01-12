### AAI-Homework

---

**(1) Discuss the similarities and differences between supervised learning, reinforcement earning and unsupervised learning.**

*Sol* 

**Similarities**

1) Three learning algorithms are all based on data. 

2) Three algorithms' intent are all train models and then use models to predict results or actions.


**Difference**

- Supervised learning
  1) A human builds a classifier based on **input and output data**
  2) That classifier is trained with a training set of data
  3) That classifier is tested with a test set of data
  4) Deployment if the output is satisfactory


- Unsupervised learning
  1) A human builds an algorithm based on **input data**
  2) That algorithm is tested with a test set of data (in which the algorithm creates the classifier)
  3) Deployment if the classifier is satisfactory


- Reinforcement learning
  1) A human builds an algorithm based on **input data**
  2) That algorithm presents a state dependent on the input data in which a user **rewards or punishes** the algorithm via the action the algorithm took, this continues over time
  3) That algorithm learns from the reward/punishment and updates itself, this continues
  4) It's always in production, it needs to learn real data to be able to present actions from states



*problem 2 is in the back*

<div style="page-break-before: always;"> </div>

**(2) What does a Bellman equation describe in MDPs?**

*Sol*  

With a complete knowledge of system, that includes a prefect knowledge of state the agent is in as well as the transition probability and reward function, it is possible to estimate the value function for each policy $\pi$ from self-consistent equation.

So, for a specify policy, we could use Bellman equation to estimate its value function.  The equations depends on specific policy. 

In the environment with N states, the Bellman equation is a set of N linear equations, one for each state, with N unknowns which are the expected value for each state.  

By deriving a version of Bellman's equation for the optimal value function itself, we can get a good approximation of the optimal value function and calculates a optimal policy that agents will achieve a good performance.  
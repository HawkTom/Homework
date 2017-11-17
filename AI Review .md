### what is AI

- Thinking humanly
- Thinking Rationally
- Acting Humanly:  Turing test.  A computer passes the test of intelligence. if it can fool a human interrogator
- Acting Rationally

### Basic Search

- Problem Formulation

  - States: all reachable states from the initial state by any sequence of actions
  - Initial state: the state where the problem starts
  - Actions: legal actions on state
  - Next state: a description of what each actions does, Result(s, a)
  - Goal test: determine whether a given state is a goal state.
  - Path cost: function that assigns a numeric cost to each other.

- Search Methods: Performance Metrics

  - Completeness: Does it always find a solution if it exists
  - Optimality: Does it always find the least-cost solution
  - Time complexity: # nodes generated / expanded
  - maximum #nodes in memory

- Uniformed Search Methods

  - BFS: Breadth-first search

    - Costs in the search tree is same


    - Expand the shallowest unexpanded node

  - UCS: Uniform-cost search

    - Expand the cheapest unexpected node
    - the costs in the search tree may be different 

  - DFS: Depth-first search

    - expand the deepest unexpanded node
    - not complete, not optimal 

  - DLS: Depth-limited search

    - nodes at depth $l$ have no successors
    - Limit $l$ is defined based on domain knowledge

  - IDS: Iterative deepening search(IDS)

    - Apply DLS with increasing limits

  - Bidirectional search

    - search from forward and backward directions simultaneously 

### Heuristic Search

> Basic search:  use no domain knowledge
>
> Heuristic Search: use domain knowledge

Heuristic function $h(n)$ estimates the cheapest cost from $n$ to Goal

- (1)  $h(n) = 0$ if $n$ is the goal node
- (2) nonnegative
- (3)problem-specific

A 'good' heuristic can be powerful only it is a 'good' quality. It should be **admissible**

***admissible:*** never overestimates the cheapest cost from $n$ to goal

### Heuristic Search Methods

- Greedy Best-first Search: 
  - expand the node that seems closest to the Goal
  - expand node $n$ that has the minimal $f(n) = h(n)$
  - It is not complete, can stuck in loops.  And it is not optimal.
- A*  Search:
  - expand node $n$ has the minimal $f(n) = h(n) + g(n)$
  - It is complete. And it is optimal. 
  - **the prove of optimality if A***

### Optimization

- Unconstrained Optimization

  - Steepest descent
    - Iterative algorithm: $x^{k+1} = x^k - \alpha^{k}\bigtriangledown f(x^k)$
    - Step size $\alpha^k$ is important:  high -> jumping ; low-> little progress
    - **step size selection ???**
  - Zig-zagging
    - why?
  - Newton's method
    - Newton's method to solve the formula
    - $x^{k+1} = x^k - (\bigtriangledown ^2f(x^k))^{-1}\bigtriangledown f(x^k)$  

  > Steepest descent: the most basic method,  used very often,  needs $\bigtriangledown f(x) \in \mathbb R^{n}$
  >
  > Newton Method: Extremely fast convergence ($x^*$ is the optimal),  needs second-order derivate $\bigtriangledown ^2f(x)\in \mathbb R^{n*m}$ 

- Constrained Optimization

  - consider them directly (projected gradients)

    - first steepest descent 
    - second keeps feasibility

  - Lagrangian duality 

  - KKT conditions

    - $$
      minimize \ \ f(x) \\
      subject \ \ to \ \ \ 
      \left\{\begin{matrix}
      g_i(x)\leq0, i=1,...,I 
      &\\ h_j(x) = 0, j=1, ...J 
      \end{matrix}\right.
      $$

    - Define the Lagrangian function $ L(x;\lambda, \mu) = f(x) +\lambda^Tg(x) + \mu^Th(x)$

    - conditions 

    - $$
      \left\{\begin{matrix}
      \lambda_jg_j(x) = 0\\
      h_i(x) = 0 \\
      g_j(x) \leq 0 \\
      \beta_j \geq 0
      \end{matrix}\right.
      $$

    - SQP method (sequential quadratic programming)

### Optimization without derivatives

- Bisection method: $if\ F(a)F(b) < 0, then\ a\ solution\ exists$
- Golden -section search 
- Nelder-Mead method
- Simulated annealing 
- Evolutionary algorithm

### Machine Learning

- > Under-fitting:  high training error and high test error
  >
  > - deal:  set a more complex model
  >
  > Over-fitting: low training error and high test error
  >
  > - set a less complex model
  > - regularization: penalize certain parts of the parameter space
  > - get more data

- Linear Model

- Tree Model

- Neural Networks

- K nearest neighbour

- Support Vector Machine 

### Theory of Learning


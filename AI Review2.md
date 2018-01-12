_By Hawk_   _2018-1-12_

### Feature Engineering

- `Features and Feature Engineering`

  - **Features**:  information that describes a problem at hand and is potentially useful for prediction/problem solving
  - **Feature Engineering**: design and process for AI applications
  - Process:  
    - understanding the properties of the task and how they may interact with the strengths and limitations of the chosen model
    - design a set of features
    - run experiments and analyse the results on a validation dataset
    - change the feature set
    - go to step 2

- `Feature Explosion`

  - Initial features: an expression of prior knowledge 
  - Features combinations 
  - Problem:  Storage Cost;  Irrelevant, Redundant or even harmful features; Large number of required training samples; Dysfunctional distance functions
  - Benefits of small features set 

- `Tackling Feature Explosion`

  - Feature selection:  greedy method

    - Reduce the original feature by throwing out some redundant features

    - Greedy heuristic search for feature selection (**sequential feature selection**)

      - **Forward selection**: add one feature each step
      - **Backward selection**: remove one feature each step
      - **Evaluate method**: information theory; prediction accuracy
      - **Stop criterion** 

    - Three typical methods:

      - Wrapper methods <img src="https://upload.wikimedia.org/wikipedia/commons/0/04/Feature_selection_Wrapper_Method.png">

        highly accurate, computationally expensive, risk of over fitting

      - Filter methods<img src="https://www.researchgate.net/profile/Davide_Roverso/publication/272784254/figure/fig1/AS:294779976994816@1447292431226/Figure-1-Filter-method-for-feature-selection-the-features-are-filtered-independently-of.png">

        fast and simple; not as accurate as wrappers

        Examples:  correlation-based filters (**Pearson correlation**, **Information gain**)

      - Embedded method<img src="https://upload.wikimedia.org/wikipedia/commons/0/04/Feature_selection_Wrapper_Method.png">

        similar to wrappers but less computationally expensive; less possible to over fitting

        Example: classification and regression trees

  - Regularization: (introducing penalty for complexity -> reduce features)

    - Ridge regression (2-order)
    - Lasso regression (1-order)

### Unsupervised Learning

1. `What is clustering`

   - group the points into some number of clusters

   - members of a cluster are close /similar to each other

   - members if different clusters are dissimilar

   - It is hard for clustering high dimension data.

   - Distance measurements:

     - Cosine similarity  and distance   <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/1e1fccd8f6d7c2acccde3c9426a795c4b9570c27">

         $D_C(A， B) = 1-S_C(A，B)$     or     $distance = \frac{cos^{-1}(similarity)}{\pi}$

     - Jaccard similarity and distance (Two sets A and B)

       ​			     		 <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/eaef5aa86949f49e7dc6b9c8c3dd8b233332c9e7">  $0\leq J(A, B) \leq 1$

       <img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/3d17a48a5fb6cea57b076200de6edbccbc1c38f9">

     - Euclidean distance


2. `Hierarchical clustering`   (**Repeatedly combine** , **two nearest clusters**)

   - represent a cluster of mangy points:  **centroid ( average of its points)**
   - how to determine "nearness" of clusters: **distance of centroids** (and other criterion)
   - when to stop. number criterion, distance criterion
   - Additionally,  __in the non-Euclidean space__   

3. `k-means clustering`  (scan quickly)

4. `The BFR algorithm`  ==Extension of  k-means to large data==

   - assumes that clusters are normally distributed a centroid in an Euclidean space

   ```
   Select initial k centroids by some approach:
   	1. random selection
   	2. samll random sample and cluster optimally
   	3. take sample one by one, each as far from the previously slected points as possible
   ```

   - 3 set of points which we keep track of

     - Discard set (DS): points close enough to a centroid to be summarized

     - Compression set (CS):  group of points are close together but not close to any existing centroid

     - Retained set (RS): isolated points waiting to be assigned to a compression set

       <img src="https://image.slidesharecdn.com/javoenihrfu3oauzriou-signature-f43061a7db8d94aa9e293b85d96a2faeff7cf3535bbf93f2b2ff71999b5d49ab-poli-160324134237/95/clusteryanam-79-638.jpg?cb=1458828249">

   - Summarizing sets of points

     - the number of points: N
     - the vector SUM:  $SUM_i = i^{th}$ component of SUM
     - the vector SUMSQ:   $SUMSQ_i = $ sum of squares of $i^{th}$ component
     - represent cluster: $(d, SUM_i, (SUMSQ_i/N)-(SUM_i/N)^2$

   - Actual clustering

   ```
   1. Find those points that are “sufficiently close” to a cluster centroid and add those points to that cluster and the DS
   2. Use any main-memory clustering algorithm to cluster the remaining points and the old RS
   3. DS set: Adjust statistics of the clusters to account for the new points (Ns,SUMs,SUMSQs)
   4. Consider merging compressed sets in the CS
   5. If this is the last round, merge all compressed sets in the CS and all RS points into their nearest cluster
   ```

   ​	__Mahalanobis Distance to decide whether to put a new point into a cluster (and discard)__

   ​	__Combine 2 CS sub-clusters if the combined variance is below some threshold. __

5. `The CURE algorithm`

   ```
   0. Pick a random sample of points that fit in main memory
   1. Clustering: group nearest points/clusters
   2. Pick representative points:
   	For each cluster, pick a sample of points, as dispersed as possible
   	From the sample, pick representatives by moving them (say) 20% toward the centroid of 		the cluster
   3. Now, rescan the whole dataset and visit each point p in the data set
   4. Find the closest representative to p and assign it to representative’s cluster
   ```

6. `Spectral clustering`


### Markov Decision Process

1. `Basic concepts`

   <img src="https://i.stack.imgur.com/eoeSq.png">

   - receive current state state $S_t$ and reward $R_t$ from the environment
   - Take action $A_t$
   - Environment changes to $S_{t+1}$ and $R_{t+1}$ 
   - __Objective of interaction__ : maximise total reward
   - __Objective if learning__: find out such actions from the information collected during interaction
   - Learn a ==policy== (a mapping from states to actions)
   - $A_t$ affects $S_{t+1}, S_{t+2}, S_{t+3},...$ and $R_t+1, R_{t+2},R_{t+3},...$ all $R_{t+k}$ contribute to the cumulative reward starting from time t.
   - Reinforcement Learning vs Supervised Learning
     - RL: learn a policy;  SL: learn a classifier
     - No teachers in RL; Feedbacks in SL is instant
     - ...

2. `Markov decision process`

   - __MDP: M=\<S, A, P, R\>__   S: set of all possible states; A: set of all possible actions

   - $\mathbb{P}(S_{t+1}|S_1, ..., S_t, A_1,...,A_t) = \mathbb{P}(S_{t+1}|S_t, A_t)$  the future only correlate with present state

   - P: transition probability  $p(s, a, s^{'}) = \mathbb{P}(S_{t+1} = s^{'}|S_t=s, A_t=a)$

   - R: immediate reward function;  R: S->R;  R: S\*A -> R; R: S\*A\*S -> R

   - __Policy__:  describe the behaviour of agent  

     - Deterministic policy  (Discrete): ($\pi(s) = a$: instructs the agent to take action a at state s )
     - Stochastic policy (Continue):  $\pi$ is a conditional distribution over actions given states

   - __Cumulative reward__

     - total amount of reward rather than just a single-step
     - discounted cumulative reward:  $G_t = R_{t+1} + \gamma R_{t+2} + ... = \sum_{k=1}^{\infty}\gamma ^{k-1}R_{t+k}$
     - $\gamma \in (0, 1)$  $\gamma \rightarrow1 $  far-sighted;   $\gamma \rightarrow 0$ myopic
     - $G_t = R_{t+1} + \gamma G_{t+1}$

   - __Value functions__ (maximise expected cumulative reward)

     - state Value functions (==$v^\pi$==):  $v^{\pi}(s):= E[G_t | \pi, S_t = s] $
     - action Value functions (==$q^{\pi}$==): $q^{\pi}(s, a) := E[G_t|\pi, S_t = s, A_t = a]$

   - __Bellman equation__

     - for state value function:   
       $$
       \begin{align}
       v^{\pi} &= E[G_t | \pi, S_t = s] \\
       & = E[R_{t+1} + \gamma G_{t+1}|\pi, S_t = s]\\
       & = E[R_{t+1} + \gamma v^{\pi}(S_{t+1}) | \pi, S_t = s]
       \end{align}
       $$
       since the transition probability is $p(s, \pi(s) , s^{'})​$ 
       $$
       v^{\pi}(s) = \sum_{s^{'}\in S} p(s, \pi(s), s^{'})(R(s, \pi(s), s^{'}) + \gamma v^{\pi}(s^{'}))
       $$
       for stochastic $\pi(a|s)$
       $$
       v^{\pi}(s) =\sum_{a\in A} \pi (a|s) \sum_{s^{'}\in S} p(s, \pi(s), s^{'})(R(s, \pi(s), s^{'}) + \gamma v^{\pi}(s^{'}))
       $$

     - for action value function:
       $$
       \begin{align}
       q^{\pi}(s,a ) &= E[G_t | \pi, S_t = s, A_t = a] \\
       & = E[R_{t+1} + \gamma G_{t+1}|\pi, S_t = s,  A_t = a]\\
       & = E[R_{t+1} + \gamma v^{\pi}(S_{t+1}) | \pi, S_t = s,  A_t = a]
       \end{align}
       $$
       since action at the current step is always $a$ regardless of $\pi $ in $q^\pi(s, a)$
       $$
       q^{\pi}(s, a) = \sum_{s^{'}\in S} p(s, a, s^{'})(R(s, a, s^{'}) + \gamma v^{\pi}(s^{'}))
       $$
       compare 
       $$
       \left\{\begin{matrix}
       v^{\pi}(s) =\sum_{a\in A} \pi (a|s) \sum_{s^{'}\in S} p(s, \pi(s), s^{'})(R(s, \pi(s), s^{'}) + \gamma v^{\pi}(s^{'}))\\ 
       q^{\pi}(s, a) = \sum_{s^{'}\in S} p(s, a, s^{'})(R(s, a, s^{'}) + \gamma v^{\pi}(s^{'}))
       \end{matrix}\right.
       $$
       we have
       $$
       v^\pi (s) = \sum_{a\in A} \pi(a|s)q^\pi(s,a)
       $$
       thus, 
       $$
       \begin{align}
       q^{\pi}(s, a) &= \sum_{s^{'}\in S} p(s, a, s^{'})(R(s, a, s^{'}) + \gamma v^{\pi}(s^{'})) \\
       & =  \sum_{s^{'}\in S} p(s, a, s^{'})(R(s, a, s^{'}) + \gamma \sum_{a^{'}\in A} \pi(a^{'}|s^{'})q^\pi(s^{'},a^{'}))) \\ 
       & =  \sum_{s^{'}\in S} p(s, a, s^{'})(R(s, a, s^{'}) + \gamma q^\pi (s^{'}, \pi(s^{'}))) 
       \end{align}
       $$

3. `Planning in MDPs`

   - Optimality
     - optimal state value function: $v^*(s) = max_\pi v ^\pi (s)$
     - optimal action value function: $q^*(s, a) = max_\pi q ^\pi (s, a)$
     - __optimal policy have the highest expected cumulative reward at any state__

   - ==Solve Bellman equation==

     - Policy iteration algorithm

       ![PI.png](img\PI.png)

     - Value iteration algorithm

       ![VI.png](img\VI.png)

4. `Extensions to MDPs`

   - POMDPs:  _\<S, A, O, P ,R, W\>_  O: set of all observations; W:  an observation probability function 
   - continue MDPs
   - Semi-MDPs
   - Decentralised POMDPs

### Reinforcement Learning

_what if the agent does not have such full knowledge_

1. `Model-based RL` (Estimate during interaction)

   - $\hat M := <\hat S, \hat A, \hat P, \hat R >$
     - $\hat S, \hat A$ set of all **visited** states and actions
     - $\hat R$: estimated transition probabilities
       - $\hat R(s, a, s^{'}) = {R_{s, a,s^{'}}}/{N_{s, a,s^{'}}}$
       - $R_{s, a,s^{'}}$ be the sum of rewards received at transition _(s, a, s')_ in the whole interaction history
       - $N_{s, a,s^{'}}$ be the number of transition _(s, a, s')_occurred
     - $\hat P$: estimated immediate rewards 
       - $\hat P(s, a, s^{'}) = {N_{s, a,s^{'}}}/{N_{s, a}}$
       - $N_{s, a}$ be the number of ‘taking action _a_ at state _s'_ in the whole interaction history
       - $N_{s, a,s^{'}}$ be the number of transition _(s, a, s')_ occurred
   - ![model_based_RL.png](img\model_based_RL.png)
   - ​

2.  `Exploration vs exploitation in RL`     ==**trade off**==

   - Exploration:  deliberately take actions that are not (seemingly) “optimal” according to the current knowledge
     - $\varepsilon$-greedy:  choose  a random action with probability $\varepsilon$ ; choose the 'optimal' action with $1-\varepsilon$
     - $\varepsilon$ often set small values like 0.03, 0.01, 0.003 or even smaller
     - R-MAX: Assume $q(s, a)$=$R_{max}$ <maximum immediate reward of that MDP>,  unless _a_  has been taken at least _m_ times at _s_
     - R-MAX forces the agent to try every possible actions many times before making any conclusion
   - Exploitation: gain more information in the hope of discovering better policies

3. ` Model-free RL`

   - Monte-Carlo methods

     - Monte-Carlo value estimation:
       $$
       N(s) \leftarrow N(s) +1 \\
       \hat G (s) \leftarrow \hat G(s)+G_t \\
       \hat v^\pi(s) \leftarrow \hat G(s) /N(s)
       $$
       $G_t$ is the actual cumulative reward $G_t = R_{t+1}+ \gamma R{t+2} + \dots + \gamma^k R_{t+k+1} +\dots $

     - MC reinforcement learning

       ![MC_RL.png](img\MC_RL.png)

       Incremental version of MC estimation
       $$
       \hat v^\pi(S_t) \leftarrow \hat v^\pi(S_t) + \frac{1}{N(S_t)} (G_t - \hat v^\pi(S_t)) \\
       \hat v^\pi(S_t) \leftarrow \hat v^\pi(S_t) +\alpha (G_t - \hat v^\pi(S_t))\ \ \   0< \alpha < 1\\
       $$
       $\alpha$ is the update rate

   - Temporal difference  terminology

     - $$
       \hat v^\pi(S_t) \leftarrow \hat v^\pi(S_t) +\alpha (G_t - \hat v^\pi(S_t))  \\
       G_t = R_{t+1} + \gamma \hat v^\pi(S_{t+1} ) \\
       \hat v^\pi(S_t) \leftarrow \hat v^\pi(S_t) +\alpha (R_{t+1} + \gamma \hat v^\pi(S_{t+1} ) - \hat v^\pi(S_t))
       $$

     - "TD target": $R_{t+1} + \gamma \hat v^\pi(S_{t+1} )$

     - "TD error":  $R_{t+1} + \gamma \hat v^\pi(S_{t+1} ) - \hat v^\pi(S_t)$

       ![TD_RL.png](img\TD_RL.png)

   - MC vs TD

     - MC: unbiased, but usually has a higher variance
     - TD:  biased, but usually has a lower variance

   - Other version of TD algorithms

     - Sarsa algorithm

       <img src="https://i.stack.imgur.com/R7xR1.png">

     - Q-learning algorithm

       <img src="https://articles.wearepop.com/hubfs/images/_article/SecretFormula/Images_Algorithm_pt2_3.gif?t=1515543793775">

       ​

4. `Issues with terminology`  (details in slides)

### Fuzzy Logic

1. `Introduction` details in slides

2. `Fuzzy Sets anf Membership Functions`

   - fuzzy set:  fundamental to mathematics. Example:  "tall man" is a fuzzy set

   - Membership Function: the degree of an element of universe X belong to a fuzzy set.

     - $\mu_A(x) = 1$  if x is totally in A;  
     - $\mu_A(x) = 0$  if x is not in A; 
     - $0< \mu_A(x) < 1$  if x is partly in A; 

   - Example: 

     ![Membership.png](img\Membership.png)

     5 Fuzzy Set:   ==Very Short==,  ==Short==, ==Medium==, ==Tall==, ==Very Tall==

     Membership Function:  ==curve in the coordinate system==

3. `Fuzzy Linguistic Variables`

   - example of FLV:  

     - Colour:  red, blue, green,...
     - age: young, middle-aged, old, very-old,
     - size: small, big, very big, ...

   - representation of hedges in fuzzy logic

     <img src="http://images.slideplayer.com/26/8533323/slides/slide_38.jpg">

     <img src="http://images.slideplayer.com/26/8533323/slides/slide_39.jpg">

4. `Fuzzy Set Operations and Properties` :raised_hands:   :star::star::star:

   ==Assume a Fuzzy set:==   $A = \mu_A(x_i)/x_i + ............+\mu_A(x_n)/x_n$

   - Operations

     - __Complement__:  $\mu_\bar A(x) = 1 - \mu_A(x)$

     - __Containment__:  all elements have the smaller membership value compare to another fuzzy set

     - __Insertion__:  $\mu_{A\cap B}(x) = min[\mu_A(x), \mu_B(x)] = \mu_B(x) \cap \mu_B(x) $

     - __Union__: $\mu_{A\cup B}(x) = max[\mu_A(x), \mu_B(x)] = \mu_B(x) \cup \mu_B(x) $

       <img src="https://image.slidesharecdn.com/fuzzylogicanditsapplicationinenvironmentalengineering-170116083318/95/fuzzy-logic-and-its-application-in-environmental-engineering-7-638.jpg?cb=1484555710">

   - Properties

     - __Equality__:  $\mu_A(x)  = \mu_B(x), \forall x \in X $  
     - __Inclusion__:  $\mu_A(x) \leq \mu_B(x) , \forall x\in X$ 
     - __Cardinality__:  $card_A = \mu_A(x_1)+\mu_A(x_2) + ...+ \mu_A(x_n) =\sum_{\mu_A}(x_i) $
     - __Empty Fuzzy Set__:  $\mu_A(x)  = 0,  \forall x \in X $
     - __Alpha-cut__:  $A_{\alpha} = \{\mu_A(x)  \geq \alpha, \forall x\in X\}$
     - __Fuzzy Set Normality__ : a fuzzy sunset is normal if there exits at least one element $\mu_A(x) = 1$
     - __Height__: $height(A) = max_x(\mu_A(x))$
     - __Core__:  $core(A) = \{x| \mu_A(x) = 1\ \ and\ \ x \in X\}$
     - __Support__:  $supp(A) =  \{x| \mu_A(x) > 0\ \ and\ \ x \in X\}$

5. `Fuzzy Rules`

   - If ....  Then....  (FLV are used in fuzzy rules)
   - Example: If height is tall, Then weight is heavy.

6. `Fuzzy Inference System`

   - Step1: Input Fuzzification

   - Step2: Fuzzy Rules Evaluation

   - Step3: Calculate Membership

   - Step4: Activate Fuzzy Rules

   - Step5: Compute Decision Function

   - Step6: Compute Final Decision

     ==__Specific Example could see slides__==

7. `Summary`
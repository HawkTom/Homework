### AAI-Homework

---

**(1) Discuss the strength and weakness of TD learning and MC learning. Explain when you would use which algorithm and why.**

*Sol*  

TD learning is biased, but it usually has a lower variance.  The learning process is faster because it estimate Q-value only from current reward.  But the targets are based on the model itself which make this method less stable.  And it may convergence to a wrong solution if the model starts off arbitrarily wrong.  

MC learning is unbiased but it usually has a high variance. We estimate the Q-values for occurred state-action pairs from the following sequence of rewards. Since we only use received rewards, this estimate is unbiased and the model will get trained towards the true Q-values on average.

So, when the problem has a strong requirement of response time and less need for the accuracy, the TD algorithm is a good choice.  On the contrary, the MC algorithm is used for the condition with high demand in accuracy while low requirements in real time. 

**(2) Find out from the literature by yourself what TD(λ) learning algorithm is. Describe in your own words how it works.**

*Sol*  

In the TD learning algorithm, we update $v^{\pi}$ at each step, this could called TD(0) algorithm.  

And in another condition that if only update the $v^{\pi}$ when it have passed $m_{th}$ step from this step, where $m_{th}$  step is our terminal condition.  This situation is called TD(1) algorithm.

For above two algorithm, they have own features.  For TD(0) it updated at each step, it means no feedback occurs beyond the current time step.  While for TD(1), the error feeds back without decay arbitrary far in time.

So TD($\lambda$) is smooth way between above two methods.  This method means the step much closer to the target, it has much more influence on this step.   

The pseudo code of TD($\lambda$) is show below.  (In the back page)

![TD lambda](..\img\TD lambda.png)

If $\lambda = 1$, the algorithm is TD(1) algorithm. And when $\lambda = 0$, the algorithm is the TD(0) algorithm.
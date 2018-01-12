### AAI-Homework

---

**Projection of *z* onto set *S*, denoted often P(*z*; *S*) amounts to finding the closest point (in the Euclidean metric) in *S* from *x*  **

**Assume that $S = \left \{x|c^Tx\leq b\right\}$ for  some vector *c* and some scalar *b***

**Write this as a optimization problem, determine which kind of problem it is (linear, quadratic, ...)**

**Provide a close-form formula to find the projection for arbitrary *c*, *b* and *z***

*Sol:*

The problem could be formulated as this :
$$
 min\ f(\textbf x) =\frac{1}{2} \left \| \textbf x- \textbf z  \right \|^2 =\frac{1}{2} \sum_{i=1}^{n} (x_i - z_i)^2\\
subject\ to: c^T x\leq b\\
$$
$c, b,x,z​$ are vectors

Obviously, it is a **quadratic** problem.
$$
L(x, \lambda ) = \frac{1}{2}\sum_{i=1}^{n} (x_i - z_i)^2 + \lambda (c^Tx -b)
$$
By the **KKT conditions:**
$$
\frac{\partial L}{\partial x} = (x-z) + \lambda c = 0  \ \ \ \ \ (1)\\
c^T x-b\leq 0 \ \ \ \ \ (2)\\
\lambda (c^Tx-b) = 0 \ \ \ \ \ (3)\\
\lambda \geq 0 \ \ \ \ \ (4)
$$
$c, b,x,z$ are vectors

From the equation (3), we can get either $\lambda = 0$ or $c^Tx-b=0$:

1.  $\lambda = 0:$     $x=z$    replace the $x$ in equation (2),  we can get  $c^Tz -b \leq 0$


2. $\lambda > 0$ ,      $c^Tx - b =0$  

   Simultaneous equation (1) and equation (3)
   $$
   \begin{equation}
   \left\{
   \begin{array}{rl}
   c^Tx - b&=0\ \ \ \ \ \ (5)\\
   x-z+\lambda c&=0 \ \ \ \ \ \ (6)
   \end{array}
   \right.
   \end{equation}
   $$
   we can get $x$ from equation (6) :
   $$
   x = z-\lambda c
   $$
   then take it into equation (5) so that we get the $\lambda$
   $$
   \lambda = \frac{c^Tz-b}{c^Tc}
   $$

   $$
   \therefore \ \ c^Tz-b >0 
   $$

   Finally, we take the value of $\lambda$ into equation (6), so, we can get the value of $x$
   $$
   x = z-\lambda c = z-\frac{c^Tz-b}{c^Tc}\cdot c
   $$




So, in conclusion, we can see this problem in two views:

- when $c^Tz-b\leq 0$, the minimal point $x =z$,  this means when the given point is in the scope of the constrains, the minimal point is same as the given point
- when $c^Tz-b> 0$, the minimal point $x =z-\frac{c^Tz-b}{c^Tc}\cdot c$ ,  this means when the given point is out of the constrains, the minimal point is in the boundary of constrains.




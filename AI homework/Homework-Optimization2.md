### AAI-Homework

---

- **Consider the (very artificial) network**
- **There is one commodity**
- **The commodity is measured in units. Only integer units allowed. No fractional units are possible**
- **There are *M* producers and *N* consumers producing this commodity. **
- **Producer m produces $p_m$ unit of commodity. Consumer *n* requires  $c_n$ units of commodity.**
- **The cost of transporting *k* units of commodity from producer *m* to consumer *n* equals to $kc_{mn}$ (linear dependence).**
- **The goal is to design which producer sends how many units to each consumer.**

### Question

**1.Write the equivalent condition under which the demands of all consumers will be satisfied.  **

*Sol:*   
$$
\sum_{m=1}^{M}p_m \geq \sum_{n=1}^{N}c_n \\
 \sum_{m=1}^{M}k_{mn} \geq c_n\ \ for\ each \ comsumer
$$
**2. Write this problem as an integer problem. **

*Sol:* 
$$
\begin{align}
&Minimize\ \ \  f = \sum_{m=1}^{M}\sum_{n=1}^{N}k_{mn}c_{mn} \\
\end{align}
$$

$$
\begin{align}
subject\ \ to:
&  \sum_{m=1}^{M}k_{mn} \geq c_n\ \ for\ each \ comsumer \\
&\sum_{n=1}^{N}k_{mn} \leq p_m\ \  for\ each\ producer \\
& k_{mn}\ is\ interger
\end{align}
$$

**3. How the problem changes if producer $m$ is allowed to send consumer $n$ at most one unit of commodity?**

*sol:*

The problem needs to add a constraint :
$$
k_{mn} \in \{0, 1\}
$$
**4. For the later problem, suggest a representation of variables suitable for an evolutionary algorithm.**

*Sol:*

In this problem, we can use binary representation (binary encoding of candidate solution), because from the question 3, we can see the each $k$ only has two statues which is very suitable for binary encoding.



**5. Write basic pseudo code of an EA solving this problem**

```ruby
BEGIN
initial population using binary representation
FOR i=0,...,n DO
	calulating the fitness of each individual
	based on fitness select the parents
	randomly choose individual to mutation
	randomly choose two individuals to crossover
	form new population
	IF termination criterion THEN
		break
	END IF
END FOR
END
```


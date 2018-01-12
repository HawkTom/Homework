### AAI-Homework

---

- **Question:  Derive the closed-form solution of MLR** 
- **Hint : At variable-level: **
  - **(1) Compute the write $i^{th}$ equation $\frac{\partial}{\partial w_i}L(w) = 0$.**
  - **Re-write the $i^{th}$ equation into 'vector-vector' form.**
  - **Align the m equation about $x_i^{(n)}$ into a matrix-vector form. Note to check the match of dimensionality.**
  - **Obtain the representation of $w$.**
- **Hint: The solution is much easier to characterize in matrix notation. **

*Sol:* 
$$
min_\textbf wL(\textbf w) = \frac{1}{2}\sum_{n=1}^{N}[y^{(n)} - \textbf w^T\textbf x^{(n)}]^2
$$

$$
\begin{align}
\frac{\partial}{\partial w_i}L(\textbf w) 
& =  \frac{\partial}{\partial w_i} \{\frac{1}{2}\sum_{n=1}^{N}[y^{(n)} - \textbf w^T\textbf x^{(n)}]^2\} \\
& =\sum_{n=1}^{N}[y^{(n)} - \textbf w^T\textbf x^{(n)}]*(-x_i^{(n)})
\end{align}
$$

$$
(\frac{\partial}{\partial \textbf w}L(\textbf w) )^T = [y^1-\textbf w^T\textbf x^1,\ y^2-\textbf w^T\textbf x^2,\ ...,\ y^N-\textbf w^T\textbf x^N]\cdot  
\begin{bmatrix}
x_1^1 & x_2^1&\dots&x_{(m+1)}^1\\
x_1^2& x_2^2&\dots&x_{(m+1)}^2\\
\dots&\dots&\dots&\dots \\
x_1^N & x_2^N&\dots&x_{(m+1)}^N\\
\end{bmatrix}
$$

$$
\textbf X = 
\begin{bmatrix}
\textbf x^1\\
\textbf x^2\\
\dots \\
\textbf x^N \\
\end{bmatrix} 
=
\begin{bmatrix}
x_1^1 & x_2^1&\dots&x_{(m+1)}^1\\
x_1^2& x_2^2&\dots&x_{(m+1)}^2\\
\dots&\dots&\dots&\dots \\
x_1^N & x_2^N&\dots&x_{(m+1)}^N\\
\end{bmatrix}
\\
\textbf y :N*1 \ \ \ \ \textbf w: (m+1)*1
$$

$$
[y^1-\textbf w^T\textbf x^1,\ y^2-\textbf w^T\textbf x^2,\ ...,\ y^N-\textbf w^T\textbf x^N]^T = \textbf y - \textbf X\textbf w
$$

$$
(\frac{\partial}{\partial \textbf w}L(\textbf w) )^T = (\textbf y - \textbf X\textbf w)^T \cdot \textbf X = \textbf 0
$$

$$
\textbf y^T \textbf X- \textbf w^T\textbf X^T \textbf X = \textbf 0 \\
\textbf w = (\textbf X^T \textbf X)^{-1}\textbf X^T \textbf y
$$


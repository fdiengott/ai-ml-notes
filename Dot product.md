The dot product multiplies the values in two vectors element-wise and then sums the result.
Vector dot product requires the dimensions of the two vectors to be the same. 

It is represented by a dot!

$$
\begin{align}
& a \cdot b = \sum_{i=0}^{n-1}a_ib_i \\ \\
& a \cdot b = 
	\begin{bmatrix}
		a_0\\
		a_1\\
		...\\
		a_k\\
    \end{bmatrix}
	\begin{bmatrix}
		b_0\\
		b_1\\
		...\\
		b_k\\
    \end{bmatrix}
    = [a_0b_0 + a_1b_1 + ... + a_nb_n]
\end{align}
$$

or


$$
\begin{align}
\vec{w} = [w_1\; w_2\; ... w_n] \\
\vec{x} = [x_1\; x_2\; ... x_n] \\
\\
\vec{w} \cdot \vec{x} = w_1x_1 + w_2x_2 + ... + w_nx_n
\end{align}
$$
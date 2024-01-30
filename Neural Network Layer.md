
$$
\begin{align}
	& \begin{bmatrix}
	197\\
	184\\
	136\\
	214\\
	\end{bmatrix}
	\;
	\begin{aligned}
		\vec{x}\\
		\rightarrow
	\end{aligned}
	\;
	&& \begin{bmatrix}
		 \enclose{circle}{w_1,b_1}\\
		 \enclose{circle}{w_2,b_2}\\
		 \enclose{circle}{w_3,b_3}\\
	\end{bmatrix}
	\begin{aligned}
		a_1^{[1]} = g(\vec{w_1}^{[1]} \cdot \vec{x} + b_1^{[1]}) \\
		a_2^{[1]} = g(\vec{w_2}^{[1]} \cdot \vec{x} + b_2^{[1]}) \\
		a_3^{[1]} = g(\vec{w_3}^{[1]} \cdot \vec{x} + b_3^{[1]}) \\
	\end{aligned}
	\;
	&&& \begin{aligned}
		\vec{a}\\
		\rightarrow
	\end{aligned}
	&&&& \begin{bmatrix}
		 0.3\\
		 0.7\\
		 0.2\\
	\end{bmatrix}
\\
&\text{input layer}
&&\text{hidden layer}
&&& \text{activations}
&&&& \text{output layer}
\end{align}
$$

The first layer $\vec{x}$ can also be referred to as $\vec{a}^{[0]}$

$$
\begin{align}
	& \vec{a}^{[0]}
	\rightarrow 
	&& \begin{bmatrix}
		\enclose{circle}{}\\
		\enclose{circle}{}\\
		\enclose{circle}{}\\
	\end{bmatrix}
	\begin{aligned}
		\vec{a}^{[1]}\\
		\rightarrow
	\end{aligned}
	&& \enclose{box}{\enclose{circle}{}}
	\quad
	\begin{aligned}
		\vec{a}^{[2]}
	\end{aligned}
	\\
	& \text{layer 0}
	&& \text{layer 1}
	&& \text{layer 2}
\end{align}
$$

$\vec{a}^{[i]}$ - refers to the activations output by layer $i$. 

![[Pasted image 20231210165854.png]]


## Equation for a single activation value
$$
a_j^{[l]} = g(\vec{w}_j^{[l]} \cdot \vec{a}^{[l-1]} + b_j^{[l]})
$$
> $g()$ - activation function (e.g. sigmoid function)
> $j$ - the number value in the list of activations
> $l$ - the layer we are in
> $a$ - activation value
> $w$ - weight
> $b$ - bias

The activation value is based on the value of the dot product of the proper weight vector plus the activation from the previous layer, but this layer's bias run through a sigmoid function

## Types
- Dense Layer
	- Each neuron output is a function of *all* the activation outputs of the previous layer
- Convolutional Layer ^f5930e
	- Each neuron only looks at part of the previous layer's outputs
		- Faster computation
		- Need less training data (less prone to overfitting)

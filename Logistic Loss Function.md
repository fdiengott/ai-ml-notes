> Loss - a measure of the difference of a single example to its target value

Convex function

$$
L(f_{\vec{w},b}(\vec{x}^{(i)}, y^{(i)})) = \Biggl\{ 
\begin{align}
-log(f_{\vec{w}, b}(\vec{x}^{(i)})) \quad if \; y^{(i)} = 1 \\
-log(1 - f_{\vec{w}, b}(\vec{x}^{(i)})) \quad if \; y^{(i)} = 0
\end{align}
$$
> L - loss

Simplified into one equation
$$
  loss(f_{\mathbf{w},b}(\mathbf{x}^{(i)}), y^{(i)}) = (-y^{(i)} \log\left(f_{\mathbf{w},b}\left( \mathbf{x}^{(i)} \right) \right) - \left( 1 - y^{(i)}\right) \log \left( 1 - f_{\mathbf{w},b}\left( \mathbf{x}^{(i)} \right) \right)
$$


First equation
![[Pasted image 20231203171317.png]]


2nd equation
![[Pasted image 20231203170654.png]]


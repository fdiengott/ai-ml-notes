
### Example 
$$
\begin{align}
&w_0x_0 + w_1x_1 + b \\
&w_0x_0 + w_1x_1 + w_2x_0^2 + w_3x_0x_1 + w_4x_1^2 + b \\
&w_0x_0 + w_1x_1 + w_2x_0^2 + w_3x_0x_1 + w_4x_1^2 + w_5x_0^3 + w_6x_0^2x_1 + w_7x_0x_1^2 + w_8x_1^3 + b \\
&w_0x_0 + w_1x_1 + w_2x_0^2 + w_3x_0x_1 + w_4x_1^2 + w_5x_0^3 + w_6x_0^2x_1 + w_7x_0x_1^2 + w_8x_1^3 + w_{10}x_0^3x_1 + w_{ 9}x_0^4 + w_{11}x_0^2x_1^2 + w_{12}x_0^1x_1^3 + w_{13}x_1^4 + b \\
\end{align}
$$

### Code
```python
def map_feature(x1, x2, degree = 6):
    x1 = np.atleast_1d(x1)
    x2 = np.atleast_1d(x2)
    
    out = []

    for i in range(1, degree + 1):
        for j in range(i + 1):
            out.append(x1**(i-j) * x2**j) 

    return np.stack(out, axis=1)
```
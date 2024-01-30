Back propagation requires several steps no matter the function (logistic regression, neural network, etc.)

1. specify how to compute the output given the input x and params w, b 
	ex. 	
		`z = np.dot(w,x)`
		`f_x = 1 / (1+np.exp(-z)`
2. Specify loss and cost
	ex. 
		Logistic loss `loss = -y*np.log(f_x) - (1-y)*np.log(1-f_x)`
3. Train on data to minimize $J$
	ex. gradient descent: `w = w-alpha * dj_dw`

## Computing
![[Pasted image 20231229181150.png]]
A right to left operation using the chain rule. 
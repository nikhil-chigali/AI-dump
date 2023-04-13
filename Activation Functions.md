# Logistic function
Logistic function also known as a #sigmoid function is used to predict the probability of an output node being between 0 and 1. #classification 
	$\large f(x) = {\large \frac{1}{1+e^{-x}}}$  
Refer [[Algebra]] for more info.

# Tanh function
Tanh is also a type of #sigmoid function and is used to predict if an output node is between 1 and -1. Used in classification use cases. #classification #regression 
	$f(x) = {\large \frac{e^{x} - e^{-x}}{e^{x} + e^{-x}}}$ 

# ReLU 
ReLU(Rectified Linear Unit) used to set the output node to 0 if fuction result is negative and keeps the result value if the result is a positive value. #regression #classification
	$\large f(x)= {\begin{cases} 0, & \text{if } x < 0\\ x, & \text{if } x\geq 0\\ \end{cases}}$ 

# Softmax  
Softmax takes *logits* - raw value on \[ $-\infty, \infty$ ] and returns probability distribution across all the output labels (i.e., the sum of all the probabilities will equate to 1).  #classification
	$\large f(x) = { \frac{e^{x_i}}{\Sigma_j {e^{x_j}}}}$ 

# Log Softmax 
It is a stabilized Softmax function. It's simply the logarithm of Softmax function (i.e., it gives log probabilities instead of probabilities). Log probabilities are on a logarithmic scale instead of the standard $\large [0,1]$ interval #classification 
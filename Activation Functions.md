1. **Logistic function_** is used to predict the probability of an output node being between 0 and 1. 
	$f(x) = {\large \frac{1}{1+e^{-x}}}$ 
![[Algebra#^43f596]]
2. 
3. **_Tanh_** is used to predict if an output node is between 1 and -1. Used in classification use cases. 
	$f(x) = {\large \frac{e^{x} - e^{-x}}{e^{x} + e^{-x}}}$ ^f7d8f5
4. **_ReLU_** (Rectified Linear Unit) used to set the output node to 0 if fuction result is negative and keeps the result value if the result is a positive value. 
	$f(x)= {\small \begin{cases} 0, & \text{if } x < 0\\ x, & \text{if } x\geq 0\\ \end{cases}}$
5. ***Softmax*** takes *logits* - raw value on \[ $-\infty, \infty$ ] and returns probability distribution across all the output labels (i.e., the sum of all the probabilities will equate to 1).  
	$f(x) = {\large \frac{e^{x_i}}{\Sigma_j {e^{x_j}}}}$ 
6. ***Log Softmax*** is a stabilized Softmax function. It's simply the logarithm of Softmax function (i.e., it gives log probabilities instead of probabilities). Log probabilities are on a logarithmic scale instead of the standard $[0,1]$ interval
1. **_Sigmoid_** is used to predict the probability of an output node being between 0 and 1. 
	$f(x) = {\large \frac{1}{1+e^{-x}}}$
2. **_Tanh_** is used to predict if an output node is between 1 and -1. Used in classification use cases. 
	$f(x) = {\large \frac{e^{x} - e^{-x}}{e^{x} + e^{-x}}}$
3. **_ReLU_** (Rectified Linear Unit) used to set the output node to 0 if fuction result is negative and keeps the result value if the result is a positive value. 
	$f(x)= {\small \begin{cases} 0, & \text{if } x < 0\\ x, & \text{if } x\geq 0\\ \end{cases}}$
4. ***Softmax*** returns *logits* - raw value on \[ -$\infty, \infty$ ]  
	
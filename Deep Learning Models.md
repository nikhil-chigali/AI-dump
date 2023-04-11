# Neural Network

## Components of a neural network

-   **Activation function** determines whether a neuron should be activated or not. The computations that happen in a neural network include applying an activation function. If a neuron activates, then it means the input is important. There are different kinds of activation functions. The choice of which activation function to use depends on what you want the output to be. Another important role of an activation function is to add non-linearity to the model.
    -   _Binary_ used to set an output node to 1 if function result is positive and 0 if the function result is negative. 
		$f(x)= {\small \begin{cases} 0, & \text{if } x < 0\\ 1, & \text{if } x\geq 0\\ \end{cases}}$
    -   _Sigmoid_ is used to predict the probability of an output node being between 0 and 1. 
		$f(x) = {\large \frac{1}{1+e^{-x}}}$
    -   _Tanh_ is used to predict if an output node is between 1 and -1. Used in classification use cases. 
		$f(x) = {\large \frac{e^{x} - e^{-x}}{e^{x} + e^{-x}}}$
    -   _ReLU_ (Rectified Linear Unit) used to set the output node to 0 if fuction result is negative and keeps the result value if the result is a positive value. 
		 $f(x)= {\small \begin{cases} 0, & \text{if } x < 0\\ x, & \text{if } x\geq 0\\ \end{cases}}$
Read more - [[Activation Functions]]
-   **Weights** influence how well the output of our network will come close to the expected output value. As an input enters the neuron, it gets multiplied by a weight value and the resulting output is either observed, or passed to the next layer in the neural network. Weights for all neurons in a layer are organized into one tensor
-   **Bias** makes up the difference between the activation function's output and its intended output. A low bias suggest that the network is making more assumptions about the form of the output, whereas a high bias value makes less assumptions about the form of the output.
![[Pasted image 20230411144201.png]]
We can say that an output $y$ of a neural network layer with weights $W$ and bias $b$ is computed as summation of the inputs multiply by the weights plus the bias $x = \sum{(weights * inputs) + bias}$, where $f(x)$ is the activation function.
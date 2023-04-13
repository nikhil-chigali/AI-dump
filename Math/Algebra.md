# Likelihood
#todo

# Probability
#todo

# Odds
In #probabilitytheory, **odds** provide a measure of the likelihood of a particular outcome. They are calculated as the ratio of the number of events that produce that outcome to the number that do not. 

Odds also have a simple relation with probability: the odds of an outcome are the ratio of the probability that the outcome occurs to the probability that the outcome does not occur. In mathematical terms, where p is the probability of the outcome: $\large f: (0,1) \mapsto (-\infty, +\infty)$ 

	${\large {\text{odds}={\frac {p}{1-p}}}}$ 

where 1 – _p_ is the probability that the outcome does not occur.


![[Pasted image 20230413093136.png]]

# Odds Ratio
#todo

# Logits
#todo 
Mathematically, the logit is the inverse of the standard logistic function $\large \sigma (x)=1/(1+e^{-x})$, so the logit is defined as

	 $\large logit(p) = \sigma^{-1}(p) = ln \frac{p}{1-p} \;\; \text{for p} \in (0,1)$

Because of this, the logit is also called the **log-odds** since it is equal to the logarithm of the odds ${\large \frac  {p}{1-p}}$ where *p* is a probability. Thus, the logit is a type of function that maps probability values from $\large (0,1)$ to real numbers in ${\large (-\infty ,+\infty )}$ which is akin to *probit* (**prob**ability un**it**). However, calculating probit is computationally more expensive hence the use of *logit* was normalized.

# Logistic Function
#todo
Logistic function is a common example of a Sigmoid function (a function having a characteristic "S"-shaped curve), is denoted by $\large \sigma$ and is the inverse of logit function.
As Logit maps probabilites to real number; i.e., $\large f: (0,1) \mapsto \mathbb{R}$, Logistic function is useful in converting real values to probability range  $\large f: \mathbb{R} \mapsto (0,1)$ ^43f596


# Jacobian Matrix
For a vector function $\vec{y}=f(\vec{x})$, where
$\vec{x}=\langle x_1,\dots,x_n\rangle$ and
$\vec{y}=\langle y_1,\dots,y_m\rangle$, a gradient of $\vec{y}$ with respect to $\vec{x}$ is given by **Jacobian matrix**, whose element $J_{ij}$ contains $\large \frac{\partial y_{i}}{\partial x_{j}}$.
	$J = {\large \frac {d\vec{f(x)}}{d\vec{x}}} = \large \begin{bmatrix} \frac{\partial{\vec{f(x)}}}{\partial{x_1}} & \dots & \frac{\partial{\vec{f(x)}}}{\partial{x_m}} \end{bmatrix} = \large \begin{bmatrix} \frac{\partial{f_1(x)}}{\partial{x_1}} & \dots & \frac{\partial{f_1(x)}}{\partial{x_m}} \\ \vdots &  & \vdots \\ \frac{\partial{f_n(x)}}{\partial{x_1}} & \dots & \frac{\partial{f_n(x)}}{\partial{x_m}} \end{bmatrix}$  ^ef3bda

> [!note]
![[Pasted image 20230411164322.png]]
> A nonlinear map $f: \mathbb{R}^2 \mapsto \mathbb{R}^2$ sends a small square (left, in red) to a distorted parallelogram (right, in red). The Jacobian at a point gives the best linear approximation of the distorted parallelogram near that point (right, in translucent white), and the **Jacobian determinant** gives the ratio of the area of the approximating parallelogram to that of the original square. 

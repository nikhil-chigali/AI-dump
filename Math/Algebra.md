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
Mathematically, the logit is the inverse of the standard logistic function $\sigma (x)=1/(1+e^{-x})$, so the logit is defined as
 If p is a probability, then  _p_ / (1 − _p_) is the corresponding odds; the logit of the probability is the logarithm of the odds, i.e.:

# Logistic Function
#todo

# Jacobian Matrix
For a vector function $\vec{y}=f(\vec{x})$, where
$\vec{x}=\langle x_1,\dots,x_n\rangle$ and
$\vec{y}=\langle y_1,\dots,y_m\rangle$, a gradient of $\vec{y}$ with respect to $\vec{x}$ is given by **Jacobian matrix**, whose element $J_{ij}$ contains $\large \frac{\partial y_{i}}{\partial x_{j}}$.
$J = {\large \frac {d\vec{f(x)}}{d\vec{x}}} = \large \begin{bmatrix} \frac{\partial{\vec{f(x)}}}{\partial{x_1}} & \dots & \frac{\partial{\vec{f(x)}}}{\partial{x_m}} \end{bmatrix} = \large \begin{bmatrix} \frac{\partial{f_1(x)}}{\partial{x_1}} & \dots & \frac{\partial{f_1(x)}}{\partial{x_m}} \\ \vdots &  & \vdots \\ \frac{\partial{f_n(x)}}{\partial{x_1}} & \dots & \frac{\partial{f_n(x)}}{\partial{x_m}} \end{bmatrix}$  ^ef3bda

> [!note]
![[Pasted image 20230411164322.png]]
> A nonlinear map $f: \mathbb{R}^2 \mapsto \mathbb{R}^2$ sends a small square (left, in red) to a distorted parallelogram (right, in red). The Jacobian at a point gives the best linear approximation of the distorted parallelogram near that point (right, in translucent white), and the **Jacobian determinant** gives the ratio of the area of the approximating parallelogram to that of the original square. 

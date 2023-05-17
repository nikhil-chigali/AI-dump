# Likelihood
#task

# Probability
Probability is a measure of the likelihood of an event to occur. Many events cannot be predicted with total certainty.
	Probability of occurrence of an event P(E) = Number of favorable outcomes / Total Number of outcomes ^33cf6a

## General Rules of Probability
### Probability Rule 1
-   For any event A, 0 ≤ P(A) ≤ 1.

### Probability Rule 2
-  The sum of the probabilities of all possible outcomes is 1.

### Probability Rule 3 (The Complement Rule)
-  P(not A) = 1 – P(A)
-  that is, the probability that an event does not occur is 1 minus the probability that it does occur.

### Probability Rule 4 (The Addition Rule for Disjoint Events)
- If A and B are disjoint (mutually exclusive) events, then P(A or B) = P(A) + P(B)

### Probability Rule 5 (The General Addition Rule)
-  P(A or B) = P(A) + P(B) - P(A and B)

### Probability Rule 6 (The Multiplication Rule for Independent Events)

^547e20

- If A and B are two INDEPENDENT events, then P(A and B) = P(A) * P(B) ^fbf82d

### Probability Rule 7 (Conditional Probability Rule)
- The conditional probability of event B, given event A, is P(B | A) = P(A and B) / P(A)

### Probability Rule 8 (General Multiplication Rule)
- For any two events A and B, P(A and B) = P(A) * P(B | A)

## Bayes' Rule🅱️
P(B | A) 
	= P(A and B) / P(A) 
	= P(B and A) / P(A) 
	= P(B) * P(A | B) / P(A)
Hence, Bayes rule:
**P(B | A) = P(A | B) * P(B) / P(A)**

# Odds
In #probabilitytheory, **odds** provide a measure of the likelihood of a particular outcome. They are calculated as the ratio of the number of events that produce that outcome to the number that do not. 

Odds also have a simple relation with probability: the odds of an outcome are the ratio of the probability that the outcome occurs to the probability that the outcome does not occur. In mathematical terms, where p is the probability of the outcome: $\large f: (0,1) \mapsto (-\infty, +\infty)$ 

	${\large {\text{odds}={\frac {p}{1-p}}}}$ 

where 1 – _p_ is the probability that the outcome does not occur.


![[Pasted image 20230413093136.png]]

# Odds Ratio
#task

# Logits
Mathematically, the logit is the inverse of the standard logistic function $\large \sigma (x)=1/(1+e^{-x})$, so the logit is defined as

	 $\large logit(p) = \sigma^{-1}(p) = ln \frac{p}{1-p} \;\; \text{for p} \in (0,1)$

Because of this, the logit is also called the **log-odds** since it is equal to the logarithm of the odds ${\large \frac  {p}{1-p}}$ where *p* is a probability. Thus, the logit is a type of function that maps probability values from $\large (0,1)$ to real numbers in ${\large (-\infty ,+\infty )}$ which is akin to *probit* (**prob**ability un**it**). However, calculating probit is computationally more expensive hence the use of *logit* was normalized.

# Logistic Function
Logistic function is a common example of a #sigmoid function (a function having a characteristic "S"-shaped curve), is denoted by $\large \sigma$ and is the inverse of logit function.
As Logit maps probabilites to real number; i.e., $\large f: (0,1) \mapsto \mathbb{R}$, Logistic function is useful in converting real values to probability range  $\large f: \mathbb{R} \mapsto (0,1)$ 
	$\large f(x) = {\large \frac{1}{1+e^{-x}}} = \frac{e^x}{1+e^x}$

> [!info] 
> ![[Algebra#^fbf82d]]
> Since the **probabilities of independent events multiply**  , and logarithms convert multiplication to addition, **log probabilities of independent events add**. 
> Log probabilities are thus practical for computations, and have an intuitive interpretation in terms of #informationtheory: 
> - The negative of the average log probability is the information entropy of an event. 
> 
> Similarly, likelihoods are often transformed to the log scale, and the corresponding log-likelihood can be interpreted as the degree to which an event supports a statistical model. 

> [!note] 
> Representing probabilities, likelihoods and odds on a logarithmic scale has the following practical advantages:
> 1. **Speed** - Since multiplication is more expensive than addition, taking the product of a high number of probabilities is often faster if they are represented in log form. (The conversion to log form is expensive, but is only incurred once.) Multiplication arises from ![[Algebra#^547e20]]
> 2. **Accuracy** - The use of log probabilities improves numerical stability, when the probabilities are very small, because of the way in which computers approximate real numbers.
> 3. **Simplicity** - Many probability distributions have an exponential form. Taking the log of these distributions eliminates the exponential function, unwrapping the exponent. 
> 

# Jacobian Matrix
For a vector function $\vec{y}=f(\vec{x})$, where
$\vec{x}=\langle x_1,\dots,x_n\rangle$ and
$\vec{y}=\langle y_1,\dots,y_m\rangle$, a gradient of $\vec{y}$ with respect to $\vec{x}$ is given by **Jacobian matrix**, whose element $J_{ij}$ contains $\large \frac{\partial y_{i}}{\partial x_{j}}$.
	$J = {\large \frac {d\vec{f(x)}}{d\vec{x}}} = \large \begin{bmatrix} \frac{\partial{\vec{f(x)}}}{\partial{x_1}} & \dots & \frac{\partial{\vec{f(x)}}}{\partial{x_m}} \end{bmatrix} = \large \begin{bmatrix} \frac{\partial{f_1(x)}}{\partial{x_1}} & \dots & \frac{\partial{f_1(x)}}{\partial{x_m}} \\ \vdots &  & \vdots \\ \frac{\partial{f_n(x)}}{\partial{x_1}} & \dots & \frac{\partial{f_n(x)}}{\partial{x_m}} \end{bmatrix}$  ^ef3bda

> [!note]
![[Pasted image 20230411164322.png]]
> A nonlinear map $f: \mathbb{R}^2 \mapsto \mathbb{R}^2$ sends a small square (left, in red) to a distorted parallelogram (right, in red). The Jacobian at a point gives the best linear approximation of the distorted parallelogram near that point (right, in translucent white), and the **Jacobian determinant** gives the ratio of the area of the approximating parallelogram to that of the original square. 

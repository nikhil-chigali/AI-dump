Jacobian Matrix
For a vector function $\vec{y}=f(\vec{x})$, where
$\vec{x}=\langle x_1,\dots,x_n\rangle$ and
$\vec{y}=\langle y_1,\dots,y_m\rangle$, a gradient of $\vec{y}$ with respect to $\vec{x}$ is given by **Jacobian matrix**, whose element $J_{ij}$ contains $\large \frac{\partial y_{i}}{\partial x_{j}}$.
$J = {\large \frac {d\vec{f(x)}}{d\vec{x}}} = \large \begin{bmatrix} \frac{\partial{\vec{f(x)}}}{\partial{x_1}} & \dots & \frac{\partial{\vec{f(x)}}}{\partial{x_m}} \end{bmatrix} = \large \begin{bmatrix} \frac{\partial{f_1(x)}}{\partial{x_1}} & \dots & \frac{\partial{f_1(x)}}{\partial{x_m}} \\ \vdots &  & \vdots \\ \frac{\partial{f_n(x)}}{\partial{x_1}} & \dots & \frac{\partial{f_n(x)}}{\partial{x_m}} \end{bmatrix}$ 

> [!note]
![[Pasted image 20230411164322.png]]
> A nonlinear map $f: \mathbb{R}^2 \mapsto \mathbb{R}^2$ sends a small square (left, in red) to a distorted parallelogram (right, in red). The Jacobian at a point gives the best linear approximation of the distorted parallelogram near that point (right, in translucent white), and the Jacobian determinant gives the ratio of the area of the approximating parallelogram to that of the original square. #math

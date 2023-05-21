![[Pasted image 20230521082552.png]]

The regression line tries to map the linear association between the variable $X \& Y$
Where,
	$X=[x_1, x_2, \dots, x_n]$
	$Y=[y_1, y_2, \dots, y_n]$
To find this line of regression, recall the equation of a line
> [!tip] formula
> $\hat{y_i}=a+bx_{i}$
> Where, *a* is the intercept and *b* is the slope

We want to find those values of a and b which minimize the distance between $y_i, \hat{y_i}$


> [!tip] formula
> Find *a* and *b* that minimize,
> $\large{\Sigma_{i=1}^{n}(y_i-\hat{y_i})^2=\Sigma_{i=1}^{n}(y_i-(a+bx_{i}))^2}$

This is called **method of least squares**
Turns out,
> [!tip] formula
> $\large{b=r\frac{s_y}{s_x}}$
> $\large{a=\bar{y}-b\bar{x}}$

Another interpretation of regression line: 
> The average value of *y* when the first coordinate is near *x*.

Since average is the *best* predictor.
## Correlation Coefficient
Correlation is usually measured between two variables.
> [!note]
> Correlation doesn't mean Causation

Let's say the two variables we want to measure correlation for are $X, Y$
Where, 
	$X=[x_1, x_2, \dots, x_n]$
	$Y=[y_1, y_2, \dots, y_n]$
Means and Standard deviations of the variables are as follows,
	$\large{\bar{x}, s_x, \bar{y}, s_y}$
![[Pasted image 20230520173116.png]]
A scatter plot visualizes the relationship between two quantitative variables.
It may have,
1. Direction (sloping up or down)
2. Form (a scatter that clusters around a line is called *linear*)
3. Strength (how closely do the points follow the form?)

If the form is linear, then a good measure of strength is **correlation coefficient r**
>[!tip] Formula
> $\large{r = \frac{1}{n}\Sigma_{i=1}^{n}\frac{x_i-\bar{x}}{s_x}\times\frac{y_i-\bar{y}}{s_y}}$

This formula is simply the sum of product of each **standardized** $x_i$'s and $y_i$'s

>[!note]
>From the formula, we can deduce that if both $x_i$ and $y_i$ fall on the same side of the mean ($\bar{x} , \bar{y}$), then the correlation is going to be positive (i.e., in the case of a positive slope)
>If the relationship has a negative slope, then $x_i$ and $y_i$ don't fall on the same side of their means ($\bar{x} , \bar{y}$), in which case the data will have a negative correlation

>[!important]
> **Correlation always measures linear association.** 
>> If the data has a non-linear correlation, the correlation coefficient *r* won't be able to measure the association between the two variables

A numerical summary of the X

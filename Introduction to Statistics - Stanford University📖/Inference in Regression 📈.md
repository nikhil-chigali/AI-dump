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
> Average is the *best* predictor.

## Regression to the mean
Regression to the mean is a statistical phenomenon in which an extreme outcome is likely to revert back to average. This is often because the outlier experience involves a series of variables — either good or bad — occurring simultaneously to create a great or poor result, like flipping a coin and getting heads multiple times. This is why an extreme outcome is typically followed by an average result.

Regression to the mean doesn't mean that things are evening out. Rather, it goes to say that the extreme events are becoming diluted by the average events that occur much more commonly. 

Let's take our equation, $\hat{y}=a+bx$ 
The prediction of *y* at $x=\bar{x}$ is $\hat{y}=\bar{y}$
But $\large{b=r\frac{s_y}{s_x}}$ means that if *x* is 1 standard deviation $s_x$ above $\bar{x}$, then predicted $\hat{y}$ is only $rs_y$ above $\bar{y}$
Since *r* is between -1 and 1, the prediction is '*toward the mean*': $\hat{y}$ is few standard deviations away from $\bar{y}$ than $x$ is from $\bar{x}$

In a test-retest situation, the top scores will somewhat drop on the retest, the whole bottom group moves up.
This is because, in such kind of situations, there is more than just skill involved. It's usually a combination of "*skill + luck*" (i.e., random chance)

## Regression Fallacy
Some examples of Regression Fallacy
> [!example]
> -   A teacher laments: “When I praise my students for good work, the next time they try, they tend to be less good. When I punish my students for producing bad work, the next time they try, they tend to do much better. Therefore, punishments work, but rewards do not.”
> - An aspiring athlete marvels: “Wow, yesterday my foot was really painful, and I soaked it in a hot bowl of garlic-infused water, now it feels much better. There must be some healing properties in that garlicky water!”
> - A film critic stipulates: “Winning an Academy Award, the most prestigious prize in show business, can lead an actor’s career to decline rather than ascend._”_

False assumptions like these, where it is deduced that there's an underlying cause for change in performance in the *retest* situation, are called **regression fallacies**

Regression to mean help prevent these false assumptions.



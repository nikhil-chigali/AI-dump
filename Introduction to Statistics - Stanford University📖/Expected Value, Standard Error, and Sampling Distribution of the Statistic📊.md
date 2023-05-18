All the histograms in statistics that we see,
* Probability histogram that generates the data
* Histogram of the observed data
* Probability histogram of an estimator
---
## Expected Value
If we sample a data point (x) at random, we expect it to be around the population average $\mu$, give or take one standard deviation $\sigma$

The **expected value** of one random draw is the population average $\mu$

What about $\bar{x_n}$, the average of *n* draws?
The expected value of sample average, $E(\bar{x_n})$, is the population average $\mu$
But $\bar{x_n}$ is a random variable because sampling is a random process.
So $\bar{x_n}$ won't exactly be equal to $\mu = 69.3 in$; We might get, say, $\bar{x_n} = 70.1 in$. Taking another sample of size *n* might result in $\bar{x_n} = 69.1 in$

Now the question is how far off from $\mu$ will $\bar{x_n}$ be?

## Standard Error (SE)
is a statistic that tells roughly how far off the statistic will be from it's expected value

**Standard Error (SE)** of a statistic plays the same role that the **Standard Deviation $\sigma$** plays for one observation at random

The formula for **SE** is given by the Square root law 🌟

## Square Root Law
> [!tip] Formula
>$\large{SE(\bar{x_n}) = \frac{\sigma}{\sqrt{n}}}$

### The importance of the square root law is twofold:
1. It shows that the SE becomes smaller if we use a larger sample size *n*. We can use the formula to determine what sample size is required for desired accuracy (Controlling magnitude of *SE*, using *n*)
2. The formula for the standard error **does not depend on the size of the population**, only on the size of the sample
Standard error ties back to the errors that we saw in random sampling, expressed as "$chance\_error$" (Refer [[Simple Random Sampling and Other Sampling Plans 🎲]])

More about square root law in [[Square Root Law⚖️]]

## Expected Value and Standard Error for percentages
What percentage of likely voters approve the way the US President is handling his job?
Let, Approve = 1 and Disapprove = 0
Therefore,
> [!tip] Formula
> $E(\text{percentage of 1s}) = \mu \times 100$
> $SE(\text{percentage of 1s}) = \frac{\sigma}{\sqrt{n}} \times 100$

All of the above formulas are for sampling with replacement. They are still approximately true when sampling without replacement if the sample size is much smaller than the size of population
* Formula for $E$ is exactly true for sampling without replacement
* Formula for $SE$ is only approximately true for sampling without replacement. We have explicit formulas for without replacement

## Expected value and Standard error when simulating
All of the above formulas are also true when data are **simulated**, i.e., generated according to a **probability histogram**

> [!tip] Formula
> If the random variable $X$ that is simulated has $k$ possible **discrete** outcomes $x_1, x_2, \dots, x_k$, then
>> $\large{\mu = \Sigma_{i=1}^{k}x_{i}P(X=x_i)}$
>> $\large{\sigma^2 = \Sigma_{i=1}^{k}(x_{i}-\mu)^2P(X=x_i)}$ 
>If the random variable $X$ has a density $f$ (also said to have infinitely many solutions), such as when $X$ follows the normal curve, then
>> $\large{\mu = \int_{-\infty}^{\infty}xf(x)\,dx}$
>> $\large{\sigma^2 = \int_{-\infty}^{\infty}(x-\mu)^2f(x)\,dx}$ 
> 


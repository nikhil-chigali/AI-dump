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

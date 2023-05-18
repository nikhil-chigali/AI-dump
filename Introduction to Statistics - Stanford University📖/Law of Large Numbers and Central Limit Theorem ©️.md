[[Square Root Law⚖️]] states that $SE(\bar{x_n})$, the standard error of the sample mean, goes to zero as sample size increases.
Therefore, 
>[!info] Law of Large Numbers
>The sample mean $\bar{x_n}$ will likely be close to its expected value $\mu$ if the sample size is large. This is the **law of large numbers**

Keep in mind that law of large numbers applies,
1. for averages and therefore also for percentages, but not for sums as SE *increases* with sample size
2. for sampling with replacement from a population, or for simulating data from probability histogram
>[!note]
>In terms of the [[Expected Value, Standard Error, and Sampling Distribution of the Statistic📊#Three Histograms]]
>The law of large numbers state that the empirical histogram of the data (Histogram #2) will be close to the probability of probability histogram (Histogram #1) if the sample size is large

## Central Limit Theorem (CLT)
When sampling with replacement and *n* is large, then the sampling distribution of the sample average (or sum or percentage) approximately follows the normal curve. 
> [!note]
To standardize, subtract off the expected value of the statistic, then divide by its SE.

Ex:![[Pasted image 20230518181811.png]]

The key point of the theorem is that we know that the sampling distribution of the statistic is normal *no matter what the population histogram is:*
![[Pasted image 20230516144805.png]]
	$\mu = \$ 67,000$
	$\sigma = \$ 38,000$
If we sample *n* incomes at random, then the sample average $\bar{x_n}$ follows a normal curve centered at 
	$E(\bar{x_n}) = \mu = \$67,000$
and its spread given by
	$SE(\bar{x_n}) = \frac{\sigma}{\sqrt{n}} = \frac{\$38,000}{\sqrt{n}}$
If we sample 100 incomes, then by empirical rule there is about 16% chance that $\bar{x_n}$ is larger than $E+1SE = \$ 70,800$
	$SE(\bar{x_n}) = \frac{\$38,000}{\sqrt{n}} = \frac{\$38,000}{\sqrt{100}} = \$3,800$

## When does the Central Limit Theorem apply?
For the normal approximation to work, the key requirements are: 
1. We sample with replacement, or we simulate independent random variables from the same distribution.
2. The statistic of interest is a sum (averages and percentages are sums in disguise).
3. The sample size is large enough: the more skewed the population histogram is, the larger the required sample size n. 
    (if there is no strong skewness, then n ≥ 15 is sufficient. For stronger skewness, we need a sample size of at least 40)
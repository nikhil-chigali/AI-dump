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

The formula for **SE** is given by the [[Square Root Law⚖️]]

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

## Expected value and standard error for the sum
Sometimes we are interested in the sum of *n* draws ($S_n$) rather than the average ($\bar{x_n}$)
Sum and average are related by $S_n = n\bar{x_n}$
Similarly the expected value and the standard error can be obtained by multiplying by n,
> [!tip] Formula
> $E(S_n) = n\mu$
> $SE(S_n) = \sqrt{n}\sigma$
>> [!note]
>> Unlike $SE$ of Averages ($\frac{\sigma}{\sqrt{n}}$) and Percentages ($\frac{\sigma}{\sqrt{n}}\times 100$) which decreases as the sample size *n* increases, the Standard error of Sum $SE(S_n)$ increases up with the sample size  ($\sqrt{n}\sigma$) 

>[!example]
>Toss a coin 100 times. How many Tails do you expect to see? Give or take how many?
>Let, Tails = 1 & Heads = 0
>P(Tails) = P(Heads) = 1/2
>Number of Tails = Sum of 100 Draws
>$E(S_n) = n\mu = n(\Sigma_{i=1}^{k}x_{i}P(X=x_i)) = 100\times\frac{1}{2} = 50$
>$SE(S_n) = \sqrt{n}\sigma = n(\sqrt{\Sigma_{i=1}^{k}(x_{i}-\mu)^2P(X=x_i)}) = \sqrt{100}\times\frac{1}{2} = 5$

$SE(\text{percentage of tails}) = \frac{\sigma}{\sqrt{n}} = 5\%$

## Sampling Distribution
**Experiment:** Toss a coin 100 times. The number of tails has the following possible outcomes - 0,1,2,3,...,100
How likely is each outcome?

**Observation:** The number of tails has the binomial distribution with n=100, p=0.5 ('success' = coin lands tails)

So if the statistic of interest is $S_n$ = 'number of tails', then
$S_n$ is a random variable whose probability histogram is given by the binomial distribution. This is called **sampling distribution** of the statistic $S_n$

The sampling distribution of $S_n$ provides more detailed information about the chance properties of $S_n$ than the summary numbers given by the expected value and the standard error

A sampling distribution is a probability distribution of a statistic (such as the mean, standard deviation, variance, proportion, sum, and range) obtained from a larger number of samples drawn from a specific population. The sampling distribution of a given population is the distribution of frequencies of a range of different outcomes that could possibly occur for a statistic of a population.

## Understanding Sampling Distribution

A lot of data drawn and used by academicians, statisticians, researchers, marketers, analysts, etc. are actually samples, not populations. A sample is a subset of a population. 
For example, a medical researcher that wanted to compare the average weight of all babies born in North America from 1995 to 2005 to those born in South America within the same time period cannot draw the data for the entire population of over a million childbirths that occurred over the ten-year time frame within a reasonable amount of time. They will instead only use the weight of, say, 100 babies, in each continent to make a conclusion. The weight of 100 babies used is the sample, and the average weight calculated is the sample mean.

Now suppose that instead of taking just one sample of 100 newborn weights from each continent, the medical researcher takes repeated random samples from the general population, and computes the sample mean for each sample group. So, for North America, they pull up data for 100 newborn weights recorded in the U.S., Canada, and Mexico as follows: four 100 samples from select hospitals in the U.S., five 70 samples from Canada, and three 150 records from Mexico, for a total of 1,200 weights of newborn babies grouped in 12 sets. They also collect a sample data of 100 birth weights from each of the 12 countries in South America.

>[!note]
>Each sample has its own sample mean, and the distribution of the sample means is known as the sample distribution.

The average weight computed for each sample set is the sampling distribution of the mean. Not just the mean can be calculated from a sample. Other statistics, such as the standard deviation, variance, proportion, and range can be calculated from sample data. The standard deviation and variance measure the variability of the sampling distribution.

The number of observations in a population, the number of observations in a sample, and the procedure used to draw the sample sets determine the variability of a sampling distribution. 

> **The standard deviation of a sampling distribution is called the standard error**. 

While the mean of a sampling distribution is equal to the mean of the population, the standard error depends on the standard deviation of the population, the size of the population, and the size of the sample.

Knowing how spread apart the mean of each of the sample sets are from each other and from the population mean will give an indication of how close the sample mean is to the population mean. The standard error of the sampling distribution decreases as the sample size increases.

## Three Histograms
The chance process of tossing a coin 100 times comes with three different histograms:
1. The probability histogram for producing the data:![[Pasted image 20230518171132.png]]
	The probability graph is a theoretical construct for simulating data.
	Ex: P(H) = 0.5 and P(T) = 0.5
2. The histogram of the 100 observed tosses. This is an empirical histogram of real data:
![[Pasted image 20230518171314.png]]
	This graph looks similar to the probability histogram in the first step, but it's a little different because the 100 tosses involve a **chance process** (hence chance error is involved)
3. The probability histogram of the statistic $S_{100}$ = 'number of tails', which shows the distribution of $S_{100}$:![[Pasted image 20230518171727.png]]
	This histogram gives the **sampling distribution of the statistic** "Number of tails in 100 tosses ($S_{100}$)"
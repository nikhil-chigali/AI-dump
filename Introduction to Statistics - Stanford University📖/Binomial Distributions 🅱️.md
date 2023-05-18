Unlike Normal Distribution $N(\mu,\sigma)$, Binomial Distribution $B(n,p)$ is a discrete random variable and can be solved for exact solution.
## Binomial Setting
If you read a question and each trial only has 2 outcomes (pass/fail, heads/tails, boy/girl, etc.,), it could be in a **Binomial Setting** if:
1. Each observation is either success or failure
2. There is a fixed number "n" observations
3. All observations are **independent**
4. The probability of success "p" is the same/constant for all the observations

## Binomial Distribution
1. $\mathcal{X}$ is defined as the number of successes
2. $n$ trials
3. $p$ probability of success
$\mathcal{X}$ can take on whole number values between 0 & n with a distribution of $B(n,p)$

### Binomial Coefficient
The Binomial coefficient gives us the number of "k" successes out of "n" observations
> [!tip] Formula
> Binomial Coefficient $= \large {n \choose k} = \large\frac{n!}{k!(n-k)!}$

To put simply, it's the number of k combinations from n trials
Ex: 3 successes out of 10 trials,
$= \large {10 \choose 3} = \large\frac{10!}{3!(10-3)!} = 120 ways$

Now that we know the number of 'k' successes out of 'n' trials, let's look at the probability of observing 'k' successes out of 'n' trials,
> [!tip] Formula
>**Binomial Probability, $P(\mathcal{X}=\mathcal{k}) = \large {n \choose k}p^k(1-p)^{n-k}$**

We can use the binomial probability formula to calculate the probability without relying on any approximation table
> [!note]
> You can use $binompdf(n,p,k)$ to find binomial probabilities in a scientific calculator
> Similarly, $binomcdf(n,p,k)$ gives us the probability of X less than equals to k. $P(\mathcal{X} \le \mathcal{k})$

> [!example]
> You play an online game 10 times. Each time there are three possible outcomes: P(big prize) = 10%, P(small prize) = 20%, P(no prize) = 70%
> What is P(win 2 small prizes)?
> > Success = win small prize
> > Failure = Win big prize or nothing
> > P(2 small prizes in 10 games) = P(X=2)
> > $= \large {10 \choose 2}0.2^2(1-0.2)^{10-2}$
> > $= 30.2\%$

> [!info]
> The outcomes of the 10 experiments are due to chance, so the number of successes is random: One set of 10 exp might result in 4 successes, another set might result in 7 successes.
> Hence, we call $\mathcal{X}$ = number of successes a **random variable**
> In the above example, we see that $\mathcal{X}$ has a **binomial distribution**

## Probability Histogram
We can visualize the probabilities of various outcomes of $\mathcal{X}$ with a probability histogram:
![[Pasted image 20230518092244.png]]
A histogram of data gives percentages for observed data. In contrast, a probability histogram is a theoretical construct: it visualizes probabilities rather than that have been empirically observed.

## Normal approximation to Binomial distribution
Consider the same example as before, but now we have n=50 games & p=0.2,
![[Pasted image 20230518093136.png]]
The curve looks like it has a normal distribution to it. Another way of confirming if a Binomial Distribution is Normal is by checking the following 2 conditions:
> [!tip] Formula
>$np\ge10 \text{ and } n(1-p)\ge10$

Now if we would like to find **P(at most 12 small prizes)**, it would be tedious to do calculations for all $\large \mathcal{X}  \epsilon [0,12]$   
Rather, we can do a normal approximation to the function to find a value.

> [!tip] Formula
>Mean and Standard deviation of a binomial count, 
$\large{\mu = np; \sigma=\sqrt{np(1-p)}}$ given $np\ge10 \text{ and } n(1-p)\ge10$ is true

### Standardize
$\mathcal{X} = 12$
$\mu = np = 10$
$\sigma=\sqrt{np(1-p)} = 2.83$
	$z = \frac{x-\mu}{\sigma} = 0.71$
### Get probability value from the z-score table
for z = 0.71, P(X=12) is 76%

## Sampling without replacement
A **simple random sample** selects subjects without replacement.

This is not the binomial setting, as **p** changes after a subject has been removed, and it violates the **independence** condition
But if the population is much larger than the sample, then sampling with replacement is about the same as sampling without replacement
Then the number of successes will have approximately the binomial distribution (and so it will approximately follow the normal curve)

> [!note]
> When determining if there is a binomial setting, the **independence** check can be tricky. 
> 	*If the population is 10 times greater than the sample size*, then we can assume there is independence in a random selection

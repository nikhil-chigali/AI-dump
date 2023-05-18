Unlike Normal Distribution $N(\mu,\sigma)$, Binomial Distribution $B(n,p)$ is a discrete random variable and can be solved for exact solution.
## Binomial Setting
If you read a question and each trial only has 2 outcomes (pass/fail, heads/tails, boy/girl, etc.,), it could be in a **Binomial Setting** if:
1. Each observation is either success or failure
2. There is a fixed number "n" observations
3. All observations are **independent**
4. The probability of success "p" is the same/constant for all the observations
> [!note]
> When determining if there is a binomial setting, the **independence** check can be tricky. 
> 	*If the population is 10 times greater than the sample size*, then we can assume there is independence in a random selection

## Binomial Distribution
1. $\mathcal{X}$ is defined as the number of successes
2. $n$ trials
3. $p$ probability of success
$\mathcal{X}$ can take on whole number values between 0 & n with a distribution of $B(n,p)$

### Binomial Coefficient
The Binomial coefficient gives us the number of "k" successes out of "n" observations
	Binomial Coefficient $= \large {n \choose k} = \large\frac{n!}{k!(n-k)!}$
To put simply, it's the number of k combinations from n trials
Ex: 3 successes out of 10 trials,
$= \large {10 \choose 3} = \large\frac{10!}{3!(10-3)!} = 120 ways$

Now that we know the number of 'k' successes out of 'n' trials, let's look at the probability of observing 'k' successes out of 'n' trials,
	**Binomial Probability, $P(\mathcal{X}=\mathcal{k}) = \large {n \choose k}p^k(1-p)^{n-k}$**

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
> > $\large {10 \choose k}p^k(1-p)^{n-k}$

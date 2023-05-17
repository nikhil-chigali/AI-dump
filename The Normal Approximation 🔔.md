## The Empirical Rule (or) Three-Sigma Rule (or) 68-95-99.7 rule
states that for a normal distribution, (where $\mu$ is mean, and $\sigma$ is standard deviation)
1. 68% of the data falls within the first standard deviation from the mean. $(\mu \pm \sigma)$
2. 95% of the data falls within the first two standard deviations from the mean $(\mu \pm 2\sigma)$
3. 99.7% of the data falls within the first three standard deviations from the mean $(\mu \pm 3\sigma)$
![[Pasted image 20230517232651.png]]
> [!example]
> If the data follows a normal curve, the $\mu$ is 20 and $\sigma$ is 0.5, then,
> 1. 68% of the data falls between
> >   $(\mu \pm \sigma) = (20 - 0.5, 20 + 0.5) = (19.5, 20.5)$
> 2. 95% of the data falls between
> >   $(\mu \pm 2\sigma) = (20 - 2\times0.5, 20 + 2\times0.5) = (19, 21)$
> 3. 99.7% of the data falls between
> >   $(\mu \pm 3\sigma) = (20 - 3\times0.5, 20 + 3\times0.5) = (18.5, 21.5)$

## Standardizing data
A normal curve is determined by $\mu$ and $\sigma$ : If the data follows the normal curve, then knowing $\mu$ and $\sigma$ means knowing the whole histogram from the empirical rule.
To compute areas under the curve, we first **standardize** the data by subtracting off  $\mu$ and then dividing by $\sigma$ : 
	$\large z = \large\frac{x-\mu}{\sigma}$
$z$ is called the **standardized value** or **z-score**
$z$ has no unit (where, $x, \mu, \sigma$ can have units)

Ex: $z = 2$ means the data point$(x)$ is 2 standard deviations$(2\sigma)$ above average$(\mu)$

The z-score shows the number of standard deviations a given data point lies from the mean. So, standard deviation must be calculated first because the z-score uses it to communicate a data point's variability.

> [!note]
> Standardized data has mean 0 and standard deviation 1.
> Once standardized, the data distribution has a **standard normal curve** (see image above) given by the equation $y = \frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}x^2}$

## Normal approximation
Finding the probable percentage of population by finding the areas under the curve is **normal approximation**

>[!example]
> Given a data of father's heights follows a normal distribution with a mean of 68.3 in and a standard deviation of 1.8 in.
> What percentage of fathers have heights between 67.4 in and 71.9 in?

### Step 1: Standardize
	$z_1 = \large\frac{67.4 in - 68.3 in}{1.8 in} = -0.5$
	$z_2 = \large\frac{71.9 in - 68.3 in}{1.8 in} = 2$

### Step 2: Mark the area under the normal curve
![[Pasted image 20230518001713.png]]

### Step 3: Once we have the z-scores, we look up areas from the Z-score table
Z-score table has entries that denote the area under the curve *below/to the left of* the corresponding $z$ value 
![[Pasted image 20230518002026.png]]
![[Pasted image 20230518002039.png]]
![[Pasted image 20230518002047.png]]
From the table above, we can calculate the area under the curve between the $z$-scores $(-0.5, 2)$ by subtracting the area to the left of $z=-0.5$ from the area to the left of $z=2$
	$Area(z=(0.5,2)) = Area(2) - Area(-0.5)$
![[Pasted image 20230518002442.png]]
Percentage of fathers with height between (67.4 in, 71.9 in) 
$=0.9772 - 0.3085 = 66.87\%$
> [!note]
> Empirical rule is just a special case of normal approximation.

## Computing Percentiles with the Normal Approximation

What is the 30th percentile of fathers' heights?
![[Pasted image 20230518010938.png]]

From the table, we can find the $z$ value with 30% to be: $z = -0.52$

From the standardization formula, we solve for $x = \mu + z\sigma$
Or: $z = -0.52$ means that the height is 0.52 standard deviations below average.
Solving $x$ gives us $x=67.364$

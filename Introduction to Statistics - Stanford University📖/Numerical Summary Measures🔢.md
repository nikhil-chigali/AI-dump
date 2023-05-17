Use mean and median for summarizing data with only one number.
* **Mean** is simply the average of all the data points
* **Median** is the number that is larger than half the data and smaller than the other half

Consider the following histogram, where area corresponds to percentage:
![[Pasted image 20230516144805.png]]
Median is marked at $50,000 where half the area of the histogram is below $50,000 and half the area is above it.

> [!note]
> Mean and Median are the same when the histogram is symmetric
> ![[Pasted image 20230516145950.png]]

A histogram which is longer on the right is said to be *skewed* to the right. In such histograms, the mean can be much larger than the median. 
A histogram which is longer on the left is said to be *skewed* to the left. In such histograms, the mean can be much smaller than the median.
![[Pasted image 20230516150320.png]]
**For such skewed histograms, it is better to use MEDIAN**

### Quartiles
**1st Quartile** ⇾ 25th Percentile of the data
**Median** (**2nd Quartile**) is simply the 50th Percentile of the data
**3rd Quartile** ⇾ 75th Percentile of the data

> [!example]
> **How would you describe the 25th percentile on the example of household income, if you know that the 25th percentile corresponds with a specific number X?**
	25% of the households have income less than X, and 75% of the households have income greater than X

## Five-number summary

![[Descriptive Statistics and Visualizing Information 📊#^b347e4]]

There are two ways to describe a data distribution:
### 1. Mean and Standard Deviation
Mean gives the average of the data, denoted by $\large \bar{x}$.
Standard deviation gives the spread of the data. It's the root of mean of deviations of all data points from its mean raised to the power of 2.

$\large s = \sqrt{\frac{1}{n}{\Sigma_{i=1}^{n}(x_i-\bar{x})^2}} or \sqrt{\frac{1}{n-1}{\Sigma_{i=1}^{n}(x_i-\bar{x})^2}}$
> [!example]
> Assuming we have data including house prices in some particular city, we could potentially use the standard deviation for the following:
> 1. to know how different the prices in the particular city are
> 2. to know whether all the prices are around the average
> 3. looking at two parts of the city, you notice that the average price is actually the same. You would like to know if the data also looks the same / similarly

Both $\bar{x}$ and $s$ are sensitive to a few large or small data points.

### 2. Median and Interquartile Range
Optimal when you are dealing with skewed data. 
Median gives the center point of the data and Interquartile range gives the data between Q1 and Q3
Mean and Interquartile range are not sensitive to outliers in data.

> [!note]
> When each data point in a distribution is increased/decreased by $x\%$, then the mean, Standard Deviation, Median, and InterQuantileRange will also be scaled by $x\%$.
> If each data point is increased/decreased by a constant $x$, then mean and median will also change by the same amount. However, standard deviation and IQR will remain unchanged.


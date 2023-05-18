## Conditional Probability

![[Algebra#Probability Rule 7 (Conditional Probability Rule)]]
This gives us the General Multiplication rule:
![[Algebra#Probability Rule 8 (General Multiplication Rule)]]

In the special case where A and B are independent, 
P(B | A) = P(B)
Hence, P(A and B) = P(A) * P(B)

> [!example]
> Given, 
> 	P(word 'money' appears in the email | email is *spam*) = 8%
> 	P(word 'money' appears in the email | email is *ham*) = 1%
> 	P(email is *spam*) = 20%
> What is the probability that 'money' appears in an email?
> i.e., P(word 'money' appears in the email)
> 	= P(money appears)
> 	= P(money appears and *spam*) **or** P(money appears and *ham*)
> 	\[Since both the above events are mutually exclusive]
> 	= P(money appears and *spam*) **+** P(money appears and *ham*)
> 	= P(money appears | *spam*) * P(*spam*) **+** P(money appears | *ham*) * P(*ham*)
> 	= P(money appears | *spam*) * P(*spam*) **+** P(money appears | *ham*) * (1- P(*spam*))
> 	= 0.08 * 0.2 + 0.01 * (1 - 0.2)
> 	= 2.4 %

![[Algebra#Bayes' Rule🅱️]]

> [!example]
> Companies usually use the above example calculations to build spam filters.
> But a more practical statistic to for us would be knowing 
> 	P(email is spam | money appears in email)
> Applying Bayes rule,
> 	P(*spam* | money) = P(money | *spam*) P (spam) / P(money)
> 	= 0.08 x 0.2 / 0.024 = 67%

> [!tip] Bayes' formula
>$P(B \mid A) =\large \frac{P(A \mid B) P(B)}{P(A)}$

usually, P(A) in the denominator is not given to us, and we derive it similarly as done in `Example 1`. If we plug it into Bayes' formula, we get the expanded version of Bayes' rule:

> [!tip] Bayes' formula
> $P(B \mid A) =\large \frac{P(A \mid B) P(B)}{P(A \mid B) P(B) + P(A \mid \bar{B}) P(\bar{B})}$

## Bayesian Analysis

The above examples are good examples of Bayesian analysis.
In Bayesian Analysis, 
* We have a **Prior Probability** \[*P(spam)=20%* in our example].
* The idea is to look for **evidence** \[presence of keywords like "money"] and improve the **prior probability** using that evidence
> [!note]
> Bayesian analysis helps us improve or update the **prior probability** into what's called a **posterior probability** that incorporates the **evidence** we have. 

>[!example] False Positives
> 1% of the population has a certain disease. If an infected person is tested, then there is a 95% chance that the test is positive. If the person is not infected, then there is a 2% chance that the test gives an erroneous positive result ('false positive')
>Given that a person tests positive, what are the chances that he has the disease?
>> Know ➡️ P(D) = 1% ; P(+|D) = 95% ; P(+|no D) = 2%
>> Want  ➡️ P(D|+) = ?? *(Good application of Bayes' rule that allows us to flip the conditions around)*  
>> P(D|+) = P(+|D)P(D) / P(+) 
>> *We don't know the denominator, hence we'll use the expanded version of Bayes' rule*
>> P(D|+) = P(+|D)P(D) / (P(+|D)P(D)+P(+|no D)P(no D)) = 32.4%
>
>We got a low probability of **32.4%** that a person is infected given test shows positive though the test detects a positive person 95% of the time because, the population that's actually infected is only 1%.

>[!example] Case Study: Warner's randomized response model
>What % of students have cheated during exam in college?
>Problem: Students might be too embarrassed to answer truthfully.
>**Randomization comes to rescue:**
>We do a survey that first instructs students to toss a coin twice. If the student gets 'tails' on the first toss, then the student has to answer Q1, otherwise the student answers Q2.
>Q1: *Have you ever cheated on an exam in college?*
>Q2: *Did you get 'tails' on the second toss?*
>So the answer will be partly random: We don't know whether a 'yes' answer is due to the student cheating or getting tails on the second toss. This should put the student at ease to answer truthfully.
>Key point: While we don't know what an individual 'yes' means, we can estimate the proportion of cheaters using all the answers collectively:
>P(yes) = P(yes and Q1) + P(yes and Q2)
>P(yes) = P(yes | Q1)P(Q1) + P(yes | Q2)P(Q2)
>Solve for P(yes | Q1) = (P(yes) - P(yes | Q2) P(Q2)) / P(Q1)
>In one survey, 27 students answered 'yes' and 30 answered 'no'
>So we estimate P(yes) = 27/(27+30) = 47%, and get 
>P(yes | Q1) = (0.47 - 0.5 * 0.5) / 0.5 = 44%


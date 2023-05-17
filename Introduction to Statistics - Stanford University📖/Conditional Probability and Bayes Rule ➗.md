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

Bayes' formula,

$P(B \mid A) =\large \frac{P(A \mid B) P(B)}{P(A)}$

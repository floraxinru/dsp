[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> Exercise 5.1 

>> In the BRFSS (see Section 5.4), the distribution of heights is
roughly normal with parameters mu = 178 cm and sigma = 7.7 cm for men. In order to join Blue Man Group, you have to be male between 5'10" and 6'1" (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.

```
import scipy.stats
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
type(dist)
dist.mean(), dist.std()
#How many people are more than one standard deviation below the mean? About 16%
dist.cdf(mu-sigma)

#How many people are between 5'10" and 6'1"?
# Solution 
#first convert from inches to cm
ft = 5
inch = 10
ft_to_cm1 = ft*12*2.54
in_to_cm1 = inch*2.54
#can improve code by defining a function for this
lower=ft_to_cm1+in_to_cm1
ft2 = 6
inch2 = 1
ft_to_cm2 = ft2*12*2.54
in_to_cm2 = inch2*2.54
upper=ft_to_cm2+in_to_cm2
```
lower = 177.8, upper = 185.42
```
#find how many sigmas away are the upper and lower cutoffs
1-((185.7-upper)/sigma)

>0.9636363636363635
```


The upper cutoff for Blue Man Group is about 0.9636 sigmas above the mean
```
(178.0-lower)/sigma

>0.025974025974024498
```

Similarly, the lower cutoff is about 0.02597 sigmas below the mean

```
dist.cdf(mu+(0.02597+0.9636)*sigma)
>0.83880783027039496
```

So about 83.9% of US male population are in the height range to join for the Blue Man Group.

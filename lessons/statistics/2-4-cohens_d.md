[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

**Cohen effect size** is *the difference in means expressed in number of standard deviations*

(Book exercise 2.4:) Using the variable `totalwgt_lb`, investigate whether first babies are lighter or heavier than others. 

Compute Cohen’s effect size to quantify the difference between the groups.  How does it compare to the difference in pregnancy length?

```

from __future__ import print_function, division #future?

%matplotlib inline

import numpy as np

import nsfg
import first


#using the function defined in the book that computes the Cohen effect size:
def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d
    

first_lb = firsts.totalwgt_lb
others_lb = others.totalwgt_lb
CohenEffectSize(first_lb, others_lb)


>>> -0.088672927072602006
```
Because Cohen's d is the difference between the two means divided by the pooled standard deviation, and the result is negative, we know the first babies are lighter than others.

The absolute value of Cohen's effect size for totalwgt_lb is more than three times as large as the effect size in pregnancy length between first babies and others (0.028879044654449883). In other words, the difference in total weight has a larger effect than the difference in pregnancy length.

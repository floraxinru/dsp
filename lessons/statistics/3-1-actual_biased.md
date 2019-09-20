[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

```
resp = nsfg.ReadFemResp()
numkdhh = resp.numkdhh

#actual distr
pmfkd = thinkstats2.Pmf(numkdhh, label='actual_kids')

#biased distr, if ask kids how many kids there are in their households, using BiasPmf defined earlier
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x) 
        #For each household with x children, we multiply the probability by x, the number of children in that household
        
    new_pmf.Normalize()
    return new_pmf
biased_pmfkd = BiasPmf(pmfkd, label= 'observed_kids')

#plots
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmfkd, biased_pmfkd])
thinkplot.Config(xlabel='Num_Kids_per_HH', ylabel='PMF')

#compute means for each
print('Actual mean', pmfkd.Mean())
print('Observed mean', biased_pmfkd.Mean())

```
![Image of actual and biased pmfs](https://github.com/floraxinru/dsp/blob/master/lessons/statistics/3-1kids.png)


Actual mean 1.02420515504
Observed mean 2.40367910066

So the actual mean for number of kids per household is 1, and the observed mean is more than double of the actual mean (about 135% higher).

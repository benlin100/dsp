# Statistics

# Table of Contents

[1. Introduction](#section-a)  
[2. Why We Are Using Think Stats](#section-b)  
[3. Instructions for Cloning the Repo](#section-c)  
[4. Required Exercises](#section-d)  
[5. Optional Exercises](#section-e)  
[6. Recommended Reading](#section-f)  
[7. Resources](#section-g)

## <a name="section-a"></a>1.  Introduction

[<img src="img/think_stats.jpg" title="Think Stats"/>](http://greenteapress.com/thinkstats2/)

Use Allen Downey's [Think Stats (second edition)](http://greenteapress.com/thinkstats2/) book for getting up to speed with core ideas in statistics and how to approach them programmatically. This book is available online, or you can buy a paper copy if you would like.

Use this book as a reference when answering the 6 required statistics questions below.  The Think Stats book is approximately 200 pages in length.  **It is recommended that you read the entire book, particularly if you are less familiar with introductory statistical concepts.**

Complete the following exercises along with the questions in this file. Some can be solved using code provided with the book. The preface of Think Stats [explains](http://greenteapress.com/thinkstats2/html/thinkstats2001.html#toc2) how to use the code.  

Communicate the problem, how you solved it, and the solution, within each of the following [markdown](https://guides.github.com/features/mastering-markdown/) files. (You can include code blocks and images within markdown.)

## <a name="section-b"></a>2.  Why We Are Using Think Stats 

The stats exercises have been chosen to introduce/solidify some relevant statistical concepts related to data science.  The solutions for these exercises are available in the [ThinkStats repository on GitHub](https://github.com/AllenDowney/ThinkStats2).  You should focus on understanding the statistical concepts, python programming and interpreting the results.  If you are stuck, review the solutions and recode the python in a way that is more understandable to you. 

For example, in the first exercise, the author has already written a function to compute Cohen's D.  **You could import it, or you could write your own code to practice python and develop a deeper understanding of the concept.** 

Think Stats uses a higher degree of python complexity from the python tutorials and introductions to python concepts, and that is intentional to prepare you for the bootcamp.  

**One of the skills to learn here is to understand other people’s code.  And this author is quite experienced, so it’s good to learn how functions and imports work.**

---

## <a name="section-c"></a>3.  Instructions for Cloning the Repo 
Using the [code referenced in the book](https://github.com/AllenDowney/ThinkStats2), follow the step-by-step instructions below.  

**Step 1. Create a directory on your computer where you will do the prework.  Below is an example:**

```
(Mac):      /Users/yourname/ds/metis/metisgh/prework  
(Windows):  C:/ds/metis/metisgh/prework
```

**Step 2. cd into the prework directory.  Use GitHub to pull this repo to your computer.**

```
$ git clone https://github.com/AllenDowney/ThinkStats2.git
```

**Step 3.  Put your ipython notebook or python code files in this directory (that way, it can pull the needed dependencies):**

```
(Mac):     /Users/yourname/ds/metis/metisgh/prework/ThinkStats2/code  
(Windows):  C:/ds/metis/metisgh/prework/ThinkStats2/code
```

---


## <a name="section-d"></a>4.  Required Exercises

*Include your Python code, results and explanation (where applicable).*

### Q1. [Think Stats Chapter 2 Exercise 4](statistics/2-4-cohens_d.md) (effect size of Cohen's d)  
Cohen's D is an example of effect size.  Other examples of effect size are:  correlation between two variables, mean difference, regression coefficients and standardized test statistics such as: t, Z, F, etc. In this example, you will compute Cohen's D to quantify (or measure) the difference between two groups of data.   

This is my Python Code:  
#read the data file and and create a new dataset, live, that only has live birth data   
preg = ReadFemPreg()  
live = preg[preg.outcome == 1]  
  
  
#split my dataset into 2 groups - firstborn and not firstborn  
firsts = live[live.birthord == 1]  
others = live[live.birthord != 1]  


#Created two Hist objects with respect to totalwgt_lb  
firstborn_weight = thinkstats2.Hist(firsts.totalwgt_lb)  
others_weight = thinkstats2.Hist(others.totalwgt_lb)  


#graph the histogram  
width = 0.05  
thinkplot.PrePlot(2)  
thinkplot.Hist(firstborn_weight, align='left', width=width)  
thinkplot.Hist(others_weight, align='right', width=width)  
thinkplot.Show(xlabel='lbs', ylabel='frequency', xlim=[2, 12])  


#hard to deduce from histogram, now calculate the mean and variance  
first_mean = firsts.totalwgt_lb.mean()  
other_mean = others.totalwgt_lb.mean()  
first_var = firsts.totalwgt_lb.var()  
other_var = others.totalwgt_lb.var()  
print(first_mean)  
print(other_mean) ###non-newborn babies are born a little heavier than first born (appx: .124 lbs heavier)  

#now calculate Cohen's d:  
group1 = firsts.totalwgt_lb  
group2 = others.totalwgt_lb  
print(CohenEffectSize(group1, group2))  

My answers:  
first_mean = 7.201094430437772  
other_mean = 7.325855614973262  
Cohen's d = -0.088672927072602  

According to the calculations, non-newborn babies are born a little heavier than first born babies (appx: .124 lbs heavier). Cohen's D is about -0.0887 (the - sign means that we see an increase in weight from group 1 (firstborn) to group 2 (non firstborn). A value of ~0.09 is relatively very low so it most likely has a small effect size. We can compare this to the effect size of mean pregnancy length which was 0.029. So the effect size for weight is relatively larger than the effect size for length, but the effect size overall for both is still small.


### Q2. [Think Stats Chapter 3 Exercise 1](statistics/3-1-actual_biased.md) (actual vs. biased)
This problem presents a robust example of actual vs biased data.  As a data scientist, it will be important to examine not only the data that is available, but also the data that may be missing but highly relevant.  You will see how the absence of this relevant data will bias a dataset, its distribution, and ultimately, its statistical interpretation.

  
resp = nsfg.ReadFemResp()  
resp.numkdhh  
#actual  
actual_pmf = thinkstats2.Pmf(resp.numkdhh, label='actual')  
mean = actual_pmf.Mean()  
print(mean)  

#biased  
bias_pmf = BiasPmf(actual_pmf, label='biased')  
biased_mean = bias_pmf.Mean()  
print(biased_mean)  

#plot both distributions  
thinkplot.PrePlot(2)  
thinkplot.Pmfs([actual_pmf, bias_pmf])  
thinkplot.Show(xlabel='num_of_children', ylabel='PMF')  

![Plots of Both Distributions]
(https://github.com/benlin100/dsp/blob/master/ben.png)  
actual_mean = 1.02420515504  
biased_mean = 2.40367910066  

The results show that, in the biased distribution there is a much higher probability to have a higher number of children than lower. The   mean of the biased distribution is 2.4, more than 50% higher thin the actual mean.   

### Q3. [Think Stats Chapter 4 Exercise 2](statistics/4-2-random_dist.md) (random distribution)  
This questions asks you to examine the function that produces random numbers.  Is it really random?  A good way to test that is to examine the pmf and cdf of the list of random numbers and visualize the distribution.  If you're not sure what pmf is, read more about it in Chapter 3.  

Here's my code:  
t = np.random.random(size = 1000)  

#pmf  
pmf = thinkstats2.Pmf(t)  
thinkplot.Pmf(pmf, linewidth = 0.1)  
thinkplot.Show(xlabel='value')  

#cdf  
cdf = thinkstats2.Cdf(t)  
thinkplot.Cdf(cdf)  
thinkplot.Show(xlabel='value', ylabel='CDF')  

Yes, it really is random. From the pmf, we can see that regardless of what the value is, their probabilties are all set to 0.001. Each value in the range has an equal chance of showing up. Now looking at the CDF, we see the same results. The CDF shows a diagonal line that looks to have an approximate slope of 1. This means that percentile rank is going to follow a uniform distribution and that the model is going to assume that every value from 0 to 1 is going to have the same likelihood. For example, if you choose a value of 0.5, because all the values have the same probablitiy, we can expect that 0.5 has a percentile rank of 50%. Same with 0.1, we an expect 0.1 to have a percentile rank of 10%. 





### Q4. [Think Stats Chapter 5 Exercise 1](statistics/5-1-blue_men.md) (normal distribution of blue men)
This is a classic example of hypothesis testing using the normal distribution.  The effect size used here is the Z-statistic. 

To start, I created a normal distribution with scipy.stats.norm with the mean of 178 and SD of 7.7. Now I just used the Cdf function to calculate the percentile rank of the heights of both 5'10 and 6'1. I then subtracted the two values to get the approximate percentage of the population that is between the listed heights.  

Here is my code:  

import scipy.stats  
height = scipy.stats.norm(loc=178, scale=7.7) #created the normal distribution  
height.cdf(177.8) #calculated the percentile rank of 5'10  

  
height.cdf(185.42) #calculated the percentile rank of 6'1  

height.cdf(185.42) - height.cdf(177.8) #subtracted the two percentile ranks together  

The answer is ~34% of the male population has a height between 5'10 and 6'1. 





### Q5. Bayesian (Elvis Presley twin) 

Bayes' Theorem is an important tool in understanding what we really know, given evidence of other information we have, in a quantitative way.  It helps incorporate conditional probabilities into our conclusions.

Elvis Presley had a twin brother who died at birth.  What is the probability that Elvis was an identical twin? Assume we observe the following probabilities in the population: fraternal twin is 1/125 and identical twin is 1/300.  

The answer is 5/11. This is how I got to that conclusion:  

So I calculated the likelihood that his twin brother was a male and it was an identical twin. So first, I made the two probablities equivalent with the same denominator. So for identity, it is 10/3000 (10 twin babies for 3000 births. And for fraternal, 125/3000 (125 fraternal twins for 3000 babies. So we can assume that for the twins, half are going to be girls and half will be boys. We already know the deceased baby is a boy, so that value is 5. Now, we look at fraternal. There are 4 different possible combinations of boy/girl, so the possibility of having a boy-boy is 6/24. So in total, there are 11 chances that he had a twin brother. But we already knew that. The question then lies as to whether the boy was a fraternal or identical twin. In this case, that probability is 5/11. 

---

### Q6. Bayesian &amp; Frequentist Comparison  
How do frequentist and Bayesian statistics compare?

>> REPLACE THIS TEXT WITH YOUR RESPONSE

---

## <a name="section-e"></a>5.  Optional Exercises

The following exercises are optional, but we highly encourage you to complete them if you have the time.

### Q7. [Think Stats Chapter 7 Exercise 1](statistics/7-1-weight_vs_age.md) (correlation of weight vs. age)
In this exercise, you will compute the effect size of correlation.  Correlation measures the relationship of two variables, and data science is about exploring relationships in data.    

### Q8. [Think Stats Chapter 8 Exercise 2](statistics/8-2-sampling_dist.md) (sampling distribution)
In the theoretical world, all data related to an experiment or a scientific problem would be available.  In the real world, some subset of that data is available.  This exercise asks you to take samples from an exponential distribution and examine how the standard error and confidence intervals vary with the sample size.

### Q9. [Think Stats Chapter 6 Exercise 1](statistics/6-1-household_income.md) (skewness of household income)
### Q10. [Think Stats Chapter 8 Exercise 3](statistics/8-3-scoring.md) (scoring)
### Q11. [Think Stats Chapter 9 Exercise 2](statistics/9-2-resampling.md) (resampling)

---

## <a name="section-f"></a>6.  Recommended Reading

Read Allen Downey's [Think Bayes](http://greenteapress.com/thinkbayes/) book.  It is available online for free, or you can buy a paper copy if you would like.

[<img src="img/think_bayes.png" title="Think Bayes"/>](http://greenteapress.com/thinkbayes/) 

---

## <a name="section-g"></a>7.  More Resources

Some people enjoy video content such as Khan Academy's [Probability and Statistics](https://www.khanacademy.org/math/probability) or the much longer and more in-depth Harvard [Statistics 110](https://www.youtube.com/playlist?list=PL2SOU6wwxB0uwwH80KTQ6ht66KWxbzTIo). You might also be interested in the book [Statistics Done Wrong](http://www.statisticsdonewrong.com/) or a very short [overview](http://schoolofdata.org/handbook/courses/the-math-you-need-to-start/) from School of Data.

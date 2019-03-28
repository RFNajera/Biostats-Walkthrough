# Biostats Walkthrough

# Data Source
The State of North Carolina released some data through their vital statistics program that is in a comma-separated values format (.csv) and is [available to download by clicking here](https://www.dropbox.com/s/xzbrkjb6lyek7v7/nc.csv?dl=0).

# Using R
We will be using [R Studio](https://www.rstudio.com/) for this walkthrough, but you can use any software package that uses R with the code we'll be posting here. You can also use other statistical packages (e.g. STATA, SAS, SPSS) by translating the code. The concepts are the same.

### Libraries
For this walkthrough, we will be using several librarires. To load them by checking if you need it, dowloading it if you do, and then load them, use the following code:

```R
if(!require(BSDA)){install.packages("BSDA")}
library(BSDA)
if(!require(dplyr)){install.packages("dplyr")}
library(dplyr)
if(!require(ggplot2)){install.packages("ggplot2")}
library(ggplot2)
if(!require(coin)){install.packages("coin")}
library(coin)
if(!require(pwr)){install.packages("pwr")}
library(pwr)
if(!require(gplots)){install.packages("gplots")}
library(gplots)
if(!require(XNomial)){install.packages("XNomial")}
library(XNomial)
if(!require(ggplot2)){install.packages("ggplot2")}
library(ggplot2)
if(!require(ggpubr)){install.packages("ggpubr")}
library(ggpubr)
```

# Types of Variables
There are two basic types of variables: **Continous** and **Categorical**.

- Continous
  - Continous variables are those that are on the number scale (negative infinity to positive infinity) and have an infinite number of values between two values. For example, the weight of rocks from a quarry can be continous if they're in kilograms (e.g. 1.56 kg) and the differences between them are on the same scale (e.g. 1.56 kg to 5.56 kg have a difference of 4 kg, 4000 g, or 4000000mg).
- Discrete
  - Discrete variables are similar to continous variables except that they have a finite number of values between them. For example, the weight of rocks, but only counted in half kilos (e.g. 1.56 kg to 5.56 kg have a difference of 4 kg or 8 half kilograms).
- Categorical: Ordinal
  - Ordinal variables are those that are in a certain order but do not necessarily have a number associated to them. For example, school education levels are in categories (e.g. elementary, middle school, high school, college, graduate school, doctoral degree) **and** those categories come in that order.
- Categorical: Nominal
  - Nominal variables are those that do not necessarily have a number associated to them, and they are not in any particular order. For example, states in the United States can be nominal in a dataset (e.g. Alaska, Texas, Oklahoma) without one needing to be ahead of the other in the list.
- Dichotomous
  - Dichotomous variables are those that have exactly two possible categories and said categories are not in any order. For example, men and women, up and down, left and right, inside and outside... All of these have two possibilities and there is no one that must come before the other.

# The Central Limit Theorem
When you draw a sample from a population, the average (mean) of that sample will be normally distributed (bell-shaped) around a sample mean that is very close to the mean of the population (usually written as **µ** in statistics). As you increase the sample size, the mean of those samples will still be very close to the mean of the population but the spread of the numbers away from the sample mean (the sample standard deviation) is tighter.

Check out this video on YouTube for more of an explanation:
[![Understanding The Central Limit Theorem](https://img.youtube.com/vi/_YOr_yYPytM/0.jpg)](https://www.youtube.com/watch?v=_YOr_yYPytM)

As the video points out, you can make some inferences on the population based on the sample. Let's practice this with the NC birth data:

### Exercise 1. Draw 500 samples of different sizes from the data and plot the average age of those samples in a histogram.

First, let's look at 500 samples of size n=5:

```R
mu=mean(births$mage) # The mean of the population is the mean of age in the entire dataset
sigma=sd(births$mage) # The standard deviation of the population age
n=5 # Sample size
xbar=rep(0,500) # How many sample means
for (i in 1:500) {xbar[i]=mean(rnorm(n,mean=mu,sd=sigma))} # Loop to do the sampling 500 times
hist(xbar,prob=TRUE,breaks=12,xlim=c(16,40),ylim=c(0,0.25),main = "Histogram of Sample Means (n=5)") #Draw the historgram
```

This gives you the following histogram:

![Histogram for 500 samples of size 5](https://raw.githubusercontent.com/RFNajera/Biostats-Walkthrough/master/histogram_n_5.png)

Run the code above for 500 samples of size 25 each. You should get a histogram that is narrower:

![Histogram for 500 samples of size 25](https://github.com/RFNajera/Biostats-Walkthrough/blob/master/histogram_n_25.png?raw=true)

Run the code above a third time for 500 samples of size 100 each. You should get a histogram that is narrower:

![Histogram for 500 samples of size 100](https://github.com/RFNajera/Biostats-Walkthrough/blob/master/histogram_n_100.png?raw=true)

What do you notice about the width of the histograms as the sample sizes get bigger? Based on these samples, what would you guess the average age of a mother in the 2004 NC births dataset is? What would you guess is the average age of all mothers? What if the sample size were 1,000? (The entire dataset contains 1,000 observations.)

So why did the histograms get narrower? It has to do with the sample standard error of the sample. That standard error (the standard deviation of the sample) is calculated by taking the population standard deviation (sigma) and dividing it by the square of the sample size (n): σ / \sqrt{n}

# Parametric and Non-Parametric Tests

# Looking at Data

### Is It Normally Distributed?

### Are There Outliers?

# Is There an Association?

# A Sample From a Population

# One Sample Z Test

# One Sample t Test

# Comparing the Means of Two Groups

# Comparing the Proportions of Two Groups

# Comparing the Means of Three or More Groups: ANOVA

# Simple Linear Regression

# Multiple Linear Regression

# Logistic Regression

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

- Continuous
  - Continous variables are those that are on the number scale (negative infinity to positive infinity) and have an infinite number of values between two values. For example, the weight of rocks from a quarry can be continous if they're in kilograms (e.g. 1.56 kg) and the differences between them are on the same scale (e.g. 1.56 kg to 5.56 kg have a difference of 4 kg, 4000 g, or 4000000mg).
- Discrete
  - Discrete variables are similar to continous variables except that they have a finite number of values between them. For example, the weight of rocks, but only counted in half kilos (e.g. 1.56 kg to 5.56 kg have a difference of 4 kg or 8 half kilograms).
- Categorical: Ordinal
  - Ordinal variables are those that are in a certain order but do not necessarily have a number associated to them. For example, school education levels are in categories (e.g. elementary, middle school, high school, college, graduate school, doctoral degree) **and** those categories come in that order.
- Categorical: Nominal
  - Nominal variables are those that do not necessarily have a number associated to them, and they are not in any particular order. For example, states in the United States can be nominal in a dataset (e.g. Alaska, Texas, Oklahoma) without one needing to be ahead of the other in the list.
- Dichotomous
  - Dichotomous variables are those that have exactly two possible categories and said categories are not in any order. For example, men and women, up and down, left and right, inside and outside... All of these have two possibilities and there is no one that must come before the other.

# Looking at Data
Before we continue, we need to look at the data in our dataset and understand it.

- Father's age (fage):
- Mother's age (mage):
- Mature (mature):
- Weeks of gestation (weeks):
- Premature birth (premie):
- Visits to physician (visits):
- Marital status (marital):
- Weight gained during pregancy (gained):
- Birth weight (weight):
- Low birth weight (lowbirthweight):
- Baby gender (gender):
- Mom's smoking status (habit):
- Mom's ethnicity (whitemom):

## **For the purposes of this walkthrough, we will call the entire dataset the "population" and samples derived from it will be called "samples."**

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

So why did the histograms get narrower? It has to do with the sample standard error of the sample. That standard error (the standard deviation of the sample) is calculated by taking the population standard deviation (sigma) and dividing it by the square of the sample size (n): σ / √n

As a result, as the sample size (n) gets bigger, the standard error (which determines the spread of the histogram) gets smaller.

# The Assumption of Normality
One of the assumptions made in these statistical tests is that the variable in question is normally distributed. If it is not, we will need to do *non-parametric* tests (which is a whole other walkthrough). One quick way to assess the *normality* of the data is to plot it on a histogram (like we did above) and see the shape.

### Question: Is maternal age normally distributed in the data set (population)?

### Question: Is birth weight normally distributed in the population?

### Question: Is weight gained during pregnancy normally distributed in the population?

### Are There Outliers?

# Is There an Association?

### Question: Is there an association between a baby being born prematurely and the mom being a smoker?

### Question: Is there an association between a baby being born prematurely and the mom being white?

### Question: Is there an association between a mom being white and smoking?

### Question: Is there an assocaition between a baby being born prematurely and the mom being a smoker and white? (The Cochran-Mantel-Haenszel Method)

# Confounding?

### Question: Is smoking habit a confounder of the association between a baby being premature and the mom being white?

# A Sample From a Population

### Let's create two samples: A and B and do some tests...

# One Sample Z Test

### Question: Did sample A come from the dataset?

### Question: What if a sample of six birth weights were, in pounds: 1.25, 4.35, 5.65, 2.33, 4.95, and 6.90. Did this sample come from the population?

# One Sample t Test

### Question: An OB/Gyn says that they helped deliver a child that weighed 12 pounds. What is the probability that a child of that weight was delivered?

### Question: A pediatrician reports that they treated a child that weighed 1.2 pounds. What is the probability that a child of that weight was delivered?

### Question: What is the 95% confidence interval for the mean of the population based on sample B?

# Comparing the Means of Two Groups

### Question: Is the mean age of moms to premature babies different than the mean age of moms to non-premature babies different?

### Question: Is the mean birth weight of premature babies different than the mean birth weight of non-premature babies?

### Question: Is the mean birth weight of babies born to smoking mom different than the mean birth weight of babies born to non-smoking moms?

# Comparing the Proportions of Two Groups

### Question: Is the proportion of male babies from white women different to the proportion of male babies from non-white women?

# Comparing the Means of Three or More Groups: ANOVA

### Question: Is the mean gestation time different between women in their 20s, 30s and 40s?

# Simple Linear Regression

### Question: What is the mean birth weight for babies based on mom's age? Is it significant?

### Question: What is the mean birth weight for babies based on mom's gained weight during pregnancy? Is it significant?

# Multiple Linear Regression

### Question: What is the mean birth weight for babies based on mom's age and how much weight they gained during pregnancy?

# Logistic Regression

### Question: What are the odds of a baby being premature based on mom's age?

### Question: What are the odds of a baby being premature based on mom's weight gain during pregnancy?

### Question: What are the odds of a baby being premature based on mom's smoking habit?

### Question: What are the odds of a baby being premature based on mom's ethnicity?

### Question: What are the odds of a baby being premature based on mom's age, weight gain, smoking habit and ethnicity?

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
There are two basic types of variables: Continous and Categorical.

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

### The Assumption of Normality

### Different Distributions for Different Analyses

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

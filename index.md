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

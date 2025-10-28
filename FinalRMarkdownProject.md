Final R Markdown Report: Asthma and Socioeconomic Factors
================
Emma Shumway
2025-10-28

- [ABSTRACT](#abstract)
- [BACKGROUND](#background)
- [STUDY QUESTION and HYPOTHESIS](#study-question-and-hypothesis)
  - [Question](#question)
  - [Hypothesis](#hypothesis)
  - [Prediction](#prediction)
- [METHODS](#methods)
  - [Analysis 1: Asthma and Poverty
    Level](#analysis-1-asthma-and-poverty-level)
  - [Analysis 2: Asthma and Sex](#analysis-2-asthma-and-sex)
  - [Analysis 3: Asthma and Age](#analysis-3-asthma-and-age)
- [DISCUSSION](#discussion)
  - [Interpretation - Analysis 1](#interpretation---analysis-1)
  - [Interpretation - Analysis 2](#interpretation---analysis-2)
  - [Interpretation - Analysis 3](#interpretation---analysis-3)
- [CONCLUSION](#conclusion)
- [REFERENCES](#references)

# ABSTRACT

This report \_\_\_\_\_.

# BACKGROUND

Here is some background: \_\_\_\_\_.

# STUDY QUESTION and HYPOTHESIS

## Question

How does age, poverty level, and sex each influence an individual’s
susceptibility to asthma?

## Hypothesis

There will be a significant correlation between asthma and age, asthma
and poverty level, but not a very significant correlation between asthma
and sex.

## Prediction

If house finches are acting as important amplifying hosts, locations
with more house finches in the blood host analysis will also be the same
locations with higher positive tests for WNV in mosquito pools.

# METHODS

A t-test will test the significance of asthma being present given
certain factors.

## Analysis 1: Asthma and Poverty Level

## Analysis 2: Asthma and Sex

## Analysis 3: Asthma and Age

``` r
library(ggplot2)

age <- data.frame(category = c(" 0-4", " 5-11", "12-17", "18-24", "25-34", "35-64", "65+"), value = c(1.4, 2.4, 2.0, 3.8, 6.4, 11.5, 27.1))

ggplot(age, aes(x = category, y = value)) +
  geom_bar(stat = "identity", fill = "darkred") + # stat="identity" uses y-values directly
  labs(title = "Asthma Deaths By Age",x = "Age (Years)",y = "Asthma-Related Deaths Per Million")
```

![](FinalRMarkdownProject_files/figure-gfm/age%20and%20deaths-1.png)<!-- -->

# DISCUSSION

## Interpretation - Analysis 1

Insert analysis here.

## Interpretation - Analysis 2

Insert analysis here.

## Interpretation - Analysis 3

Insert analysis here.

# CONCLUSION

The data suggests that \_\_\_\_.

# REFERENCES

1.  Name, etc.

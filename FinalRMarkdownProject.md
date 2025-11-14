Final R Markdown Report: Asthma and Socioeconomic Factors
================
Emma Shumway
2025-11-13

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

Asthma affects over 26 million people in the U.S. (Most Recent Asthma
Data, 2024). The development of asthma is not linked to any single
factor; rather, there have been a variety of genetic and environmental
factors known to be associated with asthma incidence (Khachi et al.,
2014). Effective treatment can only be provided through thorough study
of the underlying causal factors, so it is useful to examine available
data for trends. This report attempts to answer the question: how does
age, poverty level, and sex each influence an individual’s
susceptibility to asthma? It is hypothesized that there will be a
significant correlation between asthma and age, asthma and poverty
level, but not a very significant correlation between asthma and sex. If
each of these factors do influence an individual’s susceptibility to
asthma, this will result in a p-value of \<0.05 after running a t-test.

# STUDY QUESTION and HYPOTHESIS

## Question

How does age, poverty level, and sex each influence an individual’s
susceptibility to asthma?

## Hypothesis

There will be a significant correlation between asthma and age, asthma
and poverty level, but not a very significant correlation between asthma
and sex.

## Prediction

If each of these factors do influence an individual’s susceptibility to
asthma, this will result in a p-value of \<0.05 after running a t-test.

# METHODS

A t-test will test the significance of asthma being present given
certain factors.

## Analysis 1: Asthma and Poverty Level

## Analysis 2: Asthma and Sex

## Analysis 3: Asthma and Age

``` r
library(ggplot2)

age <- data.frame(
  category = c(" 0-4", " 5-11", "12-17", "18-24", "25-34", "35-64", "65+"),
  value = c(1.4, 2.4, 2.0, 3.8, 6.4, 11.5, 27.1)
)

ggplot(age, aes(x = category, y = value)) +
  geom_bar(stat = "identity", fill = "darkred") +
  labs(
    title = "Asthma Deaths By Age Group",
    x = "Age (Years)",
    y = "Asthma-Related Deaths Per Million",
    caption = "Figure 1. Asthma-related deaths in 2021 occurring by age group per million as reported by the CDC."
  ) +
  scale_y_continuous(
    breaks = seq(0, 30, by = 2),  # show numbers every 2 units 
    minor_breaks = seq(0, 30, by = 1)  # add smaller grid lines between major ones
  )
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

1.  Khachi, H., Meynell, H., & Murphy, A. (2014). Asthma:
    Pathophysiology, causes and diagnosis. The Pharmaceutical Journal.
    <https://pharmaceutical-journal.com/article/ld/asthma-pathophysiology-causes-and-diagnosis>

2.  Most Recent Asthma Data. (2024, November 21). CDC.
    <https://www.cdc.gov/asthma-data/about/most-recent-asthma-data.html>

Final R Markdown Report: Asthma Prevalence and Geographic Population
Density
================
Emma Shumway
2025-12-06

- [ABSTRACT](#abstract)
- [BACKGROUND](#background)
- [STUDY QUESTION and HYPOTHESIS](#study-question-and-hypothesis)
  - [Question](#question)
  - [Hypothesis](#hypothesis)
  - [Prediction](#prediction)
- [METHODS and RESULTS](#methods-and-results)
  - [Analysis 1: Asthma Prevalence By U.S.
    State](#analysis-1-asthma-prevalence-by-us-state)
  - [Analysis 2: Asthma Prevalence By U.S.
    Region](#analysis-2-asthma-prevalence-by-us-region)
  - [Analysis 3: Population Density By U.S.
    Region](#analysis-3-population-density-by-us-region)
  - [Analysis 4: Asthma Prevalence and Population
    Density](#analysis-4-asthma-prevalence-and-population-density)
- [DISCUSSION](#discussion)
  - [Interpretation - Analysis 1: Asthma Prevalence By U.S.
    State](#interpretation---analysis-1-asthma-prevalence-by-us-state)
  - [Interpretation - Analysis 2: Asthma Prevalence By U.S.
    Region](#interpretation---analysis-2-asthma-prevalence-by-us-region)
  - [Interpretation - Analysis 3: Population Density By U.S.
    Region](#interpretation---analysis-3-population-density-by-us-region)
  - [Interpretation - Analysis 4: Asthma Prevalence and Population
    Density](#interpretation---analysis-4-asthma-prevalence-and-population-density)
- [CONCLUSION](#conclusion)
- [REFERENCES](#references)

# ABSTRACT

Asthma affects over 26 million people in the United States and is
influenced by a range of genetic and environmental factors.
Understanding geographic patterns in asthma prevalence may help identify
contributing risks and inform targeted public health action. This study
examined whether asthma prevalence differs across U.S. states and
regions and whether these differences are associated with population
density. Asthma prevalence and population density data were compiled
from recent CDC reports and analyzed using spatial visualizations,
summary statistics, ANOVA tests, and a Tukey pairwise comparison. While
asthma prevalence varied among states, no consistent geographic pattern
was apparent. In contrast, prevalence differed significantly across
regions, with the Northeast displaying higher asthma prevalence than the
South, North Central, and West in several pairwise comparisons. The
Northeast also had the highest average population density; however,
neither state nor regional analyses showed a significant relationship
between population density and asthma prevalence. These findings suggest
that asthma prevalence varies by region but is not explained by
population density alone. Additional factors such as demographic or
socioeconomic characteristics may better account for regional
differences. Further research using multi-year datasets and additional
variables is recommended to clarify the underlying drivers of geographic
variation in asthma prevalence.

# BACKGROUND

Asthma affects over 26 million people in the U.S. (Most Recent Asthma
Data, 2024). The development of asthma is not linked to any single
factor; rather, there have been a variety of genetic and environmental
factors known to be associated with asthma incidence (Khachi et al.,
2014). Effective treatment can only be provided through thorough study
of the underlying causal factors, so it is useful to examine available
data for trends. It’s possible that geographic location contribute’s to
an individual’s susceptibility to asthma. This report attempts to answer
the question: do different regions of the U.S. vary in asthma prevalence
and mortality rates? It is hypothesized that regions that are more
densely populated will experience higher rates of asthma due to
pollution from large cities. If this is accurate, we expect statistical
testing to show a significant difference in asthma prevalence between
regions of the U.S. associated with different levels of population
density.

# STUDY QUESTION and HYPOTHESIS

## Question

Do different states and regions of the U.S. vary in asthma prevalence
based on population density?

## Hypothesis

States/regions that are more densely populated will experience higher
rates of asthma due to pollution from large cities.

## Prediction

If this is accurate, it is expected an ANOVA test and/or a Tukey
pairwise comparison will show a significant difference (p-value \<0.05)
in asthma prevalence between states or regions of the U.S., or for the
correlation between population density and geographic area.

# METHODS and RESULTS

The methods were designed to compare and visualize the data through
multiple means. Recent asthma reports from the CDC were collected for
testing (Most Recent Asthma Data, 2024). Asthma prevalence rates between
states and between regions were visualized with maps. Spatial hotspots
for asthma prevalence were assessed for geographic overlap. Then, asthma
prevalence was compared by region with a bar plot. Population denstiy by
region was also compared with a box plot. Whether there was significance
in this data was tested with ANOVA tests and a Tukey pairwise
comparison.

Significant difference was found for asthma prevalence by U.S. regions
resulting in a p-value of 0.0192. Additionally, significance was found
specifically for the Northeast region compared to each other region
individually; South (p-value = 0.00419), North Central (p-value =
0.00558), and West (p-value = 0.02671). A pairwise comparison showed the
Northeast region also had the highest average population density (549
per square mile). Comparisons between the other regions showed no
significant differences. No significance was found in the comparison
between population density and asthma prevalence.

## Analysis 1: Asthma Prevalence By U.S. State

To evaluate whether asthma prevalence differed between U.S. states,
counts for asthma incidence were summarized for each state. Population
density was recorded at the same time to input datasets all at once.
Asthma prevalence was then visualized by U.S. state using a map and a
horizontal barplot to highlight states that potentially have much higher
rates of asthma.

``` r
#Asthma Prevalence By State Map

library(ggplot2)
library(maps)
library(dplyr)

# Map data
states_map <- map_data("state")

# Merge map data with asthma data
map_data <- states_map %>%
  left_join(asthma_data, by = c("region" = "state_lower"))

ggplot(map_data, aes(long, lat, group = group, fill = prevalence)) +
  geom_polygon(color = "gray90", size = 0.3) +  # state borders
  geom_polygon(aes(fill = prevalence), color = "white") +
  coord_fixed(1.3) +
 scale_fill_gradientn(
  name = "Asthma Prevalence (%)",
  colors = c("yellow2", "orange", "red", "red4")
) +
  labs(
    title = "Asthma Prevalence by U.S. State"
  ) +
  theme_void() +
  theme(
    legend.position = "right",
    plot.title = element_text(size = 16, face = "bold"),
    plot.subtitle = element_text(size = 12)
  )
```

<img src="FinalRMarkdownProject_files/figure-gfm/prevalence by state-1.png" style="display: block; margin: auto;" />

![](FinalRMarkdownProject_files/figure-gfm/plot-state-data-1.png)<!-- -->
These plots show that while there are differences between states, there
is not a clear pattern in this distribution. Additional statistical
testing will have to be done to determine significance.

## Analysis 2: Asthma Prevalence By U.S. Region

To evaluate whether asthma prevalence differed between regions of the
U.S., counts for asthma incidence were summarized for each region.
Regions were designated based on U.S. census data. Asthma prevalence was
then visualized by region using a map and a boxplot to highlight regions
that potentially have much higher rates of asthma.

``` r
#U.S. regions based on the census

# Get U.S. states map data
states_map <- map_data("state")

# Create a dataframe of states and their regions
state_regions <- data.frame(
  state = tolower(state.name),
  region = state.region
)

# Merge map data with region info
map_data <- states_map %>%
  left_join(state_regions, by = c("region" = "state"))

# Plot
ggplot(map_data, aes(x = long, y = lat, group = group, fill = region.y)) +
  geom_polygon(color = "white") +
  coord_fixed(1.3) +
  labs(title = "Four U.S. Census Regions",
       fill = "Region") +
  theme_void()
```

![](FinalRMarkdownProject_files/figure-gfm/regions%20by%20color-1.png)<!-- -->

``` r
#states and asthma prevalence boxplot

library(ggplot2)

ggplot(asthma_data, aes(x = region, y = prevalence, fill= region)) +
  geom_boxplot() +
  labs(title = "Asthma Prevalence by U.S. Region",
       x = "Region",
       y = "Asthma Prevalence (%)",
       fill = "Region") +
  theme_minimal()
```

<img src="FinalRMarkdownProject_files/figure-gfm/box plot state vs asthma prevalence-1.png" style="display: block; margin: auto;" />
The boxplot that follows designated region data shows what appears to be
a difference for the northeast region. Additional statistical testing
will have to be done to determine significance.

## Analysis 3: Population Density By U.S. Region

In order to run statistical tests on whether asthma prevalence is
correlated with population density within regions, average population
density by U.S. region was calculated and then visualized with a
boxplot.

``` r
#average population density by region table

# Define custom region lists
west <- c("washington","oregon","idaho","montana","wyoming","utah",
          "nevada","california","arizona","new mexico","colorado")

north_central <- c("north dakota","south dakota","nebraska","kansas","missouri",
                   "iowa","minnesota","wisconsin","illinois","michigan",
                   "indiana","ohio")

south <- c("texas","oklahoma","louisiana","mississippi","arkansas","tennessee",
           "alabama","georgia","florida","south carolina","north carolina",
           "virginia","kentucky","west virginia","maryland","delaware")

northeast <- c("pennsylvania","new jersey","new york","connecticut",
               "rhode island","massachusetts","vermont","new hampshire","maine")

# Assign custom region
asthma_data <- asthma_data %>%
  mutate(
    region_custom = case_when(
      state_lower %in% west ~ "West",
      state_lower %in% north_central ~ "North Central",
      state_lower %in% south ~ "South",
      state_lower %in% northeast ~ "Northeast",
      TRUE ~ NA_character_
    )
  )

# Calculate average population density by region
avg_density_by_region <- asthma_data %>%
  group_by(region_custom) %>%
  summarise(
    avg_population_density = mean(pop_density_sqmile, na.rm = TRUE)
  )

avg_density_by_region
```

    ## # A tibble: 5 × 2
    ##   region_custom avg_population_density
    ##   <chr>                          <dbl>
    ## 1 North Central                  107. 
    ## 2 Northeast                      549. 
    ## 3 South                          204. 
    ## 4 West                            60.0
    ## 5 <NA>                           112.

``` r
#population density by U.S. region

library(ggplot2)

ggplot(asthma_data, aes(x = region, y = pop_density_sqmile, fill= region)) +
  geom_boxplot() +
  labs(title = "Population Density by U.S. Region",
       x = "Region",
       y = "Population Density (square mile)",
       fill = "Region") +
  theme_minimal()
```

<img src="FinalRMarkdownProject_files/figure-gfm/box plot population vs state region-1.png" style="display: block; margin: auto;" />
Again, the northeast appears to have a significantly higher population
density than other region, which is consistent with our hypothesis that
regions with higher rates of asthma have higher densities. However, this
can only be confirmed through statistical testing.

## Analysis 4: Asthma Prevalence and Population Density

Statistical tests could then be run on the collected data. ANOVA tests
were run between the Northwest region (region of interest) and
prevalence, then population density and prevalence, then finally
population density and prevalence by region. A Tukey pairwise comparison
was run between region and prevalence factors to further narrow down
comparison between regions of interest.

``` r
# ANOVA test for region and prevalence, pairwise comparison

# load necessary libraries

library(emmeans)
```

    ## Welcome to emmeans.
    ## Caution: You lose important information if you filter this package's results.
    ## See '? untidy'

``` r
library("car")
```

    ## Loading required package: carData

    ## 
    ## Attaching package: 'car'

    ## The following object is masked from 'package:purrr':
    ## 
    ##     some

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     recode

``` r
# create a linear model for US region and asthma prevalence

m2 <- lm(prevalence ~ region, data=asthma_data) 

# perform statistical test 

Anova(m2) 
```

    ## Anova Table (Type II tests)
    ## 
    ## Response: prevalence
    ##           Sum Sq Df F value Pr(>F)  
    ## region    16.928  3  3.6503 0.0192 *
    ## Residuals 71.109 46                 
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

``` r
summary(m2)
```

    ## 
    ## Call:
    ## lm(formula = prevalence ~ region, data = asthma_data)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -2.8111 -0.7702  0.1231  0.7597  2.7500 
    ## 
    ## Coefficients:
    ##                     Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)          11.7111     0.4144  28.258  < 2e-16 ***
    ## regionSouth          -1.5611     0.5180  -3.013  0.00419 ** 
    ## regionNorth Central  -1.5944     0.5483  -2.908  0.00558 ** 
    ## regionWest           -1.2342     0.5391  -2.289  0.02671 *  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1.243 on 46 degrees of freedom
    ## Multiple R-squared:  0.1923, Adjusted R-squared:  0.1396 
    ## F-statistic:  3.65 on 3 and 46 DF,  p-value: 0.0192

``` r
# pairwise comparison

pairs(emmeans(m2, "region"))
```

    ##  contrast                  estimate    SE df t.ratio p.value
    ##  Northeast - South           1.5611 0.518 46   3.013  0.0211
    ##  Northeast - North Central   1.5944 0.548 46   2.908  0.0276
    ##  Northeast - West            1.2342 0.539 46   2.289  0.1155
    ##  South - North Central       0.0333 0.475 46   0.070  0.9999
    ##  South - West               -0.3269 0.464 46  -0.704  0.8949
    ##  North Central - West       -0.3603 0.498 46  -0.724  0.8871
    ## 
    ## P value adjustment: tukey method for comparing a family of 4 estimates

``` r
#ANOVA Test for population density and asthma prevalence by state

library("car")
library("lme4")

# create a linear model for population density per square mile and asthma prevalence by state

m1 <- lm(prevalence ~ pop_density_sqmile, data=asthma_data)

# perform statistical test

Anova(m1)
summary(m1)
```

``` r
# ANOVA test for population density and asthma prevalence by region

library("car")

region_data <- data.frame(
  region = c("North Central", "Northeast", "South", "West" ),
  density = c(107, 549, 204, 60),
  prevalence = c(10.1, 11.7, 10.2, 10.6))

# create a linear model for average population density per region and asthma prevalence

r1 <- lm(prevalence ~ density, data=region_data)

# perform statistical test

Anova(r1)
summary(r1)
```

The ANOVA test for region vs prevalence showed significant p-values
(0.00419, 0.00558, 0.02671) for the Northeast region compared to the
South, North Central, and West regions respectively. The comparison
between the Northeast region and the South and West regions remained
significant after a Tukey pairwise comparison, while the comparison with
the West region no longer showed significance. The ANOVA tests for
population density vs prevalence by state and population density vs
prevalence by region did not show significant p-values (0.667, 0.1293,
respectively).

# DISCUSSION

Results from this analysis support the hypothesis that rates of asthma
vary by region, but do not support the hypothesis that this variation is
correlated with population density in those regions.

Significant difference was found for asthma prevalence by U.S. regions
resulting in a p-value of 0.0192. A pairwise comparison showed The
Northeast also had the highest average population density (549 per
square mile), which supports the hypothesis that more densely populated
regions have a higher asthma prevalence. Comparisons between the other
regions showed no significant differences. This leads us to conclude
that while there are differences in asthma prevalence by region, it is
inconclusive if it depends on population density. Further studies could
look at other factors, such as age, sex, or race to explain this
difference.

## Interpretation - Analysis 1: Asthma Prevalence By U.S. State

States did not show a clear pattern of difference in asthma prevalence.
This does not support the hypothesis that prevalence varies by state,
but this must be statistically determined.

## Interpretation - Analysis 2: Asthma Prevalence By U.S. Region

Regions, specifically the northeast, did show differences in asthma
prevalence based on visual analysis of the boxplot. The northeast region
had a higher median and spread of prevalence. This supports the
hypothesis that prevalence varies by region, but again, this must be
statistically determined.

## Interpretation - Analysis 3: Population Density By U.S. Region

Regions, once again the northeast, did show differences in population
density based on visual analysis of the boxplot. The northeast having a
higher median and spread for population density than other regions
supports the hypothesis that prevalence varies by region, but this
specific correlation must be statistically determined.

## Interpretation - Analysis 4: Asthma Prevalence and Population Density

The ANOVA test for region vs prevalence showed significance for the
Northeast region compared to the South, North Central, and West regions
respectively. Even after the correction with the Tukey pairwise
comparison, the comparison between the Northeast region and the South
and West regions remained significant, while the comparison with the
West region no longer showed significance. The ANOVA tests for
population density vs prevalence by state and population density vs
prevalence by region did not show significance. These results support
the hypothesis that prevalence varies by region, but cannot conclude
that prevalence varies by state or with population density.

# CONCLUSION

The data suggests that asthma prevalence varies by region of the U.S.,
but not by state. It also suggests that the variation seen by region is
not significantly correlated with the population density of the region.
However, the northeast region is of interest and warrants further
investigation as to the significance seen in its asthma prevalence
variance.

Further investigations could explore additional variables that may be
contributing to individual asthma development, such as socioeconomic
factors like age, sex, or race.

There are limitations with this report. Data was collected from one
source and within only a one year time frame, which may skew results. It
is possible that the arbitary nature of assigning states to regions when
there are much geographic variation across regions may reduce accuracy
when attempting to compare differences in geography.

# REFERENCES

1.  Asthma and Allergy Foundation of America. (n.d.). Air pollution and
    asthma. Asthma & Allergy Foundation of America.
    <https://aafa.org/asthma/asthma-triggers-causes/air-pollution-smog-asthma/>
2.  Most Recent Asthma Data. (2024, November 21). CDC.
    <https://www.cdc.gov/asthma-data/about/most-recent-asthma-data.html>
3.  ChatGPT. OpenAI, version Jan 2025. Used as a reference for
    functions. such as ggplot(), creating the map and troubleshooting
    error messages. Accessed 2025-11-10.
4.  Elias, J. A., Zhu, Z., Chupp, G., & Homer, R. J. (1999, October 15).
    Airway remodeling in asthma. The Journal of Clinical Investigation.
    <https://www.jci.org/articles/view/8124>?..
5.  Khachi, H., Meynell, H., & Murphy, A. (2014). Asthma:
    Pathophysiology, causes and diagnosis. The Pharmaceutical Journal.
    <https://pharmaceutical-journal.com/article/ld/asthma-pathophysiology-causes-and-diagnosis>
6.  Kudo, M., Ishigatsubo, Y., & Aoki, I. (2013, September 9). Pathology
    of asthma. Frontiers.
    <https://www.frontiersin.org/journals/microbiology/articles/10.3389/fmicb.2013.00263/full>
7.  National Heart, Lung, and Blood Institute. (2025). Asthma. U.S.
    Department of Health and Human Services.
    <https://www.nhlbi.nih.gov/health/asthma>
8.  Paciência, I., & Cavaleiro Rufo, J. (2020). Urban-level
    environmental factors related to pediatric asthm… : Porto Biomedical
    Journal.
    <https://journals.lww.com/pbj/FullText/2020/02000/Urban_level_environmental_factors_related_to.2.aspx>
9.  Sockrider, M., & Fussner, L. (2020). What is asthma? \| American
    Journal of Respiratory and Critical Care Medicine.
    <https://www.atsjournals.org/doi/10.1164/rccm.2029P25>
10. Win, P. H., & Hussain, I. (2009, May 22). Asthma triggers: What
    really matters?. Clinical Asthma.
    <https://pmc.ncbi.nlm.nih.gov/articles/PMC7152189/>

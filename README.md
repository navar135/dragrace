# Drag Race

## 1. Research Question

What are you investigating, and why does it matter?

- I am investigating the performance of the contestants of RuPaul's Drag Race. I want to use descriptive statistics to explore which queens are more likely to win a main challenge across seasons. Then I will use hypothesis testing to answer the question: **Are queens from cities with a high queer population more likely to win RuPaul's Drag Race?**
- RuPaul's Drag Race is a reality competition show with 17 seasons aired as of 2025. The show has helped bring queer art, fashion, performance, vernacular, and identity into the mainstream. It has reshaped competition-style reality TV and expanded worldwide with 16 international spin-offs. The show is often cited as a turning point for LGBTQIA+ representation by showcasing queer and drag performers in a celebratory, unapologetic way.
- Unfortunately, we are at a time where queer representation is being stripped away, and we are seeing cancellations of shows with queer characters. However, RuPaul's Drag Race continues to shine a light on the joy, beauty, and heartbreak of what it means to be queer in America. I hope to use the data science methods from this semester to analyze a show that has truly made *Herstory*.
               ![](https://github.com/navar135/dragrace/blob/main/gifs/Drag%20Race%20Mama%20Ru%20GIF%20by%20RuPaul's%20Drag%20Race.gif)  
              
## 2. Hypothesis

State your null and alternative hypotheses clearly:

- **H₀:** Drag queens from areas with a higher queer population are *not* more likely to win a RuPaul's Drag Race episode compared to queens from areas with low queer populations.
- **H₁:** Drag queens from areas with a higher queer population *are* more likely to win a RuPaul's Drag Race episode compared to queens from areas with lower queer populations.

## 3. Data Description

Describe your data sources:

- I will join three datasets. The first contains information about all contestants, the second contains performance results for each episode, and the third contains LGBT population information for U.S. states and metropolitan areas.

### Sources
1. Drag Race data was scraped from the  
   [Drag Race wiki](https://rupaulsdragrace.fandom.com/wiki/RuPaul%27s_Drag_Race_Wiki)  
   by Steven V. Miller:  
   https://github.com/svmiller/dragracer/tree/master?tab=readme-ov-file  
2. LGBT population data comes from the  
   [UCLA School of Law Williams Institute](https://williamsinstitute.law.ucla.edu/publications/lgbt-us-msa/).

### Units of Analysis
1. `rpdr_contep.rda`: (season, episode, contestant)  
2. `rpdr_contestants.rda`: contestant  
3. `lgbt_metro_estimates.csv`: metropolitan statistical area (MSA)

### Observations and Key Variables
| Dataset | Dimensions | Key Variables |
|--------|------------|----------------|
| `rpdr_contep.rda` | 2320 × 11 | contestant, outcome, rank |
| `rpdr_contestants.rda` | 184 × 4 | contestant, hometown |
| `lgbt_metro_estimates.csv` | 55 × 6 | MSA, % LGBT |

### Filtering, Cleaning, and Transformations
1. `rpdr_contep.rda` – none  
2. `rpdr_contestants.rda` – fuzzy matching and hard-coded mapping were used to create an approximate MSA for each hometown. Example: a queen from Brooklyn, NY was mapped to **New York (NY-NJ-PA)**.  
3. `lgbt_metro_estimates.csv` – lowercase conversion; created a binary variable for high queer population density.

## 4. Methods

### Permutation Test
- Test statistic: the difference in the proportion of wins between queens from high queer population areas vs. low queer population areas.
- Null simulation: permute the labels (high vs. low queer density) and compute the statistic across 20,000 simulations.

### Bootstrap Confidence Intervals
Metrics used:
- Mean win rate per group  
- Median win rate per group

### Why CLT Does Not Apply
- The CLT applies to means of large samples.  
- The **median** does not follow the CLT; its sampling distribution is not approximately normal.

## 5. Results

### Observed Statistics
- Observed difference in win rate: **0.04556**  
- P-value (two-sided): **0.004**

### Bootstrap CIs — Mean Win Rate
| high_queer_density | boot_mean | ci_lower | ci_upper | ci_width | se |
|--------------------|-----------|----------|----------|----------|---------|
| 0 | 1.0 | 0.066545 | 0.112640 | 0.046095 | 0.011910 |
| 1 | 0.0 | 0.025617 | 0.063678 | 0.038062 | 0.009712 |

### Bootstrap CIs — Median Win Rate
| high_queer_density | boot_median | ci_lower | ci_upper | ci_width | se |
|--------------------|-------------|----------|----------|----------|---------|
| 0 | 1.0 | 0.00000 | 0.083333 | 0.083333 | 0.033254 |
| 1 | 0.0 | 0.00000 | 0.00000 | 0.000000 | 0.000000 |

## 6. Uncertainty Estimation

- 5,000 bootstrap samples were used.  
- The bootstrap distributions were asymmetric, especially for the median. The assymetry was between the high and low queer density groups. I think this is because there was a high rate of queens who did not win a single challenge in the group with low queer population  
- Interpretation: Even accounting for uncertainty, queens from high-queer-density cities appear to have a different win-rate distribution.

## 7. Limitations

- The major limitation was finding a dataset with enough information on queer population across the country. The dataset I was able to find grouped areas across state lines which also added a layer of challenge. Lastly the dataset of drag queens hometowns with not follow an easy city, state pattern but often used sall towns within a bigger city. I accounted for this by using fuzzy matching on the hometown → MSA mapping. This introduces uncertainty on if the mapping is correct. 
- LGBT population data only covers major MSAs and excludes territories like Puerto Rico from which 9 queens are from.
- Win rate doesn't tell the full story, some queens might have won more challenges but also been more inconsistent in their performances across the season fluctuating from top and bottom. 

## 8. References

- Steven V. Miller’s Drag Race dataset: https://github.com/svmiller/dragracer  
- UCLA Williams Institute LGBT population data: https://williamsinstitute.law.ucla.edu/publications/lgbt-us-msa/   
- Course modules on bootstrap, permutation testing, and CLT
- Article on Drag race impact : https://www.esquire.com/entertainment/a43145366/rupauls-drag-race-legacy/ 

# Drag Race

## 1. Research Question

What are you investigating, and why does it matter?  

- I am investigating the performance of the contestants of RuPaul's Drag race. I want to use descriptive statistics to explore which queens are more likely to win different kinds of challenges. Then I will use hypothesis testing to answer the question Are queens from cities with a high queer population more likely to win RuPaul's drag race?.  
- RuPaul's Drag Race is a reality competition show with 17 seasons aired as of 2025. RuPaul's Drag race has helped bring queer art, fashion, performance, vernacular, and identity to the mainstream eye. RuPaul's Drag Race has reshaped competition style reality TV and has expanded world-wide with 16 international spin offs of the original show. The show has often been reference as a turning point for LGBTQIA+ representation by showcasing queer and drag performers in a celebratory, unapologetic way. Unfortunately, we are at a time where a lot of this representation is being stripped away and we are seeing an increase in show cancellations that showcase queer characters, however, RuPaul's drag race continues to shine a light on the joy, beauty, and heartbreak of what it means to be queer in America. I hope to use the data science methods we learned this semester to shine a light on a show that has made Herstory.  

![](https://github.com/navar135/dragrace/blob/main/gifs/Drag%20Race%20Mama%20Ru%20GIF%20by%20RuPaul's%20Drag%20Race.gif)  

## 2. Hypothesis

State your null and alternative hypotheses clearly and succinctly.  
$H_0$ - Drag Queens from areas with a higher queer population are NOT more likely to win a RuPaul's drag race episode compared to Drag queens from areas with low queer populations.  
$H_1$ - Drag Queens from areas with higher queer population are more likely to win RuPaul's drag race episode compared to queens from areas with lower queer populations.  

## 3. Data Description
Describe your data source(s):  
I will join three dataset the first two hosts information about all the contestants, the secoond dataset has how each contestant performed for each episode of show. The third has LGBT population information for all U.S states. 

* Where it comes from (URL, API, dataset name)
1. The main two datasets containing all drag race data was scraped from the [drag race wiki](https://rupaulsdragrace.fandom.com/wiki/RuPaul%27s_Drag_Race_Wiki) by a fellow drag race fan and academic Steven V. Miller.   
    - https://github.com/svmiller/dragracer/tree/master?tab=readme-ov-file  
2. 2. The second dataset is from the [UCLA School of Law Williams Institute](https://williamsinstitute.law.ucla.edu/publications/lgbt-us-msa/). The link provides the data as a series of tables in pdf format. I converted the first table to a csv for easy import.    

* What each observation represents (unit of analysis)
1. *~/data/rpdr_contep.rda* - the unit of analysis is (season, episode, contestant)
2. *~/data/rpdr_contestants.rda* - the unit of analysis is the contestant
3. *~/data/lgbt_metro_estimates.csv* - the unit of analysis is the (MSA ('metropolitan statistical areas'))

* Number of observations and key variables  
1. *~/data/rpdr_contep.rda* - has 2320 rows × 11 columns. The key variables are contestant, outcome, rank
2. *~/data/rpdr_contestants.rda* - has 184 rows x 4 columns. The key variables are contestant and hometown
3. *~/data/lgbt_metro_estimates.csv* has 55 rows x 6. The key variables are MSA and % lgbt  

* Any filtering, cleaning, or transformation steps  
1. *~/data/rpdr_contep.rda* - None
2. *~/data/rpdr_contestants.rda* - I had to use some hard coding and fuzzy matching techniques to create a lookup column that had the approxiamate MSA of te hometown provided. For example a queen from Brooklyn, NY was matched to MSA = New York (NY,NJ,PA)
3.  *~/data/lgbt_metro_estimates.csv* - all text was converted to lowercase to match other datasets. A binary column that depicts if the MSA is considered to have a high queer population. A number close to the mean was chosen for this cutoff since the dataset depicts the largest metropolitan areas in the country that already have a much higher queer population than the rest of the country so picking a number significantly higher than the mean would be biasing our data to much since we would selecting areas that have almost an outlier high % of queer population compared to the rest of the country.  
  
## 4. Methods

Summarize how you analyzed the data:

* The test statistic for your permutation test  
- The test statistic I used for my permutation test was the difference in the proportion of number of wins each queen had on her season between queens from high queer populations vs low queer populations. 
* How you simulated or resampled under the null hypothesis  
- I conducted a permutation test that shuffled the labels of the queens from low vs high queer populations and compared the difference in win rate over 20,000 simulations
* The metric(s) for which you created bootstrap confidence intervals  
- I used two metrics for the confidence interval the mean and the proportion. 
- For the mean I took the mean win rate in each group 
- For the median I took the median win rate in each group

* Why the CLT does not apply to at least one metric  
- My second confidence interval used the median which does not folllow the central limit theorem since the definition of CLT is for large sample means

## 5. Results

Present your main findings:

* Key summary statistics and visualizations
* Observed test statistic and p-value (if applicable)
    - Observed difference in win rate: 0.04556394126706626
    - P-value (two-sided): 0.004000
* Bootstrap confidence intervals for relevant metrics
| high_queer_density | boot_mean | ci_lower | ci_upper | ci_width | se       |          |
| ------------------ | --------- | -------- | -------- | -------- | -------- | -------- |
| 0                  | 1.0       | 0.088953 | 0.066545 | 0.112640 | 0.046095 | 0.011910 |
| 1                  | 0.0       | 0.043302 | 0.025617 | 0.063678 | 0.038062 | 0.009712 |
  
| high_queer_density | boot_median | ci_lower | ci_upper | ci_width | se       |          |
| ------------------ | ----------- | -------- | -------- | -------- | -------- | -------- |
| 0                  | 1.0         | 0.02478  | 0.00000  | 0.083333 | 0.083333 | 0.033254 |
| 1                  | 0.0         | 0.00000  | 0.00000  | 0.000000 | 0.000000 | 0.000000 |

## 6. Uncertainty Estimation

Discuss your resampling results:

* How many resamples you used
* What the bootstrap or randomization distributions looked like
* How you interpret the interval estimates

## 7. Limitations

Briefly note any limitations in data, assumptions, or methods, including sources of bias or missing data.

## 8. References

List all datasets, tools, libraries, or papers you cited.






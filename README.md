# Drag Race

## 1. Research Question

What are you investigating, and why does it matter?  

- I am investigating the performance of the contestants of RuPaul's Drag race. I want to use descriptive statistics to explore which queens are more likely to win different kinds of challenges. Then I will use hypothesis testing to answer the question Are queens from cities with a high queer population more likely to win RuPaul's drag race?.  
- RuPaul's Drag Race is a reality competition show with 17 seasons aired as of 2025. RuPaul's Drag race has helped bring queer art, fashion, performance, vernacular, and identity to the mainstream eye. RuPaul's Drag Race has reshaped competition style reality TV and has expanded world-wide with 16 international spin offs of the original show. The show has often been reference as a turning point for LGBTQIA+ representation by showcasing queer and drag performers in a celebratory, unapologetic way. Unfortunately, we are at a time where a lot of this representation is being stripped away and we are seeing an increase in show cancellations that showcase queer characters, however, RuPaul's drag race continues to shine a light on the joy, beauty, and heartbreak of what it means to be queer in America. I hope to use the data science methods we learned this semester to shine a light on a show that has made Herstory.  

![](https://github.com/navar135/dragrace/blob/main/gifs/Drag%20Race%20Mama%20Ru%20GIF%20by%20RuPaul's%20Drag%20Race.gif)  

## 2. Hypothesis

State your null and alternative hypotheses clearly and succinctly.
$H_0$ - Drag Queens from cities with a higher queer population are not more likely to win RuPaul's drag race compared to Drag queens from cities with low queer populations.  
$H_1$ - Drag Queens from cities with higher queer population are more likely to win RuPaul's drag race compared to queens from cities with lower queer populations.
## 3. Data Description
Describe your data source(s):  
I will join three dataset the first two hosts information about all the contestants and their performance for each episode of show. The second has population information for different U.S cities  

* Where it comes from (URL, API, dataset name)
1. The main two datasets was scraped from the [drag race wiki](https://rupaulsdragrace.fandom.com/wiki/RuPaul%27s_Drag_Race_Wiki) by a fellow drag race fan and academic Steven V. Miller.   
    - https://github.com/svmiller/dragracer/tree/master?tab=readme-ov-file  
2. The second dataset is from the [UCLA School of Law Williams Institute](https://williamsinstitute.law.ucla.edu/publications/lgbt-us-msa/). The link provides the data as a series of tables in pdf format. I converted the first table to a csv for easy import.    
* What each observation represents (unit of analysis)
* Number of observations and key variables
1. *~/data/rpdr_contep.rda* has 2320 rows × 11 columns where the unit of analysis is (season, episode, contestant)
2. *~/data/rpdr_contep.rda* has 184 rows x 4 columns where the unit of analysis is the contestant
3. *~/data/lgbt_metro_estimates.csv* has 55 rows x 6 columns where the unit of analysis is the (State, MSA('metropolitan statistical areas')) 

* Any filtering, cleaning, or transformation steps




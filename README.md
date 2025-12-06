# Drag Race

## 1. Research Question

What are you investigating, and why does it matter?  

- I am investigating the performance of the contestants of RuPaul's Drag race. I want to use descriptive statistics to explore which queens are more likely to win different kinds of challenges. Then I will use hypothesis testing to answer the question Are queens from cities with a high queer population more likely to win RuPaul's drag race?.  
- RuPaul's Drag Race is a reality competition show with 17 seasons aired as of 2025. RuPaul's Drag race has helped bring queer art, fashion, performance, vernacular, and identity to the mainstream eye. RuPaul's Drag Race has reshaped competition style reality TV and has expanded world-wide with 16 international spin offs of the original show. The show has often been reference as a turning point for LGBTQIA+ representation by showcasing queer and drag performers in a celebratory, unapologetic way. Unfortunately, we are at a time where a lot of this representation is being stripped away and we are seeing an increase in show cancellations that showcase queer characters, however, RuPaul's drag race continues to shine a light on the joy, beauty, and heartbreak of what it means to be queer in America. I hope to use the data science methods we learned this semester to shine a light on a show that has made Herstory.  

![](https://github.com/navar135/dragrace/blob/main/gifs/Drag%20Race%20Mama%20Ru%20GIF%20by%20RuPaul's%20Drag%20Race.gif)  

## 2. Hypothesis

State your null and alternative hypotheses clearly and succinctly.  
$H_0$ - Drag Queens from states with a higher queer population are not more likely to win RuPaul's drag race maxi challenge compared to Drag queens from states with low queer populations.  
$H_1$ - Drag Queens from states with higher queer population are more likely to win RuPaul's drag race maxi challenge compared to queens from states with lower queer populations.
## 3. Data Description
Describe your data source(s):  
I will join three dataset the first two hosts information about all the contestants, the secoond dataset has how each contestant performed for each episode of show. The third has LGBT population information for all U.S states. 

* Where it comes from (URL, API, dataset name)
1. The main two datasets containing all drag race data was scraped from the [drag race wiki](https://rupaulsdragrace.fandom.com/wiki/RuPaul%27s_Drag_Race_Wiki) by a fellow drag race fan and academic Steven V. Miller.   
    - https://github.com/svmiller/dragracer/tree/master?tab=readme-ov-file  
2. The second dataset is from the [Movement Advancement Project](https://www.lgbtmap.org/equality-maps/lgbt_populations) which provides estimate LGBT population information from all 50 States. The link has an option of providing the data as a table which I copied and converted to a csv using Xcel.  

* What each observation represents (unit of analysis)
1. *~/data/rpdr_contep.rda* - the unit of analysis is (season, episode, contestant)
2. *~/data/rpdr_contestants.rda* - the unit of analysis is the contestant
3. *~/data/lgbt_state_estimates.csv* - the unit of analysis is the (State)   

* Number of observations and key variables  
1. *~/data/rpdr_contep.rda* - has 2320 rows × 11 columns. The key variables are contestant, outcome, rank
2. *~/data/rpdr_contestants.rda* - has 184 rows x 4 columns. The key variables are contestant and hometown
3. *~/data/lgbt_state_estimates.csv* has 56 rows x 6. The key variables are State and lgbt_population_density  

* Any filtering, cleaning, or transformation steps  
1. *~/data/rpdr_contep.rda* - none  
2. *~/data/rpdr_contestants.rda* - split hometown column to two columns city and state. There was one entry where a queen had two hometowns one in the UK and one in the US - the US hometown was preserved 
3.  *~/data/lgbt_state_estimates.csv* - all text was converted to lowercase to match other datasets.  




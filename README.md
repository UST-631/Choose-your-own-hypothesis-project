# Screen time vs mood score
## 1. Research Question
Researching the relationship between screen time and impact on mood

## 2. Hypothesis
Null hypothesis: high screen time mood score = low screen time mood score

## 3. Data Description
Describe your data source(s):
* Where it comes from (URL, API, dataset name)
I got this data from the Kaggel website. This dataset was free and publicly posted on there. I downloaded a csv file with the data locally and used that for the project.
  
* What each observation represents (unit of analysis)
Each observation in the dataset represents a single survey respondent. 
  
* Number of observations and key variables
The number of observation at first I thought was 1 million, but after downloading the file, it ended up being 100,001.
The key variables I used in my analysis are "screen_time_hours", "mood_score", and the labeling column created by me "screen_time_label".
  
* Any filtering, cleaning, or transformation steps
I created a new column for labeling "screen_time_hours" to "high", "medium", "low".
I also filtered the data based on those labels to test my hypothesis. I filtered for "high_screen_time_df", and "low_screen_time_df"

## 4. Methods
Summarize how you analyzed the data:
* The test statistic for your permutation test
The difference in mean mood score between the high and low screen time groups.

* How you simulated or resampled under the null hypothesis
I shuffled the new column i created for the labeling of screen_time_hours. (survey['screen_time_label']) Then after shuffling, I took the mean difference in mood score for both high screen_time_label and low screen_time_label.
  
* The metric(s) for which you created bootstrap confidence intervals
The first metric I used for the bootstrap confidence intervals was, median difference in mood score for both high and low screen times.
The second metric I used for the bootstrap confidence intervals was, difference in the proportion of respondents with mood > 8 (high – low)

* Why the CLT does not apply to at least one metric
The CLT does not apply to my median difference metric and for the proportion metric, the CLT can sometimes apply, but I still used bootstrapping so I didn’t have to rely on that assumption.

  
## 5. Results
* Present your main findings:
I compared mood scores between low and high screen time groups. The permutation test showed the observed difference in mean mood between the groups and produced a p-value  of 0.0 based on the shuffled null distribution. For the bootstrap analysis, the 95% CI for the median mood difference was approximately [–2, –1], and the 95% CI for the difference in the proportion of respondents with mood > 8 was roughly [–0.40, –0.39]. These results suggest that higher screen time is consistently associated with lower mood scores.

## 6. Uncertainty Estimation
* Discuss your resampling results:
I used 10,000 resamples for each bootstrap metric.
The bootstrap distribution for the median difference was very discrete, taking mostly values of –2 or –1.
The bootstrap distribution for the proportion difference formed a smooth, bell-shaped curve.
Both confidence intervals suggest that the differences between groups are negative, meaning the high screen-time group tends to report lower mood.

## 7. Limitations
* Briefly note any limitations in data, assumptions, or methods, including sources of bias or missing data.
One I think of is maybe the way I created the bins, with high being from range 8-12 hours of screen time and low being 1-4 hours of screen time. I just went with braking into 3 and labeling which is probably not accurate.

## 8. References
List all datasets, tools, libraries, or papers you cited.
---
Kaggle dataset used for analysis: https://www.kaggle.com/datasets/abhishekdave9/digital-habits-vs-mental-health-dataset/data
Python libraries: pandas, NumPy, matplotlib
Course materials on permutation tests and bootstrapping

**Reminder:** Your README should be clear enough that someone unfamiliar with your
work could understand what you studied, how you analyzed it, and what you found.

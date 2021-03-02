# How different is the economic reality in Republican vs. Democrat states, during Covid?

### Exploratory  analysis of new jobs listings during the 2020 Covid-19 pandemic

#### Project for Galvanize Data Science Immersive, by Mary MacCarthy in Los Angeles¶


### Table of contents: 
1. Introduction
2. The data
3. Hypothesis
4. Data exploration:
    - required libraries
    - data cleaning
    - analysis
    - hypothesis testing
    - conclusion
5. Further exploration
 


### 1. Introduction

Covid-19 arrived at a time when the U.S. was experiencing extreme political division: it was a nation led by a controversial president and a bitterly divided Congress, and daily headlines described and denounced the growing polarization between Americans on the right and the left. 

I'm interested in how this divided political situation, and the actions of U.S. political leaders, affected the economic reality of Americans during the pandemic - a public health crisis that unleashed an economic crisis, and a crisis that of course is still ongoing as we speak. 

I come at this project from the perspective of a seasoned political journalist who has covered economic and political issues in-depth as a national correspondent. 

In order to explore the economic reality of the U.S. during Covid, I searched for data sets containing measures of economic health. I settled on a comprehensive and up-to-date collection of new jobs listings in the U.S., reported daily for every state. My goal was that the data would help me to understand if and to what degree the political leanings of each state affect how well its economy is coping during Covid. 


### 2. The data set 
I based my study on the following data set, which I found via a search on AWS Open Data Registry: Covid Job Impacts - US Hiring Data Since March 1 2020. The data is compiled by Greenwich HR Labor Market Intelligence, a consulting firm focused on labor market issues. The data is updated daily; I used the data starting March 1st and ending October 24. 

The data is made up of seven CSV files, containing daily new jobs listings:
- by day
- by day in each state
- by region in each state on each day
- by industry in each state on each day. 

I was interested primarily in the new jobs listings per day in each state. 

My prior knowledge - from my perspective as a journalist and as a citizen - were the following: 
- We know that employment rates dropped dramatically near the start of the pandemic, when some states enacted shelter-in-place policies.
- We know that some of the most populated Democratic states - such as New York and California - enacted strict lockdowns that lasted many weeks.
- We know that some of the most populated Republican-led states - including Texas and Florida - did not at any point enforce strict shelter-in-place policies. 
    
Based on this prior knowledge, my assumption was that - since the start of the pandemic in March - we will see a a significant difference in the average number of jobs listings in Democrat-led states as compared to Republican-led states. 
    
It's important to mention that I did consider to what degree new jobs listings are considered a useful indicator of economic health. Of course, economists disagree over what indicator or combination of indicators are the best representation of the economic health of a country. In the U.S, the Department of Labor's monthly report which forms the basis of most analysis uses new jobs figures as one of its primary indicators. 


### 3. Hypothesis: 

Null hypothesis:
During the Covid era staring March 1 2020, Republican-led states and Democrat-led states have seen an equal number of new jobs listings. 

Alternative hypothesis:
During the Covid era staring March 1 2020, Democrat-led states have seen a significantly lower average rate of new jobs listings than Republican states.


### 4. Data exploration:


#### I began by importing the libraries I will likely need for calculations and plotting in Python:

- Numpy
- Pandas
- Scipy
- MatPlotLib

#### Next, I cleaned the data. 

Cleaning consisted of the following:

1) I was interested only in the new jobs listings in the 50 U.S. states and Washington D.C., so I removed the overseas territories that were included in the data.

2) I removed "Nan" ("not a number") values when they seemed nonsensical. 

3) I verified that each CSV file I was working with was not missing any data.

4) I looked for the minimum and maximum values in all of the numerical values, to identify any outliers that might need to be removed from the data set. 

5.) Text-cleaning code is below.


#### Recalculation 

In the given data, all numbers are indexed to March 1, 2020 with "1" equalling the number of new jobs listings on that day, and every subequent date calculated as a percentage of 1.

That indexing does not seem like the ideal measurement. A more standard measure would be to measure the daily rate of change, so I recalculated the new josb listings according.y.

#### Analysis
Plots of the national data broken down by Republican and Democrat states show a very similar normal distribution, with nearly-equal means of rate of change of new jobs listings (Republican = 0.23%, Democrat = 0.27%).


<img src="double_histogram.png"/>


The plots and stats suggests that there is very little difference in the mean of new jobs listings, when comparing Republican-led and Democrat-led states. 

Since the data has a fairly normal distribution, I can use a t-test to test my hypothesis, using the standard 0.05 level of significance. 

The p-value, or likelihood that the null hypothesis is true, is .74. In order to reject the null hypothesis, I would have needed a p-value less than or equal to the standard level of significance of 0.05. 

#### Conclusion
I cannot reject the null hypothesis. 


### Why does this matter?
I can conclude that the data shows, overwhelmingly, that there is no significant difference between new jobs listings in Republican-led states as compared to Democrat-led states, during the time period covered by the data. 

Given the political division and economic volatility that have marked the U.S. since March, it's fascinating to see that - according to the analysis here - the economic situtaion as measured by new jobs numbers is nearly identical in both Republican and Democratic states.

As a journalist - what have I learned from this? I've learned that knowing the political leaning of a state should not lead to any quick and easy conclusions about the economic reality of that state. 

More broadly, it's told me that journalists, analysts, and commentators would benefit from questioning some of our most deeply-held and seemingly "informed" assumptions. Political reporting - my own included - often starts by examining what divides us. That's what's easy to see, and it's usually easy to report and easy to comment on. 

Data-driven reporting - even a fairly simple and straightforward analysis - is a useful tool to question our assumptions and create a more informed baseline for political coverage. 
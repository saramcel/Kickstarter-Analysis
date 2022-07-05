# Kickstarting with Excel

## Overview of Project
We will perform an exploratory data analysis of previous Kickstarter campaigns to provide the client with actionable advice for her upcoming campaign.

### Purpose
 The purpose of this challenge is to provide additional information to Louise so that she can make informed decisions about her Kickstarter Campaign.
Specifically, for similar projects (theater plays), we want to know the launch season and the funding goal level that have tended to be the most successful in the past.

## Analysis and Challenges
The analysis was performed on international Kickstarter data gathered from 2010 to 2017. About 63% of the campaigns originated in the US. 
Each of the following graphs provide information from slightly different data sets. The outcomes based on luanch date is an analysis of theater projects (n = 1369) and the analysis of funding goals is based on all theater projects that are classified as plays (n = 1022). 

### Analysis of Outcomes Based on Launch Date
The analysis based on the launch date was accomplished by first converting the launch date into a usable date, then we extracted the year. Then, I created a pivot table with the date and outcomes, which could be filtered by the parent category (theater) and year (all). The outcomes of interest were "successful," "failed," and "canceled." The pivot table showed the frequency of each of these outcomes per month of launch date. For easy comparison, I created a line graph (please find below).
![Launch_Date_vs_Outcomes](link)
The graph shows that, for theater Kickstarters, the cases of failure are about 20-30 behind the cases of success, and this relationship continues from January to April. For launches in May, success cases rise sharply to about 60 cases above failure, and remain higher than failure rates until August, when they return to previous levels. The gap between failure and success narrows in October, and the gap closes almost completely for campaigns launched in December. 
Canceled Kickstarters are about the same all year long with very low case numbers. 

### Analysis of Outcomes Based on Goals
I looked at the frequencies of the same outcomes, only this time for just plays. These were stratified into levels of funding. Please note that the first category range is $998, the next category range is $3999, and the following categories have ranges of $4999 until the final category, which is $50,000 or more. 
The analysis of outcomes based on funding goals was accomplished by using the COUNTIFS function in Excel. This function allows the user to input different arrays and their criteria, and together these function as multiple "AND" statements, which can dig down into specific information. For example, please see code below.

```
=COUNTIFS(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, "<1000",Kickstarter!$R:$R, "plays")
```
This function looks at columns F, D, and R in the Kickstarter worksheet, and counts only rows that were "successful," have goals less than $1000, and are "plays."

The COUNTIFS function can be used with an additional argument to pinpoint categories of goals.

```
=COUNTIFS(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D, ">=1000", Kickstarter!$D:$D, "<4999", Kickstarter!$R:$R, "plays")
```
This time, the D column needs to meet two criteria--it needs to be equal or more than $1000, and less than $4999. 

The following is a graph of the outcome frequencies by goal category. 
![Goals_vs_Outcomes](link)
This graph shows the percentage of successful and unsuccessful plays by funding goal range. Because these are proportions, these lines can be expected to be mirror images. Please note that this data is positively skewed, meaning that most of it is in the bottom ranges, and therefore the higher ranges should be interpreted with caution.
The proportion of successfully funded plays is highest in the lowest range, and decreases steadily until the $20,000 to $29,999 range, when the percent success rate dips below 50%. The cases that exist in and after this category compose only about 4% of the data, so the remainder of the graph is not necessarily meaningful.
 
### Challenges and Difficulties Encountered

I faced challenges in the Outcomes Based on Goal deliverable, because I had started copying over my functions without ensuring they had absolute references to each column ($).
Further, I did not include the equal sign in the second argument of the function, which meant I was missing some data when my frequencies were tallied. I was able to double-check by filtering the dataset and finding out that yes, the data was there, but no, I was not capturing it, and then I could speculate as to the reason why. 

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
  1. There seems to be a better chance of success for campaigns launched in May, June, or July. 
  2. I would advise against launching a new campaign after October, especially in December. 
- What can you conclude about the Outcomes based on Goals?
  1. Kickstarters with lower funding goals are more likely to be successful. In this analysis, funding goals lower than $4999 seemed to have the greatest rate of success. 
- What are some limitations of this dataset?
  - The dataset does not show what happened to promote the campaigns outside of the Kickstarter platform.
  - The dataset does not permit analysis of the distribution of pledges per campaign, so it is not possible to advise on market segmentation (e.g. target many smaller donations vs few large donations).
- What are some other possible tables and/or graphs that we could create?
  - We could examine whether being selected as a "Staff pick" made any difference in success of the campaign by checking the proportion of success and failure.
  - We could drill down deeper into the Outcome based on Goals data to determine exactly the level at which success starts to drop off. This could be a line graph with more finely sliced categories in the lower ranges of the funding goal.

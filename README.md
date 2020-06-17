
## Problem Statement:

Every year, large and small media outlets run articles discussing the relative performance of students from different states on college prep exams. A state in the top 5 ranking for average test scores can earn positive media coverage, but how accurately do these averages convey quality of state education systems. We explore the relationship between participation rates and state averages, documenting the systematic bias introduced by state policies regarding test participation. Specifically, we explore how expanding test access can drive down state averages as more mid-tier students participate compared to low-participation states where only the most elite students self-select into test participation.



## Executive Summary

We find that on average, a 10 percentage point increase in student participation on the ACT correlates with a 0.5 point decrease in state average ACT composite score. Similarly, we find a 10 percentage point increase in SAT participation correlates with a 21 point drop in state average SAT score. Utilizing a simple linear regression model with state participation rates, we find participation rates alone explain over 70% of the variance between state averages on each of these college admissions exams. 

Our univariate linear regression model predicts state average SAT scores with a mean absolute error of 35 points and state average ACT scores with a mean absolute error of 0.9 points. Comparatively, a baseline utilizing national averages alone produces a mean absolute error of 79 points predicting SAT state average and a mean absolute error of 1.8 points predicting ACT state average. thus our single feature of participation rates reduces prediction error by 50%. Utilizing each subject test, we repeat our OLS model and find our conclusions are robust with consistent coefficient estimates across subject test score predictions and find similar R-squared estimates.

Utilizing 3 case studies (Illinois, Colorado, and Rhode Island), we provide evidence of a causal connection by documenting dramatic reductions in state averages following policy changes that shift participation rates upwards by over 25 percentage points. 

Finally, we attempt to improve our linear model of state averages by including state averages for features relating to the quality of the education system for each state, specifically students-per-teacher, spending-per-student, and average teacher salary as a proxy for teacher quality. We find these features provide minimal explanatory power to our models because the participation rate effect dominates. Further, we find the sign of the coefficients for these variables differs when using SAT or ACt as our target variable, suggesting the self-selection of participation in these exams leads to invalid estimates of the qualitative relationship of these state characteristics to test outcomes.



## Conclusion

This repo demonstrates the fundamental flaw in treating state averages as representative of state systems at large when the participants are not randomly selected. The SAT and ACT are just one context where non-random, self-selecting populations generate outcomes that get reported as objective measures to compare states in news media. The ability of a single variable regression model to consistently generate an R-squared over 70 and the case-studies of Colorado, Illinois, and Rhode Island provide strong evidence that state averages on standardized test primarily reflect the testing policies of those states and their subsequent participation rates rather than any meaningful difference in quality of education.



## Contents

The repo contains 4 notebooks, labeled NB1 through NB4 in order of sequence.

NB 1: data_prep.ipynb
- Load Excel Files from the National Center for Education Statistics
- Extract information for state average SAT Scores, ACT Scores, and NAEP Scores
- Extract state spending-per-student, students-per-teacher, and average teacher salary 
- Generate 3 CSV files

NB 2: EDA_state_averages.ipynb
- Identify highest and lowest average states for each test
- Map SAT and ACT scores by state
- Map relative SAT vs ACT participation rates

NB 3: Model_Participation_Impact.ipynb
- Explore correlation of test averages and participation rates
- Model test scores as function of participation rate
- Identify 3 case studies of changes in participation causing changes in state averages

NB 4: Model_Education_Stats.ipynb
- Explore relative state rankings of 3 standardized tests
- Incorporate state education system statistics into model of state average scores



## References

Borg, L. (2018, October 25). With SAT required, R.I. sees jump in participation, decline in scores. The Providence Journal. Retrieved March 25, 2020, from https://www.providencejournal.com/news/20181025/with-sat-required-ri-sees-jump-in-participation-decline-in-scores

Rado, D. (2016, February 11). Illinois moves ahead with new testing plan, replacing ACT with SAT. The Chicago Tribune. Retrieved March 25, 2020, from https://www.chicagotribune.com/news/ct-illinois-chooses-sat-met-20160211-story.html

Whaley, M. (2017, March 6). Colorado juniors face new, revamped college exam in SAT after state dumps rival ACT. The Denver Post. Retrieved March 25, 2020, from https://www.denverpost.com/2017/03/06/colorado-juniors-sat-college-exam/



## Data Sources

All test score averages and state statistics collected from the National Center of Education Statistics' Digest of Education Statistics utilizing the following tables:

Table 226.40 (2018) [link](https://nces.ed.gov/programs/digest/d18/tables/dt18_226.40.asp)<br>
Table 226.60 (2017) [link](https://nces.ed.gov/programs/digest/d17/tables/dt17_226.60.asp)<br>
Table 226.60 (2018) [link](https://nces.ed.gov/programs/digest/d18/tables/dt18_226.60.asp)<br>
Table 208.40 (2018) [link](https://nces.ed.gov/programs/digest/d18/tables/dt18_208.40.asp)<br>
Table 211.60 (2019) [link](https://nces.ed.gov/programs/digest/d19/tables/dt19_211.60.asp)<br>
Table 236.70 (2019) [link](https://nces.ed.gov/programs/digest/d19/tables/dt19_236.70.asp)<br>

Census regions csv file pulled from Chris Halpert's GitHub and verified with U.S. Census. https://github.com/cphalpert/census-regions


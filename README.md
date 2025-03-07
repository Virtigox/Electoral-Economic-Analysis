# Electoral-Economic Analysis
> A data analysis project exploring the correlation between electoral results and economic growth at both the state and national levels.
## NOTE
> - This election analysis is based solely on the popular vote—the total number of votes each candidate received—rather than the Electoral College results. As a result, there may be cases, such as the 2016 election, where a candidate like Hillary Clinton received more popular votes than Donald Trump but still lost due to the Electoral College outcome. While this study is called an "electoral-economic analysis," it focuses on the relationship between popular vote totals and economic indicators across states. The name may be slightly misleading, but the analysis does not take Electoral College outcomes into account.
> - The U.S. President is elected through the Electoral College rather than the popular vote, as established in the Constitution to balance power between states. While the popular vote reflects the total number of ballots cast nationwide, the Electoral College consists of 538 electors allocated based on congressional representation. A candidate must secure at least 270 electoral votes to win. This system is considered legitimate because it reinforces federalism, ensures smaller states have a voice, and encourages candidates to build broad, nationwide coalitions rather than focusing solely on populous areas.

# Cited Datasets
```
U.S. Presidential Election Results (1976–2020)

Author: MIT Election Data and Science Lab
Publisher: Harvard Dataverse
Title: U.S. President 1976–2020
UNF: UNF:6:F0opd1IRbeYI9QyVfzglUw==
Year: 2017
Version: V8
DOI: 10.7910/DVN/42MVDX

```
```
BEA State Annual Summary Statistics

Author: Bureau of Economic Analysis
Publisher: U.S. Department of Commerce
Title: State Annual Summary Statistics: Personal Income, GDP, Consumer Spending, Price Indexes, and Employment
Year: 2023
URL: https://www.bea.gov/
```
# Overview of the Datasets

_BEA State Annual Summary Statistics_:

This dataset provides annual state-level economic indicators, including:
1. Personal income
2. GDP
3. Consumer spending
4. Price indices
5. Employment

_U.S. Presidential Election Results (1976–2020)_:

This dataset captures detailed state-by-state voting results for presidential elections over 44 years, including:
1. Total vote counts
2. Vote percentages
3. Winning candidates

# Project Objective

The goal of this project is to investigate the relationship between a state's economic growth and its voting behavior during presidential elections. Specifically:

1.  Identify key economic indicators (e.g., GDP, employment) that might influence voting outcomes.
2. Explore correlations between economic trends during an administration's term and electoral results in the subsequent election.
3. Analyze and visualize patterns at both the state and national levels to highlight how economic factors shape political preferences.

# Data Visualization of Economic Growth & Election Outcomes in the U.S.
> This project presents a data visualization of all 50 U.S. states, including Washington, D.C., focusing on economic growth trends and electoral outcomes.

**Left Graph: Economic Growth Trends**
> The left graph illustrates economic growth over different presidential terms, highlighting key economic indicators:

1. Real GDP
2. Real Per Capita Personal Income
3. Real Personal Income
4. Real Per Capita PCE (Personal Consumption Expenditures)
5. Real PCE (Personal Consumption Expenditures)
6. Total Employment

**What Does "Real" Mean?**
> "Real" means the values are adjusted for inflation, so they show actual economic growth instead of just rising prices.

> Each data point is associated with the corresponding U.S. president during the given period.

**Right Graph: Popular Vote Outcomes**
The right graph visualizes vote results, showing the vote share received by candidates from the two major political parties:
1. Democratic Party
2. Republican Party
This visualization provides insights into the relationship between economic performance and voting trends across different states.
 
**UNITED STATES**  
![united states](data_image/UNITED%20STATES_economic_and_electoral_analysis.png)
Visualization of each state including District of Columbia will be presented at [`VISUAL_ANALYSIS.md`](VISUAL_ANALYSIS.md)



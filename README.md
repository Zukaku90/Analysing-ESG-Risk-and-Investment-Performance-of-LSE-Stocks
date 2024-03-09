# Analyzing-ESG-Risk-and-Investment-Performance-in-LSE-Stocks
 ## **Overview**
 In this project, I examined the correlation between the Environmental, Social, and Governance (ESG) Risk Score and the performance of securities listed on the London Stock Exchange. The investigation delved into understanding how the ESG Risk Score, which encapsulates various factors related to environmental sustainability, social responsibility, and corporate governance practices, influences the performance of listed securities.
 
## **Hypotheses**
- H1: There is a negative relationship between ESG Risk and Expected Returns.
- H2: There is a positive relationship between ESG Risk and Total Risk.
- H3: Returns of firms with higher ESG Risk are statistically greater than the returns of firms with lower ESG Risk.

## **Key Steps**
- Data Collection
  - Used the yfinance library to download daily price data.
  - Utilized the tqdm library to monitor the progress of the data collection process.
  - Gathered the ESG Risk Scores of each security in a Google Sheet and exported it as a csv file.
- Data Preprocessing
  - Used pandas techniques to remove null values, convert the daily price data into daily returns, aggregate the dataFrames, and merge the ESG and returns data together.
  - Divided the list of securities into quartiles using pd.qcut based on their ESG Risk Score, creating four seperate portfolios.
- Exploratory Data Analysis
  - Used Seaborn and matplotlib to visualise the data by plotting boxplots, histograms, lineplots and regression plots.
  - Plotted a correlation matrix to see the relationship between all the variables in our DataFrame.
- Hypothesis Testing
  - Created a function for the t-statistic that determines whether the correlation between the ESG Risk Score and the Total Risk/Expected Returns was statistically significant or not (H1 & H2).
  - Used the t-test function from the SciPy library to determine whether the culmulative returns of the lower and upper quartile portfolios were statistically different or not (H3).

## **Results**
### Critical Value
Harvey, C.R., Liu, Y., and Zhu, H. (2016) proposed a criterion for establishing statistical significance in financial economics. They argue that given the extensive data mining in the field, new findings should clear a higher hurdle for significance. The paper suggests using a t-statistic greater than 3.0 as a criterion for significance. This value ensures that only robust and reliable research findings are considered significant in financial economics. Therefore, I used a critical value of 3.0 in my experiment.

### H1
Based on the calculated t-statistic of -2.068, we can see that there is some negative correlation between the Expected Daily Return and the ESG Risk Score. However this value is less negative than our critical value of -3, indicating that the correlation is not statistically significant. Therefore we fail to reject the null hypothesis in favour of the alternative hypothesis.
### H2
Based on the calculated t-statistic of -0.265, we can see that there is a small negative correlation between the Total Risk and the ESG Risk Score. However this value is less negative than our critical value of -3, indicating that the correlation is not statistically significant. Therefore we fail to reject the null hypothesis in favour of the alternative hypothesis.
### H3
From the culmulative returns line plot, we can see that the quartile with the lowest ESG Risk Scores performed the best, whereas the quartile with the highest ESG Scores performed the worst. Additionally from the boxplot, we see that the quartile with the lowest ESG Risk had the highest total Risk and spread of returns out of the four portfolios. However, based on the t statistic of 1.949 falling short of our critical value of 3, and a p-value of 0.051 exceeding our significance level of 0.05, we fail to reject the null hypothesis in favour of the alternate hypothesis. Therefore, the differences in performance between the quartiles are not statistically significant. Despite this result, the observed results aren't completely insignificant as the null hypothesis would be rejected at the 10% significance level.
### Social Risk Score
After seeing the correlation of -0.328 between Expected Retrun and Social Risk Score, I decided to investigate this further. Based on the calcuated t-statistic of -3.063, which is more negative than our critical value of -3, we can say that the negative correlation between Social Risk Score and Expected Daily Return is statistically significant.

## Limitations
- Due to limitations of the dataset, the analysis assumes that the ESG Risk Score remains constant over time for each security, which may not accurately reflect real-world dynamics.
- It assumes a linear relationship between ESG Risk Score and financial performance, neglecting potential non-linearities or interactions with other factors.
- External factors such as regulatory changes, market sentiment, or macroeconomic conditions are not explicitly accounted for in the analysis, potentially influencing results.

## Sources
- Yahoo Finance (https://uk.finance.yahoo.com/)
- The H1 and H2 equation (https://fabian-kostadinov.github.io/2014/10/30/significance-testing-of-pearson-correlations-in-excel/)
- Harvey, C.R. & Liu, Y. & Zhu, H.. (2016). "The Cross-Section of Expected Returns." *Review of Financial Studies*, 29, 5-68. DOI: [10.1093/rfs/hhv059] (https://doi.org/10.1093/rfs/hhv059)

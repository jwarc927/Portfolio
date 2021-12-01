## Human Development in Detroit

### Background

In 1950 the population of Detroit was 1,850,000, making it second only to Chicago in the Great Lakes Region of the United States.  It had a robust manufactuing sector which buttressed its position as one of America's leading cities and was considered to be a center of economic and cultural development.  Since then, for many reasons that this project will not specifically explore, Detroit has been in a steady state of decline.  In 2015 its population fell below 680,000, removing it from the top 20 cities in the United States for the first time in 165 years.  As of the 2020 Census, Detroit's population was 639,111, placing it in position 27. Some [research](https://www.milmi.org/_docs/publications/Population_Projections_2045.pdf) suggests that Detroit's population has reached a minimum and there is much effort being spent to revitilize the city in order to make it a more attractive place to live.

### Problem Statement

While the overarching problems in Detroit are well known it is not necessarily clear which of these problems are most holding Detroit back.  This project seeks to use county level data collected from every county in the United States to fit a machine learning model to these data and the Human Development Index (HDI) of the county.  This model will then be applied to the specific circumstances of Wayne County, Michigan (of which half of the land area and vast majority of the population are within the city limits of Detroit) in order to determine the top 5 areas of development that concerned individuals in Detorit could focus on to best increase the HDI of the area.

### Data Used

The data used for this analysis include economicand social data from [StatsAmerica](https://www.statsamerica.org/About.aspx), health data from [County Health Rankings & Roadmaps](https://www.countyhealthrankings.org/explore-health-rankings/use-data), and crime data from [The University of Michigan](https://www.icpsr.umich.edu/web/pages/).

All together this data included over 200 features.  Some of these features were used to calculate the HDI of the various counties in the dataset and others were highly colinear.  So, when all cleaning was complete and highly correlated (positive or negative) features were removed, a total of 117 features were passed on to the models.  Some counties had many missing values in the data (especially Alaska) so the final data included 2,969 of the 3,107 counties in the United States.

### Calculating the HDI

The target for this analysis is the HDI.  This value is not readily available for every county in the United States, but it can calculated from the data features collected.  Again, the features used to calculate this target will have to be removed from the data passed into the models because they will be nearly perfectly correlated to the target.  The result of this calculation allows us to generate a visualization of the HDI in the counties of the United States:

### Strategy and Results

Four different models were trained and evaluated both on predictive power and interpretability.  The goal is not neccessarily to find the best model that attributes HDI increases to specific features.  Rather, we would like a fairly robust model which can also provide us some guidance on which features deserve more attention.  Selected metrics from the models generated above are presented below:

|Model|Accuracy|Recall|Precision|F1 Score|
|---|---|---|---|---|
|**SVM**|70.6%|56.4%|78.6%|65.7%| 
|**Logistic Reg**|65.8%|56.2%|74.5%|64.1%| 
|**Random Forest**|64.6%|38.9%|79.9%|52.2%| 
|**Ensemble**|69.2%|53.7%|77.7%|63.5%| 

The decision tree models ultimately performed better in attributing HDI variation to the features in the dataset.  However, since the linear model did perform nearly as well it was selected as the model of choice due to its much better interpretability.

#### Wayne County

The report below shows the top 5 areas where Wayne County both underperformes the national average and has the most opportunity to improve. Note that according to our previous results Percent of returns with itemized deductions was the second most important feature in predicting HDI; however, it does not appear in the top portion of the report. This is because Wayne County already performs well in this particular category and does not need to "work" on this issue. Instead, a feature like % Low birthweight, which was only the 20th most important feature, appears as the number 4 priority. This is because Wayne County is significantly below the national average in this parameter and could, therefore, see the largest positive impact on its HDI by focusing on this issue.


|Feature|Mean Value|County Value|County SDs from Mean|Amount of Change|Impact on HDI|
|---|---|---|---|---|---|
|Motor Vehicle Theft rate per 100000|106.465|859.079|7.354|752.615|0.006|
|Percent of population that didn't work over the past year|26.435|32.402|0.641|5.966|0.005|
|% Smokers|21.345|24.000|0.693|2.655|0.003|
|% Low birthweight|8.134|11.000|1.580|2.866|0.002|
|Population growth, 2010-2016|0.343|-2.911|-0.696|-3.253|0.002|
|% With Access to Exercise Opportunities|64.255|95.000|1.490|30.745|-0.002|
|Percent of returns with itemized deductions|21.344|24.243|0.348|2.899|-0.002|
|Rural-urban continuum code (1-9)|4.359|1.000|-1.517|-3.359|-0.003|
|Total civilian population aged 18-64 rate|0.578|0.617|0.877|0.039|-0.003|
|Civilian population aged 25 and up|67527.664|1168342.000|5.004|1100814.336|0.003|


### Conclusions

While the HDI of a region is a somewhat reductionist metric, this model does have some advantages in identifying some key metrics where a region is both lagging behind the national average ***and*** where improvement in this metric is likely to have the highest impact on the HDI.  This should not be construed as a definitive way to set priorities, but it is helpful in knowing which areas are worthy of additional research.  So, using the report for Wayne County above, if one wanted to launch an anti-smoking campaign, that does seem likely to be a worthwhile endevour.  Conversely, we see that Wayne County is not lacking in access to exercise facilities so a program to provide gym time to low income residents may not be the best use of time and resources.
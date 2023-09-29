# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Exploring Climate Data of Singapore

### Overview

On 3 Jul 2023, a number of [Parliamentary Questions](https://www.mti.gov.sg/Newsroom/Parliamentary-Replies/2023/07/Written-reply-to-to-PQs-on-electricity-demand-and-grid-stress-from-prolonged-heat-wave) were raised by Members of Parliament around electricity demand and grid stress from prolonged heat waves. Due to the recent heatwave in Singapore, concerns were raised that it could possibly lead to increased electricity demand which can put a strain around capacity in the future.

By doing some secondary research around the relationship between temperature and electricity consumption, I found a number of interesting conclusions.

1. Based on a [study in Europe](https://www.semanticscholar.org/paper/The-non-linear-link-between-electricity-consumption-Bessec-Fouquau/2356f1a1e05054663df634f1d389967ff76af752), it was found that in cold countries, there is a negative correlation between temperature and electricity demand at lower temperatures, but a positive correlation between temperature and electricity demand in higher temperatures. This is likely due to the energy needs for heaters at low temperatures, as well as air conditioning at high temperatures.

2. Based on a study using a [New York dataset](https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/gtd2.12409), an increase in temperature corresponds to an increase in electricity consumption in New York above 20 degrees Celsius.

3. The [effect of a temperature change on energy consumption](https://www.ifw-kiel.de/fileadmin/Dateiverwaltung/IfW-Publications/Sebastian_Petrick/the-impact-of-temperature-changes-on-residential-energy-consumption/the-impact-of-temperature-changes-on-residential-energy-consumption.pdf) is higher if the household is in a rich country. This is likely due to the fact that people are more willing and able to increase their consumption of electricity as opposed to people in poorer countries, who may not even have the means to afford things like heaters and air conditioners.

Based on these three studies, we can probably see that Singapore, being a warm and rich country, would likely have a strong increase in electricity consumption as temperature increases (ie. positive correlation).

---
### Problem Statement

The problem statement is:
**<center>Can we accurately predict the level of electricity consumption (and thus, plan for electricity generation) based on climate-related data?</center>**

The ideal outcome is to provide the government with relevant information to develop policies to manage electricity generation and distribution as temperature fluctuates in the short term, and increases in the long term due to global warming.

It is important that the level of electricity generation is not too low (to prevent blackouts and brownouts), and not too high (wastage and high costs).

---
### Datasets

For this project, I'll be using a number of weather datasets from data.gov.sg. These are:
1. **Monthly Total Rainfall**: Measure of monthly total rainfall from 1982 to 2023
2. **Monthly Number of Rain Days**: Measure of number of rainy days from 1982 to 2023
3. **Monthly Mean Surface Air Temperature**: Measure of monthly mean surface air temperature from 1982 to 2023
4. **Monthly Mean Sunshine Duration**: Measure of mean sunshine hours 1982 to 2023
5. **Monthly Mean Relative Humidity**: Measure of monthly mean relative humidity from 1982 to 2023

Additionally, I'll be using a table called Singapore Energy Statistics, by the Energy Market Authority in Singapore. In there, I will use one dataset:
1. **Mean Monthly Household Electricity Consumption**: It's a measure of monthly household electricity consumption between 2005 and 2022 in kWh

---

### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|kwh_per_acc|float|Singapore_Energy_Statistics_2022|Average Monthly Household Electricity Consumption| 
|total_rainfall|float|rainfall-monthly-total|Total rainfall in mm| 
|no_of_rainy_days|integer|rainfall-monthly-number-of-rain-days|Monthly number of rain days| 
|mean_temp|float|surface-air-temperature-monthly-mean|Monthly mean surface air temperature| 
|mean_sunshine_hrs|float|SunshineDurationMonthlyMeanDailyDuration|Monthly mean sunshine hours per day| 
|mean_relative_humidity|float|relative-humidity-monthly-mean|Monthly mean relative humidity| 


---

### Summary of Analysis

Based on our heatmap, we see a mild correlation between the household consumption of electricity, with the mean temperature of the month, with a correlation coefficient of 0.43. We also see a milder correlation with the mean sunshine hours and the number of rainy days.

Based on our boxplots and outlier calculations, there are a couple of outliers in the distribution of household electrical consumption, and total monthly rainfall columns. This could possibly skew calculations of mean and standard deviation, as well as affect the line of best fit between electrical consumption and mean temperature.

We see a positive correlation between the mean monthly temperature in Singapore, as well as the household consumption of electricity.

---

### Conclusions / Recommendations

Based on our data exploration exercise, we have found the following:
1. There is a mild positive correlation between the mean monthly temperature in Singapore, as well as the household consumption of electricity. Based on the linear best fit line, an increase in 1 degree in temperature will result an increase in the household consumption of electricity of 23.38 kWh per household on average.
2. The distribution of electrical consumption is close to normally distributed, while the distributions of total monthly rainfall and mean temperature, are right skewed and left skewed respectively.
3. There are anomalies in the distribution of electrical consumption, and total monthly rainfall.

Due to the mild positive correlation between household electricity consumption and mean temperature, we can expect that there will be an increase in the consumption of electricity as temperature rises. With the current fluctuations of weather in the short term, coupled by the continued global warming long term, it is paramount for the government to ensure that these are taken into account when doing capacity planning in both the short and long run.

However, do note that correlation does not imply causation, and more studies need to be done in order to identify other factors that affect the level of electricity consumption. Additionally, there might be other factors that are correlated with both temperature and the level of electricity consumption that is the true causal factor of the latter.

Based on the results, I would recommend the following next steps:
1. Clean the data of outliers, and plot the graphs again to see if there's a stronger correlation between the mean temperature and the household electricity consumption, as well as an improved R^2 value.
2. Understand the relationship between temperature and electricity consumption on a more granular level, by breaking down into different subzones as well as different types of electricity consumption (manufacturing, construction, etc.).
3. Consider and find other factors that could affect energy consumption in Singapore, in order to support more accurate capacity planning in the future.
4. Build machine learning models to predict possible future temperature fluctuations and trends, and include these predictions in the planning of future energy requirements for Singapore. However, this should not be the only determinant in the planning of future energy requirements; we should incorporate other factors that we find from point 3 above.
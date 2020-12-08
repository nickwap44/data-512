# DATA 512 Final Project: Contructing a Predictive Model of Poor COVID-19 Outcomes in Washington State Counties
Nicholas Wapstra
University of Washington - Master of Science in Data Science Program

## Abstract

With COVID-19 continuing to be a pressing issue for people across the world, it is imperative to further our understanding of factors that play into how this virus spreads and populations that are most vulnerable. As a Washington state resident, I decided to focus this research on how COVID-19 has been effecting my region specifically. Having a clearer understanding about how we can predict potentially poor outcomes can be beneficial in helping policymakers decide where to distribute our resources. Therefore, for my final project I developed a model to predict poor COVID-19 outcomes (death per capita) by Washington State county based on known COVID-19 risk factors such as age, racial/ethnic makeup, gender distribution, income per capita, population density, pre-existing health conditions, and access to healthcare. This predictive model can be beneficial to furthering our understanding from multiple angles. From a prediction standpoint, it would indicate which counties are especially susceptible to poor COVID outcomes. This information could be used to understand where medical and virus prevention resources would best be allocated. As a secondary outcome, this type of model could also give some indication about which regressors are most significant in predicting poor outcomes. Finally, I hoped to learn if the predictive model for Washington State is informative for counties across the country that are located in states with similar COVID-19 guidelines (California) and less restrictive guidelines (Florida). Worse performance in states with less restrictive guidelines could be a reflection of the impact of the differing policy decisions. I used a ridge regression model to predict poor COVID-19 outcomes. The model achieved an R-squared value of 0.237 and a mean squared error of 1.658 on the test set. Because of the extreme variability of COVID-19 poor outcomes, I deemed that this was a reasonable, but not completely successful, model performance. County median age was the most significant predictor and was negatively associated with poor outcomes (beta = -0.713). Population density, county racial makeup, county uninsured rate, and diabetes prevalence were also significant in the model. The model performed equally well on California counties (R-squared = 0.234, MSE = 1.565) and extremely poorly on Florida counties (R-squared = -5.464, MSE = 5.713). Limitations included a small sample size (n = 39 counties) and an inexhaustive feature set. Future research could examine the effects of policy and mobility data on model performance.

## Data Sources
I used multiple datasets from multiple sources that I have outlined below:

*Washington State County COVID-19 data Dataset*

This [dataset](https://www.doh.wa.gov/Emergencies/COVID19/DataDashboard) provides COVID-19 cases, hospitalizations, and deaths by Washington State county by month (last updated on 12/3/2020). This data provides the information necessary to understand the death count related to COVID for each county in Washington state which will help represent the dependent variable in the analysis. The license for the dataset is Public Domain [(License)](https://www.doh.wa.gov/DataandStatisticalReports/DataGuidelines). The data provided is strictly counts of COVID-19 related death with no identifiers to individuals that were affected beyond their county of residence.

*California County COVID-19 data Dataset*

This [dataset](https://data.ca.gov/dataset/covid-19-cases) provides COVID-19 cases, hospitalizations, and deaths for California counties by day (last updated on 12/3/2020). This data provides the information necessary to understand the death count related to COVID for each county in California which will help represent the dependent variable in the analysis when assessing the WA county model across other states. The license for the dataset is Public Domain [(License)](https://data.ca.gov/dataset/covid-19-cases). The data provided is strictly counts of COVID-19 related death with no identifiers to individuals that were affected beyond their county of residence.

*Florida County COVID-19 data Dataset*

This [dataset](https://open-fdoh.hub.arcgis.com/datasets/florida-covid19-cases-by-county?geometry=-117.476%2C23.602%2C-49.229%2C36.843) provides COVID-19 cases, hospitalizations, and deaths for Florida counties by day (last updated on 12/3/2020). This data provides the information necessary to understand the death count related to COVID for each county in Florida which will help represent the dependent variable in the analysis when assessing the WA county model across other states. The license for the dataset is Public Domain [(License)](https://open-fdoh.hub.arcgis.com/datasets/florida-covid19-cases-by-county?geometry=-117.476%2C23.602%2C-49.229%2C36.843). The data provided is strictly counts of COVID-19 related death with no identifiers to individuals that were affected beyond their county of residence.

*Land Area by US County data Dataset*

This [dataset](https://www.census.gov/library/publications/2011/compendia/usa-counties-2011.html) provides land area by square mile for each county across the country from 2011. Population density is measured by person per square mile. This data will go into calculating the current population density by county. This will be an independent variable in the model. The license for this dataset is Public Domain [(License)](https://www.census.gov/about/policies/open-gov/open-data.html). Population density has been listed as a risk factor for COVID-19 and therefore may help predict a county's poor outcomes relating to COVID-19. There are not any clear ethical considerations when using this dataset.

*Personal Income Per Capita by US County data Dataset*

This [dataset](https://apps.bea.gov/itable/iTable.cfm?ReqID=70&step=1) provides income per capity estimates for each US county from 2019. I plan to limit the counts to Washington State, California, and Florida counties. The license for this dataset is Public Domain, CC0 [(License)](https://github.com/us-bea/eu.us.opendata/blob/master/LICENSE). Poverty has been linked as a risk factor for COVID-19. Therefore, I will be using income per capita as a measure of poverty for the model. It is important to consider that this measure of poverty may not be entirely representative of the risk factor of interest. There are people in poverty within King County that will be masked by high-earners in the area.

*Age, Sex, Race, and Hispanic Origin by US County data Dataset*

This [dataset](https://www.census.gov/data/tables/time-series/demo/popest/2010s-counties-detail.html) provides population count estimates for each county with age, sex, race, and hispanic origin counts provided from 2019. The license for this dataset is Public Domain [(License)](https://www.census.gov/about/policies/open-gov/open-data.html). Sex and race have been implicated as potential risk factors for COVID-19. Population will be used to calculate the population density, percent of population that is female, and percent of population that is non-white. It is important to note that there are no identifiers besides counts that will be used in the model.

*Diabetes Prevalence by US County data Dataset*

This [dataset](https://www.cdc.gov/diabetes/data/statistics/faqs.html#data) provides estimated percentage of the population with a diabetes diagnosis for each county from 2019. The license for this dataset is Public Domain [(License)](https://www.cdc.gov/nchs/data_access/restrictions.htm). Pre-existing health conditions have been implicated as a risk factor for COVID-19. I will be using diabetes prevalence as a proxy for this measure based on availability of data. There are no identifiers besides the percentage of the population with diabetes.

*Small Area Health Insurance Estimates (SAHIE) using the American Community Survey (ACS) data Dataset*

This [dataset](https://www.census.gov/data/datasets/time-series/demo/sahie/estimates-acs.html) provides estimates of the percentage of the population that are uninsured by county from 2018.The license for this dataset is Public Domain [(License)](https://www.census.gov/about/policies/open-gov/open-data.html). I will be using the percentage of uninsured by county as a proxy to access to healthcare based on the availability of data. There are no identifiers besides the percentage of the population with diabetes.

## Data and Code for Replication
Source data (in .csv format):
1. wa-county-incomepercapita.csv
2. wa-county-popchar-age.csv
3. wa-county-popchar-racial-identity.csv
4. covid-wa-county-deaths.csv
5. ca-county-incomepercapita.csv
6. ca-county-popchar-age.csv
7. ca-county-popchar-racial-identity.csv
8. covid-ca-county-deaths.csv
9. fl-county-incomepercapita.csv
10. fl-county-popchar-age.csv
11. fl-county-popchar-racial-identity.csv
12. covid-fl-county-deaths.csv
13. us-county-health-insurance.csv
14. us-county-landarea.csv
15. us-diabetes-county.csv

Compiled datasets used for analysis:
1. wa-county-final.csv
2. ca-county-final.csv
3. fl-county-final.csv

Final report with code for data acquisition and analysis:
data-512-final-project.ipynb

Data visualizations:
1. data-512-final-1.png
2. data-512-final-2.png
3. data-512-final-3.png
4. data-512-final-4.png

## Fields
The value of the fields from the final compiled dataset are as follows:
- County (string): lists the name of the county
- IncomePerCapita (int64): income per capita for the county
- MedianAge (float64): median age for the county
- PercentFemale (float64): percentage of the county population that is female
- PercentNonWhite (float64): percentage of the county population that is non-white
- PercentDiabetic (float64): percentage of the county population that has been diagnosed with diabetes
- PercentUninsured (float64): percentage of the county population that is uninsured
- PopulationDensity (float64): total county population divided by county land area (in square miles)
- DeathsPerCapita (float64): total deaths attributed to COVID-19 divided by total county population

## Special Considerations
The data was last updated on December 3rd, 2020.

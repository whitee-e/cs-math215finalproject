# Analysis of Global Deaths from Dementia 2000-2021
## CS/MATH-215 Final Project
Ellie White and Amy Li

## Introduction
Dementia is a set of symptoms consisting of memory loss and impaired cognitive functioning. The most common cause of dementia, accounting for 60-80% of cases, is Alzheimer’s disease, which is characterized by abnormal protein accumulation in the brain (10). The most significant risk factor for developing Alzheimer’s disease is aging. Though Alzheimer’s is not curable, treatment can delay the disease progression. My colleague Amy Li has examined dementia severity across age and gender groups. My report takes a broader global approach to understanding global rates of dementia mortality over time.
<br>
<br>
This report analyzes global health statistics regarding deaths caused by Alzheimer’s and other dementias between 2000 and 2021. I refer to these deaths under the broad category of dementia-related deaths. I was interested in determining which countries have had the highest rates of dementia-related deaths when adjusted for population size. Dementia is caused by neurodegenerative diseases of aging (such as Alzheimer’s disease). People in wealthier countries generally live longer, dying more from noncommunicable diseases and diseases of aging than from infectious diseases (13). Because of this, I chose to investigate my hypothesized link between a country’s Gross Domestic Product (GDP) and its dementia-related mortality rate.
<br>
<br>
To test my hypothesis, I used three datasets from Our World in Data (OWID). I used a dataset which contains the number of deaths due to dementias in each country between 2000 and 2021 (1). This data was originally processed by OWID from the World Health Organization’s global health estimates, which come from national datasets and partner organizations (3). Since the Alzheimer’s data was not adjusted for each country’s population size, I utilized a second dataset which lists the population of each country by year (1950-2023), including projections for 2024 to 2100 (6). The population data was processed by OWID from the United Nations World Population Prospects 2024 data, which contains documented and estimated demographic data collected from many sources (varying by country) (14). Lastly, in order to compare Alzheimer’s and dementia death rates to GDP per capita, I used a third OWID dataset containing GDP per capita for each country and year (1990-2024) (2). This data was processed by OWID from the World Bank’s World Development Indicators, which uses regional and national estimates for measures of development (12).
<br>
<br>
To answer my research questions, I needed to merge the three datasets in order to have data about each country’s total dementia deaths and GDP per capita for each year. My data analysis process was made simpler due to the fact that all three of my datasets were processed by OWID, which helped clean the data by standardizing time units and country names. In addition to merging the datasets and inspecting the dataframe for missing data, I calculated the dementia mortality rate in each country and year. This allowed for comparison of dementia data between countries, adjusted for population size.
<br>
<br>
## Methods & Results
After loading the data, I began processing the data to answer my first research question regarding the mortality rate of dementia by country. The population dataset contained data outside the time frame of interest, so I excluded these portions from my dataframe. I merged my dementia and population dataframes by country and year, then calculated the mortality rate by dividing dementia deaths by total population. I calculated the mortality rate per 100,000 people. Since rates of dementia-related mortality are  relatively low in terms of overall population size, this made the mortality rates easier to interpret.
<br>
<br>
Once I had calculated the mortality rate for each country and time point, I generated a Plotly choropleth map figure showing the global distribution of dementia mortality rate between 2000 and 2021 (Figure 1). Comparing the 2000 and 2021 data, it’s evident that the dementia mortality rate in many countries has increased. These shifts are most pronounced in parts of North America, Western Europe, and Australia.
<br>
<br>
<iframe src="choropleth_alzheimers.html" width="200%" height="1000" style="border:none;">
  <p>Your browser does not support iframes.</p>
</iframe>
<br>
<br>
__Figure 1__. Dementia-related mortality rates by country in 2000 and 2021. Mortality rates were calculated in terms of deaths per 100,000 people living in a given country. Raw numbers of dementia deaths are from the World Health Organization (2024) with major processing by Our World in Data. Population data is from the UN World Population Prospects (2024) with processing by Our World in Data. This choropleth map shows that dementia mortality rates have largely increased across the globe between 2000 and 2021, especially in certain regions including parts of North America, Western Europe, and Australia. 
<br>
<br>
I was interested in observing the relationship between a country’s total population and its total dementia deaths, so I made an exploratory scatterplot with population on the x axis and total dementia deaths on the y axis (not pictured). I used this plot to find outliers in dementia mortality rates. This served a similar function to my choropleth map, but allowed for easier comparison between countries and showed some smaller countries that weren’t represented on the choropleth map. The small country of Monaco stood out, with the highest mortality rate from dementia across the entire time period. Monaco is a very wealthy country and has an unusually high percentage of citizens over the age of 65 (5). Since GDP per capita is positively correlated with life expectancy, I wondered if GDP per capita was also positively correlated with dementia mortality (8).
<br>
<br>
I extracted data between 2000 and 2021 from the GDP dataset, then merged it with my previously created dataframe that contained the dementia and population data. I noticed that the number of rows in this twice merged dataframe was less than either of the input dataframes, so I inspected the dropped rows to make sure that relevant data wasn’t being dropped. I found that some countries were dropped because they lacked GDP data, and others were dropped because they lacked dementia data. I excluded these countries from my further analysis. Then, I generated an animated scatterplot showing GDP per capita on the x axis and dementia mortality rate on the y axis (Figure 2). 
<br>
<br>
<iframe src="scatter_gdp.html" width="100%" height="100%" style="border:none;">
  <p>Your browser does not support iframes.</p>
</iframe>

__Figure 2__. GDP per capita vs dementia mortality rate in 2000 and 2021. Mortality rates were calculated in terms of deaths per 100,000 people living in a given country. Raw numbers of dementia deaths are from the World Health Organization (2024) with major processing by Our World in Data. Population data is from the UN World Population Prospects (2024) with processing by Our World in Data. This figure shows a visible positive correlation between GDP per capita and dementia mortality rate. The strength of the positive correlation increases from 2000 to 2021 (r values of 0.47 and 0.61, respectively). There are several small outlier countries, deviating from the trend.
<br>
<br>
## Conclusions
Dementia mortality rates generally increased across the globe between 2000 and 2021, with some regions showing sharper increases and others remaining stable. The most significant increases were in parts of North America, Western Europe, and Australia, while India and the African continent stayed more stable in mortality rates (Figure 1). In 2021, the countries with the highest dementia mortality rates were Monaco, the United Kingdom, Finland, Denmark, and Sweden.
<br>
<br>
Consistent with the hypothesis, GDP per capita and dementia mortality rate are positively correlated (Figure 2). Calculated Pearson correlation coefficients suggest that the strength of correlation increased between 2000 (r = 0.47, p < 0.05) and 2021 (r =  0.61, p < 0.05). The real-world relationship between the variables may be changing, causing a stronger correlation. However, there are a multitude of alternative explanations. First, improvements in data collection could’ve caused a stronger correlation in the more recent years. In other words, the underlying pattern of the data could be consistent over time, but reductions in noise of the data and measurement error caused the correlation coefficient to increase. This is called disattenuation (4). Yet it seems unlikely that measurement error decreased uniformly across the globe. There are vast disparities in healthcare infrastructure and related data collection, and countries with higher GDPs have the resources to support more rigorous data collection. Thus, the improved ability of high-resource countries to track dementia deaths may contribute to the positive correlation.
<br>
<br>
There are also broader limitations with this analysis. First, some countries lacked GDP data or dementia data and were excluded from the analysis. Within the included data, the rates of dementia mortality are likely undercounts, since it is difficult to identify the underlying cause of deaths related to Alzheimer’s disease or other neurodegenerative diseases that cause dementia (11). Dementia can cause death directly through brain damage that inhibits basic bodily functions, and also from cognitive decline leading to falls and other accidents (9).
<br>
<br>
Despite its limitations, this project demonstrates the value of data analysis in understanding longitudinal global health trends regarding dementia mortality. Future studies should analyze availability and affordability of Alzheimer’s treatments and dementia care in different countries, looking to identify any countries that have high need for such resources but low accessibility. In Monaco, where the dementia mortality rate is over twice that of any other country, free therapeutic care is available to citizens living with Alzheimer’s (7). Analyzing affordability and access to treatment could help identify other countries that would most benefit from improvements. In this undertaking, we must consider that limited data collection in low resource countries might cause us to overlook areas of high need.
<br>
<br>
Going beyond the scope of dementia and cognitive disorders, future work is needed to analyze correlations between GDP and other global health measures, and whether substantial international investment has influenced correlations over time. Using data science to evaluate the impact of global funding campaigns on human health is vital to secure future funding, especially in the current time of global health funding hesitancy.
<br>
<br>	

## References:
(1) “Deaths from Alzheimer’s.” Our World in Data, [https://ourworldindata.org/grapher/deaths-from-alzheimers-other-dementias?time=2000..latest](https://ourworldindata.org/grapher/deaths-from-alzheimers-other-dementias?time=2000..latest). Accessed 6 Dec. 2025.
<br>
<br>
(2) “GDP per Capita.” Our World in Data, [https://ourworldindata.org/grapher/gdp-per-capita-worldbank?time=earliest..latest](https://ourworldindata.org/grapher/gdp-per-capita-worldbank?time=earliest..latest). Accessed 6 Dec. 2025.
<br>
<br>
(3) Global Health Estimates. [https://www.who.int/data/global-health-estimates](https://www.who.int/data/global-health-estimates). Accessed 6 Dec. 2025.
<br>
<br>
(4) Karami, Bassel. “Biased Model Coefficients - (Part 1).” Towards Data Science, 17 Jan. 2022, [https://towardsdatascience.com/biased-model-coefficients-part-1-2722128b9e1c/](https://towardsdatascience.com/biased-model-coefficients-part-1-2722128b9e1c/).
<br>
<br>
(5) “Monaco Population 2025.” World Population Review, 5 Dec. 2025, [https://worldpopulationreview.com/countries/monaco](https://worldpopulationreview.com/countries/monaco).
<br>
<br>
(6) “Population.” Our World in Data, [https://ourworldindata.org/grapher/population-with-un-projections?tab=map&time=earliest..2100](https://ourworldindata.org/grapher/population-with-un-projections?tab=map&time=earliest..2100). Accessed 6 Dec. 2025.
<br>
<br>
(7) Tanti, Cassandra. “Residents with Alzheimer’s, Cognitive Disorders to Get Free Access to Centre.” Monaco Life, 4 May 2023, [https://monacolife.net/residents-with-alzheimers-cognitive-disorders-to-get-free-access-to-centre/](https://monacolife.net/residents-with-alzheimers-cognitive-disorders-to-get-free-access-to-centre/).
<br>
<br>
(8) Țarcă, Viorel, et al. “Social and Economic Determinants of Life Expectancy at Birth in Eastern Europe.” Healthcare, vol. 12, no. 11, June 2024, p. 1148. PubMed Central, [https://doi.org/10.3390/healthcare12111148](https://doi.org/10.3390/healthcare12111148).
<br>
<br>
(9) “Understanding How Dementia Causes Death.” Columbia Neurology, 14 Mar. 2023, [https://www.neurology.columbia.edu/news/understanding-how-dementia-causes-death-0](https://www.neurology.columbia.edu/news/understanding-how-dementia-causes-death-0).
<br>
<br>
(10) “What Is Dementia? Symptoms, Causes & Treatment | Alz.Org.” Alzheimer’s Association, [https://www.alz.org/alzheimers-dementia/what-is-dementia](https://www.alz.org/alzheimers-dementia/what-is-dementia). Accessed 6 Dec. 2025.
<br>
<br>
(11) WHO Methods and Data Sources for Country-Level Causes of Death 2000-2021. World Health Organization, May 2024, [https://cdn.who.int/media/docs/default-source/gho-documents/global-health-estimates/ghe2021_cod_methods.pdf](https://cdn.who.int/media/docs/default-source/gho-documents/global-health-estimates/ghe2021_cod_methods.pdf).
<br>
<br>
(12) “World Bank Open Data.” World Bank Open Data, [https://data.worldbank.org](https://data.worldbank.org). Accessed 6 Dec. 2025.
<br>
<br>
(13) World Health Statistics 2024: Monitoring Health for the SDGs, Sustainable Development Goals. World Health Organization, 21 May 2024, [https://iris.who.int/server/api/core/bitstreams/74b12494-f213-4b5b-9533-18442147e1fb/content](https://iris.who.int/server/api/core/bitstreams/74b12494-f213-4b5b-9533-18442147e1fb/content).
<br>
<br>
(14) World Population Prospects. [https://population.un.org/wpp/downloads?folder=Standard%20Projections&group=Most%20used](https://population.un.org/wpp/downloads?folder=Standard%20Projections&group=Most%20used). Accessed 6 Dec. 2025.





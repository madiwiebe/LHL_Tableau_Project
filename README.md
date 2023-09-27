# Final-Project-Tableau

## Project/Goals

The objective of this project was to compare causes of death worldwide from 1990-2019. The impact of factors such as disease, natural disasters, and conflict were evaluated based on overall number of mortalities, contribution to mortality rate (as percent of population), and geographical regions.

The trends of leading causes of death were investigated, and those factors that heavily impacted the overall trend of global death rates were examined more closely.

Cardiovascular disease, neoplasms, and chronic respiratory diseases were identified as the leading causes of death globally as well as in several countries.

![Global_mortality_rates](docs/images/2015%20deaths%20by%20percent%20population.png)

Conflict and terrorism as well as natural disasters were found to be the main underlying cause of abnormal peaks in global mortality rates.

![Conflict_and_natural_disasters](docs/images/ConflictNatural%20DIsasters.png)

## Process
### Import data
- Select which option to complete for the project. Locate and download associated dataset.
- Convert to Excel workbook in preparation for uploading to Tableau.

### Exploratory Data Analysis
- Investigate dataset features by creating preliminary visualizations in Tableau.
- Check for null values.
- Check for duplicate values (e.g. records for "United States" as well as "America").
- Develop questions to investigate further.

### Feature engineering
- Combined causes of death data with population data (2015).
- Created a meausre for total number of deaths by country.
- Created groups of countries based on continent/region.
- Created a measure for deaths as a percentage of population (2015).
- Created an index feature for comparing leading causes of death across countries and regions.

### Creating visualizations
- Heatmaps (total number of deaths, mortality rates)
- Causes of death over time (bar charts, line graphs, area charts)
- Trends in specific causes of death over time.
- Leading causes of death in Canada.
    - Forecasting trends in the top five leading causes of death in Canada.
- Cluster analysis (based on number of deaths, population, and mortality rate).

### Creating dashboards and presentation story
- Develop interactive filters to highlight features between related charts.
- Restrict the number of visible legends, titles, and filters.
- Review colours and set limits for how many rows may be displayed at once.


## Results

I chose to work with the "Causes of Death - Our World In Data" dataset (Option 2). Initially, I worked with the raw data; however, after some data exploration I realized that having the causes of death in columns instead of rows was severely limiting my ability to aggregate and filter my data.

After revisiting the source data, I found a version of the dataset that had been reshaped to have cause of death information stored in the rows.

### Question 1: What are the leading causes of death worldwide?

As I created my initial visualizations, I focused on identifying the causes of death having the largest number of associated deaths. Globally, cardiovascular diseases, neoplasms, and chronic respiratory diseases are the leading causes of death. 

![global_deaths_by_cause](docs/images/Number%20of%20Deaths%20by%20Cause.png)

### Question 2: How does population size affect number of deaths?

I noticed that within each cause of death category, it was countries with large populations that were contributing the most to the total number of deaths. This led me to finding population data for each country at a given point of time (the year 2015) and comparing population size with number of deaths. Unsurprisingly, countries with larger populations reported more annual deaths.

![population_vs_mortality_rate](docs/images/Population%20vs%20total%20deaths%202015.png)

### Question 3: Which countries have the highest mortality rates? 

Knowing that population size was significantly correlated with number of deaths, I attempted to normalize the data by creating a calculated field for mortality rates:

    mortality rate = number of deaths/population * 100%

When comparing mortality rates instead of total number of deaths, the country rankings shifted dramatically. While China, India, and the United States have the largest number of deaths in 2015, Lesotho, Somalia, and Bulgaria had the highest mortality rates.

### Question 4: What are the most prevalent causes of death in different regions?

I created regional groups to allow for more flexible levels of detail within my visualizations (11 regions vs 213 countries/entities). When comparing between these regions, the top three causes of death had some variation. Cardiovascular diseases were present in all eleven regions, and most regions included neoplasms as a leading cause of death. However, factors such as HIV/AIDS, neonatal diseases, and digestive diseases (among others) were only prevalent in one or two regions.

### Question 5: What are the leading causes of death in Canada? Are they predicted to increase or decrease in the next 10 years?

Cardiovascular diseases, neoplasms, and chronic respiratory diseases were the three leading causes of death in Canada. All three were predicted to increase in the next 10 years. However, other causes of death that were not so prevalent did demonstrate downward trends (e.g. meningitis, interpersonal violence, and neonatal disorders).

### Question 6: How have trends in global number of deaths changed over time?

In general, the global number of deaths increased in a slow and smooth fashion. However, there were some years with irregular peaks in this trend. When exploring this peaks further, they were identifiable as years where there was a large loss of life due to conflict or natural disasters. When visualizing those causes of death independently, it was clear that they did not follow a smooth trend. These causes involve a large number of deaths within a short span of time, as opposed to other causes where the timeframe is much more spread out.

### Question 7: How can countries be grouped based on population size, number of deaths, and mortality rate? Do these countries have any other variables in common? 

When performing cluster analysis with the context of population size, number of deaths, and mortality, it seemed that the strongest determining factor was population size. China and India made up a cluster all on their own. However, some regionality seemed to be associated; for example, Russia, Ukraine, Belarus, and other Eastern European countries all fell within the same cluster. More research and modeling with other variables would have to be done to evaluate whether mortality rates can predict other features of a country. 

## Challenges 

Working with 33 independent causes of death as equivalent categories was cumbersome to visualize, especially when my other features also contained several values (213 countries/entities, 20 years). Finding ways to display graphs that were not overwhelming and communicated a meaningful idea was challenging, especially when it came to colour coding!

The limited dimensions to this dataset were also restrictive. I think that if I had not added population data to this dataset, I would not have been able to derive many insights from this dataset.

Finally, I feel that this dataset is incomplete. There are several years where there are zero deaths reported in a region, and some regions (such as Macau) where only one death is recorded for the entire 20 years covered by the dataset. 

## Future Goals

- Combine more features with this data. 
    - Instead of using population data from only 2015, use population data from many years to explore trends in mortality rates.
    - Consider incidence vs mortality rates to assess the most fatal causes of death. How many people are living with the condition but not dying from it yet?
    - Make connections between trends and historic context (e.g. a decrease in the number of deaths caused by a disease after the discovery of a new treatment).
    - Explore more granular details for causes of death with a wide scope (e.g. types of cancer within neoplasms, specific conditions within cardiovascular diseases).
- Improve data integrity. Fill in missing values.
- Investigate country characteristics that may be related to mortality rates. Continue to refine cluster analysis and move toward building a predictive model.
- Create groups of countries based on their three leading causes of death. Do these countries have anything else in common?
- Explore trends in data connected to social conditions (drugs, alcohol, self-harm).

# Cleaned Precipitation Data

This folder contains cleaned and processed monthly precipitation data prepared for the Capstone project.

- Data source: ECCC Historical Monthly Climate Data
  
Geographic coverage

Region: Atlantic Canada
Provinces: Nova Scotia (NS), New Brunswick (NB), Prince Edward Island (PE), Newfoundland and Labrador (NL)

Temporal coverage

Period: 1995–2025
(coverage varies by station, based on data availability)

Granularity

Station × Month

Core variable

Total Monthly Precipitation (mm)

Derived from column P in the original ECCC dataset
Values represent total liquid-equivalent precipitation for each month



Data cleaning summary
The cleaning process consolidates raw monthly station observations into a structured fact table and includes:

Selection of relevant columns
Data type standardization
Construction of a monthly date field
Removal of invalid or missing precipitation values
Deduplication at the station–month level

Output dataset

data/clean/fact_precipitation.csv

This dataset is used as the Fact_Precipitation table in the Power BI star schema and connects to:

Dim_Calendar via Date
Dim_Station via ClimateID
Dim_Region via Province code

Documentation
All precipitation data preparation steps are documented in:

script/python/fact_precipitation.ipynb

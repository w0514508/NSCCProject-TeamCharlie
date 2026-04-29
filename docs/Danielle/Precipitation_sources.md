# Precipitation Dataset – Atlantic Canada

## Data Source
Monthly climate observations were sourced from Environment and Climate Change Canada (ECCC) using the MSC Datamart.

Dataset: Monthly Climate Observations - https://dd.weather.gc.ca/today/climate/observations/monthly/csv/
Region: Atlantic Canada (NS, NB, PE, NL)
Period: 1995–2025
Granularity: Station × Month

## Raw Data
The raw dataset (precipitation_monthly_raw_atlantic.csv) is produced by programmatically downloading and consolidating individual station-year CSV files.
No transformations are applied at the raw stage aside from concatenation.
Cleaning & Preparation
The cleaning process is documented in notebooks/precipitation_cleaning.ipynb and includes:

- Column selection and renaming
- Data type standardization
- Construction of a monthly date field
- Removal of invalid or missing precipitation values
- Deduplication at the station-month level

## Metric Definition

Total Monthly Precipitation (mm) is defined using column P from the ECCC dataset.
Quality flags (DwP) and normal percentages (P%N) are not used in the analytical fact table.

## Output
The cleaned dataset is saved as:
data/clean/fact_precipitation.csv

This file is used as the Fact_Precipitation table in the Power BI star schema and connects to:

- Dim_Calendar via Date
- Dim_Station via ClimateID
- Dim_Region via Province code

## Documentation
All precipitation data preparation steps are documented in:
- scrips/python/Danielle/precipitation_cleaning.ipynb
- scrips/python/Danielle/Script for raw data download.ipynb

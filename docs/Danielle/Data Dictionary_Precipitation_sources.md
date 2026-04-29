# Precipitation Data – Sources, Cleaning, and Assumptions

This document describes the **data source**, **cleaning process**, **assumptions**, and **transformations** applied to the precipitation dataset used in this project.

---

## Data Source

Monthly precipitation data was obtained from **Environment and Climate Change Canada (ECCC)** through the official Government of Canada weather data distribution service.

- **Source portal:**  
  https://dd.weather.gc.ca/today/climate/observations/monthly/csv/

- **Dataset type:** Monthly Climate Observations  
- **Geographic scope:** Atlantic Canada (Nova Scotia, New Brunswick, Prince Edward Island, Newfoundland and Labrador)  
- **Granularity:** Weather station × month  
- **Time coverage:** Varies by station, with multi-decade historical records  

Raw CSV files were downloaded programmatically and consolidated prior to cleaning.

---

## Raw Variable Definition

In the original ECCC monthly dataset:

- **`P`** represents **Total Monthly Precipitation (mm)**  
- This value includes:
  - rainfall  
  - snowfall converted to liquid water equivalent  
  - all forms of precipitation recorded during the month  

---

## Cleaned Dataset

**Table name:** `Fact_Precipitation_Monthly`  
**Grain:** Station × Month  

### Data Dictionary

| Field | Description |
|------|------------|
| ClimateID | Weather station identifier (foreign key to Dim_Station) |
| Date | Monthly reference date (first day of the month, foreign key to Dim_Calendar) |
| Precipitation_mm | Total monthly precipitation in millimeters |
| ProvinceCode | Province code (foreign key to Dim_Region) |

---

## Cleaning and Transformation Steps

The dataset was primarily cleaned using **Python (pandas)** before ingestion into Power BI.

Key steps included:

- Selecting only relevant columns required for analysis
- Casting `ClimateID` as text to preserve alphanumeric station identifiers
- Converting precipitation values to numeric format
- Constructing a monthly `Date` field using year and month values (`YYYY-MM-01`)
- Removing records with missing or invalid precipitation values
- Excluding negative precipitation values
- Deduplicating records to ensure one row per station per month

No statistical interpolation, smoothing, or imputation was applied.

---

## Power BI Transformations

In Power BI (Power Query), transformations were limited to:

- Enforcing correct data types  
- Removing error rows where applicable  
- Hiding technical key fields from the reporting layer  

All substantive data preparation occurred upstream in Python.

---

## Assumptions

- Zero precipitation values are considered valid observations.
- Differences in station coverage across datasets reflect real-world data availability.
- Monthly aggregation is appropriate for long-term trend analysis and BI reporting.
- Precipitation metrics are modeled separately from temperature metrics to preserve analytical clarity.

---

## Intended Use

The cleaned precipitation dataset supports:

- Long-term precipitation trend analysis  
- Year-over-year comparisons  
- Dual-axis visualizations with monthly temperature  
- Regional aggregation via Dim_Region  

This table is part of a star schema data model and is designed for analytical reporting rather than raw data exploration.

---

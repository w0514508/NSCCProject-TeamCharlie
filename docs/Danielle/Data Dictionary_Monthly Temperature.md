# Monthly Temperature Data – Sources, Aggregation, and Assumptions

This document describes the **source**, **aggregation process**, **assumptions**, and **intended use** of the monthly temperature dataset used in this project.

---

## Data Source

The monthly temperature dataset is derived from daily weather observations contained in the file dim_temp_clean.csv. This daily dataset was created by Yashaswi Tiwari using data originally sourced from Environment and Climate Change Canada (ECCC)**.

Daily weather data—including temperature, precipitation, and wind variables—was cleaned and consolidated at the **daily level by the project team** as part of the broader meteorological data pipeline. This daily dataset serves as a team-level analytical foundation.

The **monthly temperature dataset documented here was independently derived through aggregation** for analytical and reporting purposes.

---

## Derived Variable Definition

**Mean Monthly Temperature (°C)** is defined as:

> The arithmetic mean of daily mean temperature values recorded for each weather station within a given calendar month.

This variable represents average temperature conditions at the monthly level and is suitable for long-term trend analysis.

---

## Clean Dataset

**Table name:** `Fact_Temperature_Monthly`  
**Grain:** Weather Station × Month  

### Data Dictionary

| Field | Description |
|------|-------------|
| ClimateID | Weather station identifier (foreign key to Dim_Station) |
| Date | Monthly reference date (first day of the month, `YYYY-MM-01`, foreign key to Dim_Calendar) |
| MeanMonthlyTemp_C | Mean monthly temperature in degrees Celsius (°C) |

---

## Aggregation and Transformation Steps

Monthly temperature values were generated using **Python (pandas)** with the following steps:

1. Selection of daily weather records containing valid temperature observations
2. Casting station identifiers (`ClimateID`) as text to preserve alphanumeric codes
3. Conversion of daily timestamps to a monthly reference date
4. Grouping data by weather station and calendar month
5. Calculation of the arithmetic mean of daily mean temperatures within each group
6. Output of a cleaned, station-level monthly temperature dataset

No interpolation, climate normalization, or smoothing techniques were applied.

---

## Power BI Transformations

In Power BI (Power Query), transformations were intentionally minimal and limited to:

- Enforcement of correct data types
- Creation and management of relationships with dimension tables
- Hiding technical key fields from the reporting layer

All substantive data preparation and aggregation occurred upstream in Python.

---

## Assumptions

- Daily mean temperature values are assumed to be representative of daily weather conditions.
- Monthly aggregation is appropriate for long-term climate trend analysis and year-over-year comparison.
- Differences in station coverage reflect real-world data availability and reporting continuity.
- The absence of daily data for a station-month results in exclusion of that record from the monthly dataset.

---

## Intended Use

The `Fact_Temperature_Monthly` dataset is used to support:

- Long-term temperature trend analysis
- Year-over-year and decadal comparisons
- Dual-axis visualizations alongside monthly precipitation
- Regional and station-level aggregation through shared dimensions

This dataset is modeled as part of a **star schema** and is designed for analytical reporting rather than raw data exploration.

Memo: The source of this table changed in May 2 from Atlantic_Climate.csv to dim_temp_clean.csv.

---

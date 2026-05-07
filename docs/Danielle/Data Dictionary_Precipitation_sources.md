# Data Dictionary — Precipitation (Atlantic Canada)

## Dataset Overview

This dataset contains **monthly aggregated precipitation data** for Atlantic Canada, derived from daily climate observations provided by Environment and Climate Change Canada.

The dataset is designed to support **climate-scale analysis** of precipitation patterns over time, focusing on frequency and long-term variability rather than day-to-day weather fluctuations.

Daily precipitation data is used upstream during data processing but **is not included** in the final analytical dataset.

---

## Data Source

- **Source**: Environment and Climate Change Canada (ECCC)
- **Original Data**: Daily precipitation observations at the weather station level
- **Geographic Scope**: Atlantic Canada
- **Temporal Scope**: Historical observations (monthly aggregation)

---

## Final Analytical Table

### **Fact_Precipitation_Monthly**

This fact table stores **monthly total precipitation values**, aggregated at the station level.

It serves as the primary dataset for analyzing:
- Long-term precipitation patterns
- Interannual variability
- Precipitation frequency metrics (e.g., wet months per year)

The analytical focus is intentionally placed at the **monthly and annual level** to capture climate-relevant signals while avoiding daily-level noise.

---

## Table Granularity

- **One row per station per month**
- Monthly precipitation totals expressed in **millimeters (mm)**

---

## Column Descriptions

### `Date`
- Represents the reference date for the monthly aggregation
- Typically corresponds to the month-end date
- Used to join with the calendar dimension

---

### `ClimateID`
- Unique identifier for each Environment Canada weather station
- Used for station-level aggregation and spatial analysis

---

### `Precipitation_mm`
- Total precipitation accumulated during the month
- Unit: millimeters (mm)
- Represents the sum of daily precipitation observations aggregated to the monthly level

---

## Derived Analytical Concepts

### **Wet Month**
A *wet month* is defined as:

> A month in which total precipitation exceeds the **long-term monthly average** across Atlantic Canada.

This definition allows precipitation frequency to be analyzed consistently at the monthly and annual scale.

---

### **Wet Months per Year**
- Represents the **count of wet months within a given year**
- Used as a frequency-based climate indicator
- Supports comparison of precipitation patterns across different years

These metrics are implemented as **analytical measures** rather than stored as physical columns in the dataset.

---

## Notes and Assumptions

- The dataset intentionally excludes daily precipitation records from the final model
- Monthly aggregation is used to emphasize climate-scale behavior rather than short-term variability
- All precipitation values reflect observed totals, not modeled or interpolated data

---

## Intended Use

This dataset is intended for:
- Exploratory Data Analysis (EDA)
- Long-term precipitation trend analysis
- Frequency-based climate indicators
- Integration with other climate datasets (e.g., extreme events) at compatible temporal scales

It is not intended for:
- Daily weather analysis
- Event-level modeling
- Short-term forecasting

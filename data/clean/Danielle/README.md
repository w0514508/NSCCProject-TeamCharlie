# Clean Data – Danielle

This folder contains **cleaned and analytical datasets** generated from raw climate data and used directly in the Power BI data model and exploratory analysis.

All datasets in this folder have been validated and are considered model‑ready.

---

## Datasets

### Monthly Aggregates

- **fact_precipitation_monthly.csv**  
  Monthly total precipitation by weather station.  
  Derived from daily precipitation records and validated for dimensional integrity.  
  Used for long‑term trend and year‑over‑year precipitation analysis.

- **fact_temperature_monthly.csv**  
  Monthly mean temperature by weather station.  
  Derived from daily weather observations and used for long‑term temperature trend analysis.

---

### Extreme Events

- **fact_extreme_events.csv**  
  Daily extreme weather events identified using station‑specific 95th percentile (P95) thresholds.

  This dataset includes:
  - Extreme Wind events
  - Heavy Precipitation events

  Each row represents a single extreme event at a given station and date.  
  Multiple events may occur on the same day for the same station and are stored as separate records by event type.

  This table supports frequency‑based analysis of extreme weather trends.

---

## Usage Notes

- All datasets are integrated into the Power BI model using shared dimension tables (Calendar, Station, Region).
- Fact tables in this folder are designed for analytical use and should not require additional cleaning.
- Temporary QA visuals were used during validation and removed after confirmation.
- Detailed processing logic, assumptions, and definitions are documented in the corresponding Data Dictionary files under `docs/Danielle/`.

---

## Status

All datasets in this folder are finalized and ready for analysis and reporting.

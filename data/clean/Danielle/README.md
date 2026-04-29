# Clean Data – Danielle Folder

This folder contains **cleaned and derived datasets** used in the analytical star schema and Power BI model.  
These datasets are suitable for **analysis, reporting, and visualization**.

---

## Datasets

### Monthly Precipitation by Station
- **File:** `fact_precipitation_monthly.csv`
- **Description:** Cleaned monthly total precipitation by weather station.
- **Granularity:** Station × Month
- **Source:** Derived from ECCC monthly climate observations.
- **Usage:**  
  Used for long-term precipitation trend analysis, year-over-year comparisons, and regional aggregation.

---

### Monthly Temperature by Station
- **File:** `monthly_temperature_by_station.csv`
- **Description:** Mean monthly temperature by weather station.
- **Granularity:** Station × Month
- **Source:** Aggregated from daily weather observations.
- **Usage:**  
  Used for temperature trend analysis and dual-axis visualization alongside precipitation.

---

## Usage Notes

- These datasets correspond directly to **fact tables documented in the Data Dictionary**.
- Technical keys (e.g., ClimateID, Date) are used for model relationships and may be hidden in the reporting layer.
- All data preparation and aggregation logic is documented in notebooks located under `scripts/python/Danielle/`.
- For assumptions and transformation details, refer to the data dictionary files under `docs/Danielle/`.

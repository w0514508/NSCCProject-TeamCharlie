# Raw Data – Danielle Folder

This folder contains **raw and minimally processed datasets** used as inputs for data cleaning, aggregation, and analytical modeling.  
These files are retained for **traceability and reproducibility** purposes.

---

## Datasets

### Monthly Precipitation – Atlantic Canada
- **File:** `precipitation_monthly_raw_atlantic.csv`
- **Source:** Environment and Climate Change Canada (ECCC)
- **Description:** Monthly climate observations containing total precipitation values by weather station.
- **Granularity:** Station × Month
- **Notes:**  
  This file represents the original monthly precipitation data prior to cleaning and validation.

---

### Daily Weather Dataset – Atlantic Climate
- **File:** `Atlantic_Climate.zip`
- **Source:** Environment and Climate Change Canada (ECCC)
- **Description:** Daily weather observations including temperature, precipitation, and wind variables.
- **Granularity:** Station × Day
- **Notes:**  
  This dataset was prepared at the team level and is used as the basis for monthly temperature aggregation and extreme weather event analysis.

---

## Usage Notes

- Files in this folder should **not be used directly for reporting or visualization**.
- All analytical use is based on cleaned or derived datasets located in the `data/clean` folder.
- Detailed cleaning steps and assumptions are documented in the corresponding notebooks and data dictionaries under `docs/Danielle/`.

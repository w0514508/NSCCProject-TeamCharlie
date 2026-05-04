# Danielle – Summary of Data, Scripts, and Documentation

This folder summarizes the **data assets, notebooks, and documentation** added to the repository under my folder.  
It serves as an index to locate datasets and supporting material used in the analytical model.

---

## Datasets

### Raw Data
- **Monthly Precipitation (Atlantic Canada)**  
  Source: Environment and Climate Change Canada (ECCC)  
  Location: `data/raw/Danielle/`

- **Daily Weather Dataset (Atlantic_Climate)**  
  Team-level daily weather data containing temperature, precipitation, and wind variables.  
  Table originally created by Yashaswi and used as a raw source for derived and aggregated datasets.  
  Location: `data/raw/Danielle/`

---

### Clean / Analytical Data
- **fact_precipitation_monthly.csv**  
  Monthly total precipitation by station, derived from daily observations.  
  Location: `data/clean/Danielle/`

- **fact_temperature_monthly.csv**  
  Monthly mean temperature by station, derived from daily weather observations.  
  Location: `data/clean/Danielle/`

- **fact_extreme_events.csv**  
  Daily extreme weather events identified using station-specific percentile thresholds (P95).  
  Includes extreme wind and heavy precipitation events, stored as individual event records.  
  Location: `data/clean/Danielle/`

---

## Scripts & Notebooks

- **Script for raw data download.ipynb**  
  Downloads monthly precipitation data from ECCC.

- **Precipitation Cleaning.ipynb**  
  Cleans, validates, and aggregates precipitation data.

- **Monthly_Temperature.ipynb**  
  Aggregates daily weather observations into monthly temperature by station.

- **Extreme_Events.ipynb**  
  Identifies extreme wind and heavy precipitation events using station-specific P95 thresholds and generates the final extreme events dataset.

All notebooks are located in:  
`scripts/python/Danielle/`

---

## Documentation

The following technical documents are available in this folder:

- **Data Dictionary – Climate & Environmental Star Schema**  
  Documents all fact and dimension tables in the model, including creation method and grain.

- **Data Dictionary – Precipitation Sources**  
  Source description, cleaning steps, and assumptions for precipitation data.

- **Data Dictionary – Monthly Temperature Sources**  
  Documentation of the monthly temperature derivation process.

- **Data Dictionary – Extreme Events**  
  Documentation of extreme wind and heavy precipitation event definitions, thresholds, assumptions, and processing steps.

- **Draft Star Schema Diagram**  
  Visual representation of the analytical star schema.

- **Scrum Notes (DOCX / PDF)**  
  Daily scrum tracking and task notes.

All documentation is located in:  
`docs/Danielle/`

---

## Notes

- All datasets in this folder are integrated into the Power BI data model using shared dimension tables.
- Fact tables are validated using temporary QA visuals to ensure dimensional integrity before final analysis.
- Power BI transformations are limited to relationship management, data type enforcement, and presentation-layer configuration.
- Detailed explanations for each dataset and processing step are provided in the corresponding data dictionary files.

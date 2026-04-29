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
  Team-level cleaned daily weather data containing temperature, precipitation, and wind variables.
  Table created by Yashaswi but used as a raw data to create an aggregated monthly.
  Location: `data/raw/Danielle/`

---

### Clean / Analytical Data
- **fact_precipitation_monthly.csv**  
  Monthly total precipitation by station.  
  Location: `data/clean/Danielle/`

- **fact_temperature_monthly.csv**  
  Monthly mean temperature by station, derived from daily weather observations.  
  Location: `data/clean/Danielle/`

---

## Scripts & Notebooks

- **Script for raw data download.ipynb**  
  Downloads monthly precipitation data from ECCC.

- **Precipitation Cleaning.ipynb**  
  Cleans and validates monthly precipitation data.

- **Monthly_Temperature.ipynb**  
  Aggregates daily weather observations into monthly temperature by station.

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

- **Draft Star Schema Diagram**  
  Visual representation of the analytical star schema.

- **Scrum Notes (DOCX / PDF)**  
  Daily scrum tracking and task notes.

All documentation is located in:  
`docs/Danielle/`

---

## Notes

- Fact_AQI and Fact_ExtremeEvents are currently included in the Power BI model as **dummy tables** for structural completeness.
- Power BI transformations are limited to relationship management, data type enforcement, and presentation-layer configuration.
- Detailed explanations for each dataset are provided in the corresponding data dictionary files.
``

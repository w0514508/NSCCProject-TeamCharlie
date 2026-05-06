# Raw Data — Danielle

## Overview

This folder contains the **raw input datasets** used in the generation of cleaned and analytical climate datasets related to **precipitation and extreme weather events** across Atlantic Canada.

These files represent **upstream data sources** and are not used directly for analysis or visualization.

---

## Contents

### ✅ fact_Atlantic_Climate.csv
Raw daily climate dataset derived from Environment and Climate Change Canada observations.

This dataset includes daily measurements for multiple climate variables (e.g., precipitation, wind, temperature) at the station level and serves as the **primary upstream source** for:

- Monthly aggregated precipitation data
- Extreme weather events (Extreme Wind and Heavy Precipitation)

This file is used during preprocessing and feature generation but is not consumed directly by the final PBIX model.

---

## Notes

- Daily climate data is retained here solely for reproducibility and traceability.
- All analytical datasets derived from this file are stored in `data/clean/Danielle`.
- Detailed documentation of the cleaned datasets and analytical logic is available in `docs/Danielle`.

---

## Relationship to Clean Data

Processed datasets generated from these raw inputs include:
- Monthly precipitation fact tables
- Extreme weather events fact tables

Refer to `data/clean/Danielle/README.md` for details on analysis-ready datasets.

# Clean Data — Danielle

## Overview

This folder contains the **final cleaned datasets and Power BI model** developed for the analysis of **precipitation patterns and extreme weather events** across Atlantic Canada.

All files in this directory are considered **analysis-ready** and are used directly in the final PBIX model and supporting exploratory analysis.

---

## Contents

### ✅ Fact_Extreme_Events_All.csv
Event-level dataset containing identified extreme weather events, including:
- Extreme Wind events
- Heavy Precipitation events

Extreme events are defined using **station-specific 95th percentile (P95) thresholds**, ensuring that extremes are relative to local historical conditions.

Each row represents a single extreme event occurrence.

📄 Detailed documentation:
- See `docs/Danielle/Data Dictionary — Extreme Events.md`

---

### ✅ fact_precipitation.csv
Monthly aggregated precipitation dataset derived from daily climate observations.

- One row per station per month
- Precipitation values expressed in millimeters (mm)
- Designed for climate-scale analysis rather than daily variability

This dataset is used to analyze:
- Long-term precipitation patterns
- Frequency-based indicators (e.g., wet months per year)

📄 Detailed documentation:
- See `docs/Danielle/Data Dictionary_Precipitation_sources.md`

---

### ✅ Precipitation_ExtremeEvents_Final.pbix
Power BI model containing:
- The analytical data model
- DAX measures
- Visualizations supporting the final findings on precipitation frequency and extreme events

The PBIX relies exclusively on the cleaned datasets in this folder and does not introduce additional data sources.

---

## Notes

- Daily climate data is used upstream during data processing but is not included in this folder.
- No forecasting or predictive modeling is performed in this PBIX.
- This folder is intended to support final analysis, review, and presentation.

---

## Relationship to Project Documentation

Conceptual documentation, data dictionaries, and the high-level star schema are maintained separately in:
- docs/Danielle/

That directory provides the **conceptual and architectural context** for the cleaned datasets and PBIX stored in this folder, including:
- Dataset-level data dictionaries
- Definitions of shared dimensions
- A conceptual overview of the climate and environmental star schema used across the project

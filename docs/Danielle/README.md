# Danielle — Precipitation and Extreme Events Analysis

## Overview

This folder contains the datasets, documentation, and analytical artefacts developed for the **Precipitation and Extreme Weather Events** component of the Atlantic Canada climate project.

The focus of this work is on **climate-scale patterns**, using aggregated precipitation data and event-based definitions of extreme weather to support exploratory analysis and visualization.

The analytical outputs are designed to be consumed through an individual Power BI model (PBIX), which will later be combined with the rest of the team’s work at the dashboard level.

---

## Analytical Scope

The datasets and analysis in this folder focus on:

- **Monthly precipitation patterns**
  - Long-term variability
  - Frequency-based indicators (e.g., wet months per year)

- **Extreme weather events**
  - Extreme Wind
  - Heavy Precipitation
  - Identified using station-specific 95th percentile (P95) thresholds

Daily climate observations are used upstream during data processing but **are not included** in the final analytical datasets.

---

## Final Datasets

The following datasets are considered **final and cleaned** for analysis:

### ✅ Fact_Precipitation_Monthly
- Monthly aggregated precipitation totals (mm)
- One row per station per month
- Used for long-term precipitation frequency and trend analysis

📄 Documentation:  
- `Data Dictionary_Precipitation_sources.md`

---

### ✅ Fact_Extreme_Events
- Event-level dataset containing extreme wind and heavy precipitation events
- Extreme events are defined using **station-specific P95 thresholds**
- Event magnitude and threshold interpretation depend on `EventType`

📄 Documentation:  
- `Data Dictionary — Extreme Events.md`

---

## Shared Dimensions and Conceptual Model

Several dimensions (e.g., Calendar, Station, Region) are shared across multiple datasets and analytical areas within the project.

A **conceptual overview of the climate and environmental star schema**, including shared dimensions and their relationship to different fact tables, is documented separately.

📄 Documentation:  
- `Data Dictionary_Climate & Environmental Star Schema.md`

🖼️ Visual reference:  
- `Draft_Star_schema.png`

> **Note:**  
> The star schema and associated data dictionary represent a **high-level conceptual architecture** of the project.  
> Not all tables shown in the schema appear in this individual analytical model. Each team member’s PBIX focuses on a subset of facts and dimensions relevant to their analysis.

---

## Power BI Model (PBIX)

The PBIX file associated with this work contains:
- The analytical data model
- DAX measures
- Visualizations supporting precipitation and extreme event findings

The PBIX relies exclusively on the cleaned datasets documented above.  
No additional datasets are introduced at the visualization layer.

---

## Folder Contents

- `Data Dictionary_Precipitation_sources.md`
- `Data Dictionary — Extreme Events.md`
- `Data Dictionary_Conceptual Climate & Environmental Star Schema.md`
- `Conceptual_Climate_Star_Schema.png`
- Scrum notes documenting weekly progress
- README (this file)

---

## Intended Use

This documentation supports:
- Dataset consolidation at the team level
- Review by instructors and project stakeholders
- Maintenance and handoff of analytical assumptions and definitions

It is not intended as:
- A complete documentation of the Power BI interface
- A visual or presentation script
- A predictive or forecasting specification

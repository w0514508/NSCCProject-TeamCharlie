# Data Dictionary – Conceptual Climate & Environmental Star Schema — Shared Dimensions

This document describes the structure of the ** Conceptual Climate & Environmental analytical data model**, which follows a **star schema design**.  
It documents all **dimension and fact tables**, including their **grain, purpose, key columns, and creation method**.

The model is designed to support climate trend analysis, extreme event assessment, and environmental context reporting.

Note: This document represents a conceptual overview of the climate and environmental star schema used across the project. Not all tables shown here appear in every individual PBIX model. Each team member’s analytical model focuses on a subset of these facts and dimensions.

---

## Model Overview

The star schema separates:
- **Raw daily observations** used for derivations and analysis
- **Monthly fact tables** optimized for trend reporting
- **Contextual environmental facts** (AQI and GHG)
- **Shared dimensions** for time, location, and geography

Differences in granularity and coverage reflect real-world data availability.

---

## Dimension Tables

---

### Dim_Calendar

**Creation method:** DAX (Power BI calculated table)  
**Grain:** One row per calendar date (monthly granularity used as the primary key for facts)

**Purpose:**  
Shared time dimension used across all fact tables to enable monthly, yearly, and seasonal analysis.

| Column | Type | Description |
|------|------|-------------|
| Date | Date | Reference date (first day of month or year, depending on fact) |
| Year | Integer | Calendar year |
| Month | Integer | Calendar month (1–12) |
| YearMonth | Text | Time key in YYYY-MM format |
| MonthName | Text | Month name |
| Season | Text | Climatic season (Winter, Spring, Summer, Fall) |

---

### Dim_Station

**Creation method:** CSV source cleaned in Python  
**Grain:** One row per weather station

**Purpose:**  
Provides station-level geographic context for meteorological facts.

| Column | Type | Description |
|------|------|-------------|
| ClimateID | Text | Official weather station identifier |
| StationName | Text | Weather station name |
| Latitude | Decimal | Geographic latitude |
| Longitude | Decimal | Geographic longitude |
| ProvinceCode | Text | Province code (NS, NB, PE, NL, etc.) |

---


## Dim_Region

**Creation method:** DAX (Power BI calculated table)  
**Grain:** One row per Canadian province or territory  

### Purpose
Represents the full Canadian geographic domain and provides **analytical grouping levels** to support regional aggregation and benchmarking (apexing) across temperature, precipitation, AQI, and GHG datasets.  
This dimension enables comparisons at multiple scopes, including **province**, **Atlantic Canada**, **Rest of Canada**, and **All Canada**, without duplicating fact tables.

---

### Columns

| Column | Type | Description |
|------|------|-------------|
| RegionID | Integer | Surrogate key |
| ProvinceCode | Text | Province or territory code |
| RegionName | Text | Full province or territory name |
| MacroRegion | Text | Analytical grouping used for benchmarking (e.g., Atlantic Canada, Rest of Canada) |
| CountryScope | Text | Country-level scope used for national benchmarks (Canada) |


---

### Notes
- `MacroRegion` is used to support **regional benchmarking**, such as Nova Scotia vs Atlantic Canada or Atlantic Canada vs Rest of Canada.
- `CountryScope` enables **All Canada** aggregation where national-level comparisons are supported (e.g., temperature and GHG).
- Not all fact tables have full national coverage. For example, **precipitation analysis is scoped to Atlantic Canada**, consistent with the project charter and data availability.
- This design supports semantic aggregation in the reporting layer without altering the underlying fact tables.

---

## Fact Tables

---

### Fact_Weather_Daily

**Creation method:** CSV source cleaned in Python  
**Grain:** Weather station × day

**Purpose:**  
Contains raw daily meteorological observations used for anomaly analysis, extreme event derivation, and aggregation to monthly facts.

| Column | Description |
|------|-------------|
| ClimateID | Weather station identifier |
| DateTime | Date of daily observation |
| MaxTemp_C | Daily maximum temperature |
| MinTemp_C | Daily minimum temperature |
| MeanTemp_C | Daily mean temperature |
| HeatDegDays | Heating degree days |
| CoolDegDays | Cooling degree days |
| TotalRain_mm | Daily rainfall |
| TotalSnow_cm | Daily snowfall |
| TotalPrecip_mm | Total daily precipitation |
| SnowOnGround_cm | Snow on ground |
| MaxGustDir_deg | Direction of maximum wind gust |
| MaxGustSpeed_kmh | Speed of maximum wind gust |

---

### Fact_Temperature_Monthly

**Creation method:** Python aggregation from daily weather data  
**Grain:** Weather station × month

**Purpose:**  
Supports long-term temperature trend analysis, year-over-year comparison, and dual-axis reporting with precipitation.

| Column | Description |
|------|-------------|
| ClimateID | Weather station identifier |
| Date | Monthly reference date (YYYY-MM-01) |
| MeanMonthlyTemp_C | Mean monthly temperature (°C) |

---

### Fact_Precipitation_Monthly

**Creation method:** CSV source cleaned in Python  
**Grain:** Weather station × month

**Purpose:**  
Supports long-term precipitation trend analysis and regional comparison.

| Column | Description |
|------|-------------|
| ClimateID | Weather station identifier |
| Date | Monthly reference date (YYYY-MM-01) |
| Precipitation_mm | Total monthly precipitation (mm) |
| ProvinceCode | Province code |

---

### Fact_GHG

**Creation method:** CSV source cleaned in Python  
**Grain:** Province × Year

**Purpose:**  
Provides environmental and industrial context through historical greenhouse gas (GHG) emissions at the provincial level.  
This dataset supports long‑term trend analysis and complements climate indicators such as temperature, precipitation, and AQI.

| Column | Description |
|------|-------------|
| ProvinceCode | Province identifier (e.g., NS, ON, QC) |
| Year | Reporting year |
| GHG_Emissions | Total greenhouse gas emissions for the province |
| Unit | Unit of measurement (e.g., megatonnes CO₂ equivalent) |

This fact table is joined to **Dim_Region** using `ProvinceCode` and to **Dim_Calendar** using `Year`.

---

### Fact_AQI (Dummy)

**Creation method:** DAX (Power BI dummy table)  
**Grain:** Region × month

**Purpose:**  
Placeholder table used to illustrate the integration of air quality indicators into the analytical model.

| Column | Description |
|------|-------------|
| RegionCode | Region or province code |
| Date | Monthly reference date |
| AQI_Value | Air Quality Index value |
| AQI_Category | Qualitative air quality category |

⚠️ This table is currently a **dummy** and will be replaced with a cleaned dataset when available.

---

### Fact_ExtremeEvents (Dummy)

**Creation method:** DAX (Power BI dummy table)  
**Grain:** Weather station × period × event type

**Purpose:**  
Illustrates the structure required to analyze trends in extreme weather events derived from daily observations.

| Column | Description |
|------|-------------|
| ClimateID | Weather station identifier |
| Date | Reference date |
| EventType | Type of extreme event |
| EventCount | Number of events |

⚠️ This table is currently a **dummy** and serves as a structural placeholder.

---

## Notes

- All tables included in the Power BI model are documented here, including those created using DAX.
- Differences in granularity and geographic coverage reflect real-world data availability.
- Contextual and dummy tables are clearly identified to avoid analytical ambiguity.

---
``

Extreme Events - Sources, Cleaning, and Assumptions

## Overview

This document describes the structure, sources, and processing logic used to identify and analyze extreme weather events in the Atlantic Canada climate dataset. Extreme events are derived from daily observations and are designed to support frequency-based trend analysis rather than intensity aggregation.

---

## Data Sources

### Daily Climate Data

- **Source:** Environment and Climate Change Canada (ECCC)
- **Files:**
  - `fact_Atlantic_Climate.csv` (raw daily observations)
- **Spatial Scope:** Atlantic Canada weather stations
- **Temporal Scope:** Historical daily records (multi-decadal coverage)

---

## Fact Table: Fact_Extreme_Events

### Purpose
The `Fact_Extreme_Events` table captures statistically extreme weather events at the daily level. Each record represents a single extreme event occurring at a specific station on a given date.

This fact table supports analysis of **event frequency**, spatial distribution, and long-term trends.

---

### Grain
- **One row per extreme event**
- Identified by:
  - `ClimateID`
  - `Date/Time`
  - `EventType`

Multiple extreme events may occur at the same station on the same date and are stored as separate records.

---

### Event Definition

Extreme events are defined using **station-specific percentile thresholds** to ensure comparability across locations with different climatological baselines.

#### Extreme Wind
- Definition:  
  Daily maximum wind gust ≥ **95th percentile (P95)** of historical wind gusts for that station
- Source variable:
  - Daily maximum gust speed (km/h)

#### Heavy Precipitation
- Definition:  
  Daily total precipitation ≥ **95th percentile (P95)** of historical daily precipitation totals for that station
- Source variable:
  - Daily total precipitation (mm)

Percentile thresholds are computed using the full historical distribution of each station’s daily observations.

---

### Columns

| Column Name     | Type    | Description |
|-----------------|---------|-------------|
| ClimateID       | Text    | Unique identifier for the weather station |
| Date/Time       | Date    | Date on which the extreme event occurred |
| EventType       | Text    | Identifies the type of extreme event. Determines how EventValue and P95_Threshold should be interpreted (wind speed for Extreme Wind, precipitation for Heavy Precipitation) |
| EventValue      | Decimal | Observed magnitude of the extreme event. Represents daily precipitation (mm) for Heavy Precipitation events and wind gust speed (km/h) for Extreme Wind events. Interpretation depends on EventType |
| P95_Threshold*  | Decimal | Station-specific 95th percentile threshold used to identify the event |
| ExtremeFlag     | Integer | Binary indicator (1 = extreme event) |

*For Heavy Precipitation events, this represents the daily precipitation threshold (mm).
*For Extreme Wind events, this represents the wind gust speed threshold (km/h).
*Interpretation of this field depends on EventType.
---

## Data Processing Logic

1. Daily observations are filtered to remove missing values.
2. Station-specific P95 thresholds are calculated using historical daily distributions.
3. Extreme events are identified where observed values exceed or equal the P95 threshold.
4. Events are stored as individual records and appended vertically by event type.
5. Records are enriched via dimension tables (Station, Region, Calendar) during Power BI integration.

No temporal aggregation is applied within this table.

---

## Integration with Dimensional Model

The `Fact_Extreme_Events` table is integrated into the star schema using the following relationships:

- `ClimateID` → `Dim_Station`
- `Date` → `Dim_Calendar`

Geographic attributes (e.g., Province, Region) are resolved through dimension joins rather than stored directly in the fact table.

---

## Analytical Notes

- Extreme events are analyzed using **frequency counts**, not summed intensity.
- Percentile-based thresholds provide a robust, location-aware definition of “extreme.”
- This structure supports:
  - Trend analysis over time
  - Comparison between wind and precipitation extremes
  - Filtering by region (e.g., Nova Scotia stations)

---

## QA and Validation

All extreme event records were validated in Power BI using temporary QA visuals to confirm:
- Absence of blank station or region values
- Correct reapplication of station merges after data append
- Plausible spatial and temporal distributions of events

Temporary QA visuals were removed after validation.

---

## Design Decisions

- Extreme events are stored in a single fact table and differentiated by event type.
- The fact table grows vertically (append-only) as new event types are added.
- Station-level percentile thresholds are preferred over fixed cut-offs to reduce geographic bias.

---

## Assumptions

The following assumptions were made to support the identification and analysis of extreme weather events:

- Daily climate observations are assumed to be sufficiently complete and reliable for percentile-based threshold calculation after standard cleaning and removal of missing values.

- Station-specific historical distributions are assumed to represent an appropriate baseline for defining statistical extremes at each location.

- Extreme events are defined relative to a station’s own climatology (percentile-based) rather than using fixed absolute thresholds, under the assumption that local variability provides a more meaningful definition of rarity.

- Multiple extreme events may occur at the same station on the same date (e.g., extreme wind and heavy precipitation) and are treated as distinct events.

- Event frequency is the primary analytical focus; intensity values are stored for context but are not aggregated or summed.

- Partial years at the end of the time series may contain incomplete records and should be interpreted with caution in trend analysis.

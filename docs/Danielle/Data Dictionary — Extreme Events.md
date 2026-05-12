# 📘 Data Dictionary — Extreme Events

## Table: `Fact_Extreme_Events`

### Table Description

`Fact_Extreme_Events` is an **event-level fact table** containing all identified **extreme weather events** (extreme wind and heavy precipitation) observed at weather stations across Atlantic Canada.

An extreme event is defined using a **station-specific 95th percentile threshold**, meaning this table includes **only rare tail events**, not regular daily observations.

The table is intentionally modeled as a **single unified fact table**, with event type handled as a categorical attribute, rather than separate tables for wind and precipitation. This design supports consistent frequency-based analysis and clean BI reporting.

---

## Grain

**One row per extreme weather event**, per station, per date.

Each row represents a single instance where an observed value exceeded the station-specific extreme threshold.

---

## Columns

### `Date`
- **Type:** Date  
- **Description:** Calendar date on which the extreme event occurred.
- **Usage:** Primary temporal key; joins to `Dim_Calendar[Date]`.

---

### `ClimateID`
- **Type:** String  
- **Description:** Unique identifier for the weather station where the extreme event was observed.
- **Usage:** Foreign key linking to `Dim_Station`.

---

### `EventType`
- **Type:** Categorical (String)  
- **Description:** Type of extreme weather event.
- **Possible values:**
  - `Extreme Wind`
  - `Extreme Precipitation`
- **Notes:** Differentiates event categories within a single fact table.

---

### `EventValue`
- **Type:** Numeric  
- **Description:** Observed wind speed or precipitation amount associated with the extreme event.
- **Notes:** Used for validation and distribution analysis; not used as the primary BI metric.

---

### `P95_Threshold`
- **Type:** Numeric  
- **Description:** Station-specific 95th percentile threshold used to classify an observation as an extreme event.
- **Notes:** Threshold values are computed upstream during the extreme-event identification process and stored directly in the fact table. They are used in the EDA phase for validation and interpretation, not recalculated.

---

### `ExtremeFlag`
- **Type:** Integer (Boolean)  
- **Description:** Indicator confirming that the record represents an extreme event.
- **Value:** Always `1` in this table.
- **Notes:** Included for transparency and lineage purposes, explicitly documenting that all records in the table correspond to pre-identified extreme events.


---

## Intended Analytical Use

This fact table is designed to support:

- Annual frequency of extreme events  
- Frequency by event type  
- Temporal trend analysis  
- Composition analysis of extreme events (wind vs precipitation)

The table is **not intended** for forecasting event magnitude or analyzing non-extreme conditions.

---

## Time Scope

- Analysis includes **complete calendar years only**, from **1995 through 31/12/2025**.
- Partial-year data beyond this cutoff are intentionally excluded to prevent temporal bias in frequency analysis.

---

## Assumptions & Limitations

- The table contains **only extreme events**; non-extreme daily observations are excluded by design.
- Results reflect **observed frequency changes**, not causal relationships.
- Earlier years may underrepresent true event frequency due to changes in data collection and observation practices.

---

## Modeling Notes

- `Fact_Extreme_Events` is the **canonical fact table** for extreme weather events.
- No surrogate event key is required, as each row represents a distinct event defined by date, station, and event type.
- Aggregations (e.g., annual counts) are implemented through BI measures rather than stored summary tables.

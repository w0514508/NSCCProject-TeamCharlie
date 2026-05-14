# 📘 DAX Measure Dictionary — Precipitation & Extreme Events

This document describes all DAX measures used in the Power BI model.  
Measures are documented with a focus on **analytical intent**, **data grain**, and **appropriate usage**, rather than DAX syntax.

---

## 🌧️ Precipitation Measures

### `Monthly Precipitation (mm)`
- **Description:** Total precipitation aggregated across all stations.
- **Grain:** Monthly (Year / Month).
- **Purpose:** Base measure for precipitation analysis, including averages, anomalies, and wet‑month indicators.

---

### `Avg Monthly Precipitation (mm)`
- **Description:** Average monthly precipitation across all locations.
- **Grain:** Monthly.
- **Purpose:** Describes typical monthly precipitation behavior.
- **Notes:** Serves as a building block for annual averages and anomaly calculations.

---

### `Long-Term Avg Monthly Precipitation (mm)`
- **Description:** Long-term historical average precipitation for each calendar month.
- **Grain:** Monthly, aggregated across all years (1995–2025).
- **Purpose:** Baseline used to classify months as below, normal, or above average.

---

### `Monthly Precipitation Anomaly (mm)`
- **Description:** Difference between observed monthly precipitation and the long-term monthly average.
- **Grain:** Monthly.
- **Interpretation:** Positive values indicate wetter-than-normal months; negative values indicate drier-than-normal months.
- **Purpose:** Analyzes changes in precipitation behavior relative to historical norms.

---

### `Avg Annual Precipitation (mm)`
- **Description:** Average of annual total precipitation across all available years.
- **Grain:** Annual (derived from monthly data).
- **Purpose:** Provides high-level climate context.
- **Limitations:** Not used to analyze extremes or variability.

---

### `Wet Month Flag (Regional)`
- **Description:** Flags whether a calendar month qualifies as a wet month.
- **Logic:** Monthly precipitation exceeds the long-term monthly baseline.
- **Output:** 1 = wet month, 0 = not wet.
- **Purpose:** Building block for frequency-based precipitation indicators.

---

### `Wet Months per Year`
- **Description:** Counts the number of wet months within each calendar year.
- **Grain:** Annual (derived by explicitly constructing monthly context).
- **Purpose:** Converts precipitation magnitude into an interpretable regime indicator.
- **Notes:** Monthly grain is explicitly enforced to ensure correct evaluation context.

---

## 🌪️ Extreme Events — Core Frequency Measures

### `Total Extreme Events`
- **Description:** Total number of extreme weather events in the dataset.
- **Grain:** Event-level (no implicit time aggregation).
- **Purpose:** Overall context, validation, and reference for composition analysis.

---

### `Extreme Events (Annual)`
- **Description:** Annual frequency of extreme weather events.
- **Grain:** Annual.
- **Logic:** Counts events while preserving only the Year context.
- **Purpose:** Primary metric for long-term extreme event trend analysis.

---

### `Extreme Events – Latest Year`
- **Description:** Number of extreme events in the most recent complete year.
- **Grain:** Annual (latest year only).
- **Purpose:** Snapshot KPI providing current context alongside long-term trends.
- **Notes:** Calendar filters are removed to ensure stability.

---

## 🌪️ Extreme Events — By Type

### `Extreme Precipitation Events`
- **Description:** Counts extreme events classified as Heavy Precipitation.
- **Grain:** Event-level.
- **Purpose:** Analyzes the frequency of precipitation-driven extreme events.
- **Usage:** Supports comparison with wind-related extremes.

---

### `Extreme Wind Events`
- **Description:** Counts extreme events classified as Extreme Wind.
- **Grain:** Event-level.
- **Purpose:** Analyzes the frequency of wind-driven extreme events.
- **Usage:** Complements precipitation extremes and overall trends.

---

### `Total Extreme Events by Type`
- **Description:** Total number of extreme events within the current EventType context.
- **Grain:** Event-level.
- **Purpose:** Absolute composition analysis by extreme event category.
- **Important:** Meaningful only when EventType is present in the visual or filter context.

---

### `Extreme Event Share (%)`
- **Description:** Proportion of extreme events by event type.
- **Logic:** Event count in current EventType context divided by total extreme event count.
- **Purpose:** Composition analysis (e.g., Wind vs Precipitation).
- **Important:** Requires EventType to be present; otherwise returns 100% by definition.

---

## 📈 Extreme Events — EDA Integration

### `Total Extreme Events (Observed)`
- **Description:** Observed annual extreme event counts generated during Python EDA.
- **Source:** `ExtremeEvents_Per_Year` table.
- **Purpose:** Baseline series representing raw, observed event frequencies.
- **Notes:** No aggregation or modelling performed in Power BI.

---

### `Extreme Events Trend (Fitted)`
- **Description:** Fitted trend values generated during Python EDA.
- **Source:** `ExtremeEvents_Per_Year` table.
- **Purpose:** Visual comparison between observed event counts and long-term trend.
- **Important:** Power BI performs no modelling; it only visualizes EDA outputs.

---

## ✅ General Notes

- All measures are **explicit**, not implicit visual aggregations.
- Measures respect the **grain of their underlying fact tables**.
- Power BI is used as a **consumption and integration layer**, not for analytical modelling.
- Predictive or causal modelling is intentionally handled upstream in Python.

``

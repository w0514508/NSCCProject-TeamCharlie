
# NSCC Capstone Project on Environment & Climate Analytics by TeamCharlie

## Description
This repository contains deliverables and source code for Team Charlie's NSCC project.

This project analyzes historical climate and environmental trends in Atlantic Canada using open data from Environment and Climate Change Canada (ECCC), with a focus on temperature, precipitation, air quality, and greenhouse gas emissions.

## Team Members
- Yashaswi Tiwari
- Chisom Njoku
- Tracy Odaro
- Danielle Aranha
- Michael Okafor

## Folder Structure
- data/raw/ – Original datasets
- data/clean/ – Processed datasets
- scripts/sql/ – SQL scripts
- scripts/python/ – Python scripts
- reports/ – Final reports and outputs

## Work Responsibilities - 4 Topic Areas

---

# Average Temperatures  
**Owner:** Yashaswi Tiwari  

- **Goal**
  - Analyze how average temperature patterns have changed in Atlantic Canada over the past 30 years
  - Focus on Nova Scotia weather stations

- **Dashboard Elements**
  - **KPI Card**
    - Average Annual Temperature
  - **Slicers**
    - Year
    - Station
  - **Visuals**
    - Line Chart
      - Average annual temperature trend
    - Heatmap Calendar
      - Daily temperature anomalies
    - Bar Chart
      - Year-over-year temperature change
    - Forecast Visualization
      - Average annual temperature forecast for the next 5 years
      - Selected Nova Scotia weather station
      - Python model overlay
    - Anomaly Chart
      - Deviation from 30-year baseline
      - Confidence bands

- **Python / Pandas Analysis**
  - Exploratory Data Analysis (EDA)
  - Temperature anomaly calculation
    - Compared to 30-year baseline
  - Trend modeling
    - Linear regression or polynomial fit
  - Forecasting
    - Short-term temperature forecasting using a simple ARIMA model

---

# Average Precipitation & Extreme Weather Events  
**Owner:** Danielle Aranha  

- **Goal**
  - Analyze precipitation pattern changes in Atlantic Canada over the past 30 years
  - Identify trends in extreme weather events

- **Dashboard Elements**
  - **KPI Card**
    - Annual Precipitation
  - **Slicers**
    - Year
    - Station
  - **Visuals**
    - Dual-Axis Line Chart
      - Average temperature
      - Average precipitation over decades
    - Bar Chart
      - Year-over-year precipitation change
    - Extreme Weather Event Analysis
      - High wind event frequency
      - Heavy precipitation event frequency
    - Trend Chart
      - Extreme weather event frequency over time
    - Anomaly Chart
      - Deviation from 30-year baseline
      - Confidence bands

- **Python / Pandas Analysis**
  - Precipitation frequency analysis
  - Detection of measurable trends in extreme weather events
  - Export Outputs
    - Anomaly values as CSV
    - Forecast series as CSV for Power BI

---

# Greenhouse Gas (GHG) Emissions  
**Owner:** Michael Okafor  

- **Goal**
  - Analyze changes in GHG emissions over the past decade
  - Identify provinces or regions with the greatest change

- **Dashboard Elements**
  - **KPI Card**
    - Nova Scotia GHG Change (%)
  - **Slicers**
    - Year
    - Province / Region
  - **Visuals**
    - Stacked Area Chart
      - GHG emissions by province over time
    - Bar Chart
      - Nova Scotia emissions by sector
    - Line Chart
      - Nova Scotia vs national (Canada-wide) target trend

---

# Air Quality Index (AQI)  
**Owner:** Chisom Njoku  

- **Goal**
  - Analyze AQI trends
  - Examine correlations with seasonal patterns and industrial activity

- **Dashboard Elements**
  - **KPI Card**
    - AQI Index
  - **Slicers**
    - Year
    - Monitoring Station
  - **Visuals**
    - Line Chart
      - AQI over time by monitoring station
    - Bar Chart
      - Days exceeding AQI threshold by month
    - Map Visualization
      - AQI monitoring station locations
      - Color-coded AQI values

- **Data Analysis**
  - Correlation Analysis
    - AQI vs seasonal (monthly) patterns
    - AQI vs wind direction and wind speed
  - Export Outputs
    - Anomaly values as CSV
    - Forecast series as CSV for Power BI
``

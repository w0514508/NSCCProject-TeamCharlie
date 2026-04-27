
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

- Average Temperatures
Owner: Yashaswi Tiwari

Goal:
Analyze how average temperature patterns have changed in Atlantic Canada over the past 30 years, with focus on Nova Scotia weather stations.
Dashboard Elements:

KPI Card:

Average Annual Temperature


Slicers:

Year
Station



Visuals:

Line chart showing average annual temperature trend
Heatmap calendar displaying daily temperature anomalies
Bar chart showing year-over-year temperature change
Forecast visualization showing average annual temperature for the next 5 years for a selected NS weather station with Python model overlay
Anomaly chart showing deviation from the 30-year baseline with confidence bands

Python / Pandas Analysis:

Exploratory Data Analysis (EDA)
Temperature anomaly calculation compared to 30-year baseline
Trend modeling using linear regression or polynomial fit
Short-term temperature forecasting using a simple ARIMA model



- Average Precipitation & Extreme Weather Events
Owner: Danielle Aranha

Goal:
Analyze precipitation pattern changes in Atlantic Canada over the past 30 years and identify trends in extreme weather events.
Dashboard Elements:

KPI Card:

Annual Precipitation


Slicers:

Year
Station



Visuals:

Dual-axis line chart showing average temperature and precipitation over decades
Bar chart showing year-over-year precipitation change
Extreme weather event frequency analysis focusing on:

High wind events
Heavy precipitation events


Trend chart showing frequency of extreme weather events over time
Anomaly chart showing deviation from 30-year baseline with confidence bands

Python / Pandas Analysis:

Precipitation frequency analysis
Identification of measurable trends in extreme weather events
Export of anomaly values and forecast series as CSV files for Power BI



- Greenhouse Gas (GHG) Emissions
Owner: Michael Okafor

Goal:
Analyze changes in greenhouse gas emissions over the past decade and identify provinces or regions with the greatest change.
Dashboard Elements:

KPI Card:

Nova Scotia GHG Change (%)


Slicers:

Year
Province / Region



Visuals:

Stacked area chart showing GHG emissions by province over time
Bar chart showing Nova Scotia emissions by sector
Line chart comparing Nova Scotia emissions against the national (Canada-wide) emissions target trend



- Air Quality Index (AQI)
Owner: Chisom Njoku

Goal:
Analyze AQI trends and examine correlations with seasonal patterns and industrial activity.
Dashboard Elements:

KPI Card:

AQI Index


Slicers:

Year
Monitoring Station



Visuals:

Line chart showing AQI over time by monitoring station
Bar chart showing number of days exceeding AQI thresholds by month
Map visualization showing AQI monitoring station locations with color-coded AQI values

Data Analysis:

Correlation analysis between AQI and seasonal (monthly) patterns
Correlation analysis between AQI and wind direction and wind speed from weather stations
Export of anomaly values and forecast series as CSV files for Power BI

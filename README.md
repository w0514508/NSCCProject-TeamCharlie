
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

-1. Average temperatures: ( Yashaswi Tiwari)
patterns changed in Atlantic Canada over the past 30 years
1 KPI cards with Year and station slicers.- 1- Avg Annual Temp (trend),
Heatmap calendar: daily temperature anomalies. 
Bar: year-over-year change.
forecast average annual temperature for a selected NS weather station for the next 5 years
Temperature trend forecast with Python model overlay. 
 Anomaly chart: deviation from 30-year baseline. Confidence bands.
Pandas EDA: temperature anomaly calculation vs. 30-year baseline, 
Linear regression or polynomial fit for temperature trend; simple ARIMA for short-term temperature forecasting
 
-2. Avg precipitation  & Extreme weather event (Danielle Aranha)
patterns changed in Atlantic Canada over the past 30 years
1 KPI cards with Year and station slicers.-- Annual Precipitation,
Dual-axis line chart: average temp and precipitation over decades. 
Bar: year-over-year change.
Extreme Weather event frequency and forecast : figure out if there a measurable trend in extreme weather event frequency ( high wind, heavy precipitation) at NS weather stations
Showcase trend in extreme weather event frequency 
Anomaly chart: deviation from 30-year baseline. Confidence bands.
Pandas EDA: precipitation frequency analysis
Export: anomaly values and forecast series as CSV for Power BI
 
-3. GHG emissions (Michael Okafor)
Change in GHG emissions over the past decade, show which provinces or regions show the greatest change
KPI card- NS GHG Change %. Year and station slicers
Stacked area chart: GHG by province over time
Bar chart: NS emissions by sector.
Line: NS vs. national (all Canada) target trend.

-4. Air quality index (AQI) -(Chisom Njoku)
KPI Card - AQI Index, Year and Station Slicer
Correlations of AQI with seasonal patterns and industrial activity
Line chart: AQI over time by monitoring station. 
Bar: days exceeding threshold by month. 
Map: station locations with AQI colour coding.
Correlation analysis: AQI vs. seasonal month, AQI vs. wind direction/speed from weather stations
Export: anomaly values and forecast series as CSV for Power BI

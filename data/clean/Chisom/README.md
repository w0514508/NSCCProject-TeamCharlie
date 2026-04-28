
## https://search.open.canada.ca/opendata/?search_text=air+quality 

The raw data used in this project was downloaded from the Government of Canada Open Data Portal, specifically from the air quality datasets available at:
A total of five(5) CSV files were selected from this source, each representing air‑quality measurements for different pollutants and monitoring stations in Nova Scotia.
These files were cleaned individually by:
- Removing null and invalid values
- Standardizing column names and structure
After cleaning, the datasets were appended into a single staging table, which served as the consolidated raw layer for further analysis.

### The raw data used in this project consists of ambient air‑quality measurements collected from multiple monitoring stations across Nova Scotia.
### These datasets were first standardized and cleaned into a staging table, which serves as the structured raw layer for further analysis.
### The staging table includes observations for three pollutants and five monitoring stations, with records spanning 1995 to 2025, depending on data availability by pollutant and station.

#### Pollutant      Record Count
- O3              549881
- NO2             436229
- SO2             41960

#### For Stations 
Station
- Sydney             436229
- Aylesford          240895
- Pictou             183800
- Port Hawkesbury    125186
- Sable Island        41960

#### From the staging table, a final clean dataset was created specifically for AQI‑focused analysis and it contains validated daily air‑quality records for O₃ (Ozone) and NO₂ (Nitrogen Dioxide) within the 2015–2025 reporting window.

#### Pollutant Coverage (Daily Records)
- O₃ (Ozone): 10,939 records
- NO₂ (Nitrogen Dioxide): 3,561 records

#### Station Coverage (Daily Records)
- Aylesford: 3,648
- Port Hawkesbury: 3,646
- Pictou: 3,645
- Sydney: 3,561

#### Sable Island and SO₂ is not present in the final clean dataset due to the absence of Sable Island and SO₂ observations within the selected 2015–2025 time period.

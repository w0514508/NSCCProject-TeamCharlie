## Final Temperature Data tables for data model
---
## Data is downloaded from https://dd.weather.gc.ca/today/climate/observations/daily/csv/
  - Original Station list count- 8612
    - Total Atlantic count - 917
      - NB : 229
      - NS : 307
      - NL : 326
      - PE : 55
    - Clean Data list - 137
      - NB : 27
      - NS : 52
      - NL : 50
      - PE : 8
- Total Yearwise Files downloaded (2787)
  - NB - 588 files
  - NS : 951 Files
  - NL : 1040 Files
  - PE : 208 Files

## 🇨🇦 Canada — Air Pollutant Averaging Times

This table summarizes the recommended averaging periods used in **Canada**, aligned with
the **Air Quality Health Index (AQHI)** and **Canadian Ambient Air Quality Standards (CAAQS)**.

| Pollutant | AQHI Averaging Time | Regulatory / Reporting Averaging Time | Notes |
|----------|--------------------|----------------------------------------|-------|
| PM₂.₅ | **3‑hour rolling average** | **24‑hour average**, Annual average | Core AQHI pollutant; cumulative exposure important |
| PM₁₀ | — | **24‑hour average** | Not part of AQHI; limited health indexing use |
| O₃ (Ozone) | **3‑hour rolling average** | **8‑hour rolling average** | AQHI uses short‑term risk; CAAQS uses 8‑hr exposure |
| CO | — | **1‑hour & 8‑hour averages** | Acute + multi‑hour exposure monitoring |
| NO | — | **1‑hour average** | Short‑lived; emissions indicator |
| NO₂ | **3‑hour rolling average** | **1‑hour average**, Annual average | AQHI core pollutant; strong acute respiratory effects |
| NOₓ | — | **1‑hour average** | Emissions & photochemistry tracking |
| SO₂ | — | **1‑hour average**, 24‑hour average | Short‑term irritation risk near sources |

### Notes
- Canada uses the **Air Quality Health Index (AQHI)** rather than a single‑pollutant AQI.
- AQHI is calculated from **PM₂.₅, O₃, and NO₂ only**, using **rolling 3‑hour averages**.
- Other pollutants are monitored and regulated but do **not** directly drive AQHI values.

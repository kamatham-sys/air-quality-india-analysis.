# Project Documentation

## 1. Objective

Analyse daily air quality data from 26 Indian cities (2015-2020) to:
- Identify the cities with the worst air quality
- Understand seasonal patterns
- Find which pollutants relate most strongly to AQI
- Test whether the 2020 COVID-19 lockdown reduced pollution

## 2. Dataset Description

| Column | Description |
|--------|-------------|
| City | Name of the city |
| Date | Date of the reading |
| PM2.5, PM10 | Particulate matter (ug/m3) |
| NO, NO2, NOx | Nitrogen oxides |
| NH3 | Ammonia |
| CO | Carbon monoxide |
| SO2 | Sulphur dioxide |
| O3 | Ozone |
| Benzene, Toluene, Xylene | Volatile organic compounds (dropped in cleaning) |
| AQI | Air Quality Index value |
| AQI_Bucket | Category: Good, Satisfactory, Moderate, Poor, Very Poor, Severe |

## 3. Data Cleaning

| Step | Action | Reason |
|------|--------|--------|
| 1 | Convert `Date` to datetime | Enables time-based analysis |
| 2 | Drop Benzene, Toluene, Xylene | Too many missing values |
| 3 | Drop rows with missing AQI and AQI_Bucket | Target variable must be present |
| 4 | Check for duplicates | None found |
| 5 | Fill missing pollutants with **city-wise median** | Pollution levels differ by city; median resists outliers |
| 6 | Fill remaining gaps (PM10, NOx, NH3, O3) with overall median | Some cities had no readings for these |
| 7 | Save as `cleaned_data.csv` | Reusable cleaned dataset |

Result: 29,531 rows reduced to 24,850 rows, 16 columns reduced to 13.

## 4. Feature Engineering

| New column | Logic |
|------------|-------|
| Year, Month, Month_Name, Day_of_Week | Extracted from Date |
| Season | Winter (Dec-Feb), Summer (Mar-May), Monsoon (Jun-Sep), Post-Monsoon (Oct-Nov) |
| Period | Pre-Lockdown (before 25 Mar 2020), Lockdown (25 Mar - 31 May 2020), Post-Lockdown (after 31 May 2020) |

## 5. Analysis and Observations

1. **AQI over time:** AQI follows a yearly cycle, high in winter and low in the monsoon. The 2020 winter peak is lower than earlier years.
2. **Top 10 cities:** Ahmedabad, Delhi, Patna, Gurugram and Lucknow rank highest. The **median** was used because Ahmedabad has extreme values.
3. **Seasonal AQI:** Winter and post-monsoon are highest; monsoon is lowest.
4. **AQI categories:** Most days are Satisfactory or Moderate; very few are Good; a small number are Severe.
5. **Correlation:** CO (0.68) and PM2.5 (0.66) correlate most with AQI; NH3 (0.10) and O3 (0.20) least.
6. **Lockdown comparison:** To keep it fair, only cities with data in **every year** for the same window (25 Mar - 31 May) were compared. Average AQI: 149.3 (2019) vs 89.8 (2020), about 40% drop.
7. **Pollutant change:** NO2 about -50%, PM2.5 about -42%, SO2 about -16% (2020 vs 2019).

## 6. Conclusions

- Ahmedabad, Delhi, Patna, Gurugram and Lucknow need the most attention for pollution control.
- Winter and post-monsoon are the critical seasons.
- The lockdown reduced average AQI by about 40%, showing that traffic and industrial activity are major pollution sources.

## 7. Limitations

- Missing values were filled with medians, which can hide real day-to-day variation.
- Not every city has data for all years, so comparisons are limited to cities with full coverage.
- The lockdown comparison shows association, not proof of cause; weather also affects air quality.

## 8. Future Work

- Add a predictive model for AQI
- Include post-2020 data
- Build an interactive dashboard (Plotly / Streamlit)
- Analyse city-wise lockdown impact separately

## 9. Reproducing the Results

1. Install the libraries in `requirements.txt`
2. Place `city_day.csv` in the `data/` folder
3. Run all cells in `airpollutant_analysis.ipynb` from top to bottom

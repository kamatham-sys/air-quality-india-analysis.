# Air Quality in India: Pollution Trends and the COVID-19 Lockdown Effect

An exploratory data analysis (EDA) project investigating air quality patterns across Indian cities from 2015 to 2020 using Python. The analysis examines city-level pollution, seasonal variations, pollutant relationships, and changes in air quality during the COVID-19 lockdown period in 2020.

## Project Overview

Air pollution is a major environmental concern in India. This project analyzes daily air quality data to identify pollution hotspots, understand seasonal patterns, examine relationships between pollutants and the Air Quality Index (AQI), and compare air quality during the 2020 lockdown with the corresponding period in 2019.

**Objectives**
- Identify cities with the highest median AQI.
- Analyze seasonal and monthly variations in air quality.
- Examine relationships between major air pollutants and AQI.
- Compare air quality during the COVID-19 lockdown period in 2019 and 2020.
- Identify which pollutants experienced the largest changes during the comparison period.

## Key Findings

| Analysis | Key Finding |
|---|---|
| Most polluted cities | Ahmedabad, Delhi, Patna, Gurugram, and Lucknow recorded the highest median AQI in the analysis. |
| Seasonal patterns | Winter and post-monsoon periods showed higher AQI, while the monsoon period generally showed lower AQI. |
| Lockdown-period comparison | Average AQI decreased from 149.3 in 2019 to 89.8 in 2020 during March 25–May 31, a reduction of approximately 39.9%. |
| Pollutant correlations | CO (0.68) and PM2.5 (0.66) had the strongest reported positive correlations with AQI. NH3 (0.10) and O3 (0.20) had weaker correlations. |
| Pollutant changes | NO2 decreased by approximately 50%, PM2.5 by 42%, and SO2 by 16% in the lockdown-period comparison. |

*Note: These findings are based on the analyzed dataset and cleaning methodology. The lockdown comparison indicates an observed change, not proof that lockdown measures alone caused the reduction. Correlation does not establish causation.*

## Dataset

- **Source:** Central Pollution Control Board (CPCB), India
- **Dataset:** City-level daily air quality observations
- **Period:** 2015–2020
- **Original file:** `city_day.csv`
- **Original dimensions:** 29,531 rows × 16 columns
- **Cleaned dataset:** `cleaned_data.csv`
- **Cleaned dimensions:** 24,850 rows × 13 columns

### Variables

The dataset includes AQI, AQI categories, and measurements of air pollutants:

- **Particulate matter:** PM2.5, PM10
- **Nitrogen compounds:** NO, NO2, NOx, NH3
- **Gaseous pollutants:** CO, SO2, O3
- **Volatile organic compounds:** Benzene, Toluene, Xylene

The target variables are `AQI` and `AQI_Bucket`, which represents air quality categories such as Good, Satisfactory, Moderate, Poor, Very Poor, and Severe.

## Tools and Technologies

- **Python** — data analysis
- **Pandas** — data manipulation and cleaning
- **NumPy** — numerical operations
- **Matplotlib** — data visualization
- **Seaborn** — statistical visualization
- **Jupyter Notebook** — interactive analysis

## Methodology

1. **Data loading and inspection:** Loaded the original dataset and examined its dimensions, data types, missing values, and summary statistics.
2. **Data cleaning:** Removed selected columns with extensive missing values, excluded records without the required AQI information, and handled missing pollutant values using city-wise medians followed by overall medians where necessary.
3. **Feature engineering:** Created Year, Month, Month_Name, Day_of_Week, Season, and Lockdown Period features.
4. **Exploratory data analysis:** Examined AQI distributions, city-level pollution, seasonal patterns, AQI categories, and pollutant correlations.
5. **Lockdown-period comparison:** Compared AQI and pollutant measurements between March 25 and May 31 in 2019 and 2020, using cities with available data in both comparison periods.
6. **Interpretation:** Summarized the major patterns, differences, and limitations identified during the analysis.

## Project Structure

```text
air-quality-india-analysis/
├── airpollutant_analysis.ipynb
│── city_day.csv
│── cleaned_data.csv
├── README.md
|── Reqquirements.txt
└── DOCUMENTATION.md
```

## How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/<kamatham-sys>/air-quality-india-analysis.git
cd air-quality-india-analysis
```

### 2. Create a virtual environment (recommended)

**Windows:**

```bash
python -m venv venv
venv\Scripts\activate
```

**macOS/Linux:**

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook airpollutant_analysis.ipynb
```

Ensure the notebook's data path matches the repository structure. If the notebook expects `data/city_day.csv`, place the original dataset in the `data/` directory.

## Limitations

- The analysis is limited to the cities and dates available in the dataset.
- Missing-value imputation can affect pollutant distributions and correlation estimates.
- Seasonal averages may conceal differences between individual cities and years.
- The lockdown comparison does not independently account for weather conditions, long-term trends, or other factors that influence air pollution.
- Correlations describe statistical associations and should not be interpreted as causal relationships.

## Future Improvements

- Develop an interactive dashboard using Power BI or Plotly.
- Compare pollution trends across individual cities and years.
- Investigate the influence of meteorological conditions on AQI.
- Build a baseline machine learning model to predict AQI using historical pollutant measurements.

## Author

**Kamatham Sneha**

*Data Analytics Project | October 2026*

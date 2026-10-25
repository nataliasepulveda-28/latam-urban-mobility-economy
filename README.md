# Urban Mobility and Economic Productivity in Latin American Cities

An exploratory data analysis that connects **urban traffic congestion** with **economic indicators** in major Latin American cities, to identify where investment in transport infrastructure is likely to have the greatest impact.

**Tech stack:** Python · pandas · NumPy · seaborn · Matplotlib · Jupyter Notebook

---

## Overview

Traffic congestion has a direct economic cost: lost time, lower productivity and higher operating costs for businesses and residents. Public budgets for transport are limited, so the question is not only *where* congestion is worst, but *where it matters most given each city's economic capacity*.

This project combines real-world traffic data with city-level economic indicators to answer that question. The result is a clean, merged dataset and a set of visual and written findings that support infrastructure investment decisions.

## Objectives

1. Evaluate how urban mobility (congestion and travel times) relates to economic productivity (GDP per capita) in Latin American cities.
2. Identify which cities combine heavy congestion with limited economic capacity, and therefore have the strongest case for transport investment.
3. Produce a clean, reproducible dataset that integrates mobility and economic indicators for further analysis.

## Data sources

| Dataset | Content | Size |
|---|---|---|
| **TomTom Traffic Index** | Near-real-time traffic metrics per city: delay caused by traffic jams (`jams_delay`), live traffic index, jam length and count, minutes of delay and travel time per 10 km | 1,004,464 records, 12 columns |
| **OECD Cities** | Economic indicators per city and year: GDP per capita, unemployment rate, PM2.5 and population | 30 records, 7 columns |

Key variables: `jams_delay` (total congestion minutes), `traffic_index_live` (real-time traffic index), `mins_delay` (delay minutes per trip), `city_gdp_capita`, `unemployment_pct`, `pm25` and `population`.

## Methodology

The analysis follows seven documented steps in the notebook:

1. **Load and explore:** import both datasets and review their structure, columns and data types.
2. **Clean and prepare:** inspect data types and missing values, standardize column names to `snake_case`, convert dates to `datetime`, and clean the numeric columns of the economic dataset (thousands separators, decimal commas and percent signs).
3. **Extract the year and filter:** derive `year` from the update timestamp and keep 2024 records only.
4. **Summarize mobility by city:** average the traffic metrics per city, country and year, so each city has a single comparable record.
5. **Merge mobility and economy:** inner join on `city` and `year`, keeping only the cities present in both datasets.
6. **Visualize relationships:** boxplot of `jams_delay`, histogram of `city_gdp_capita` and a comparative bar chart by city.
7. **Export and document:** save the clean merged dataset as `ladb_mobility_economy_2024_clean.csv` and summarize the results.

## Key findings

- **Congestion is highly uneven.** `jams_delay` is positively skewed: most cities show moderate congestion, while a small group shows extremely high values that behave as outliers. Across the full TomTom sample, Mexico City has the highest average `jams_delay` in 2024 (about 2,833 minutes), followed by Tokyo, New York, London and Manila.
- **GDP per capita is also right-skewed.** Few cities have a high GDP per capita and most are concentrated in the lower-middle ranges.
- **An inverse pattern appears between wealth and congestion.** Cities with a higher GDP per capita tend to record less congestion, while lower-GDP cities concentrate the worst traffic indicators.

## Recommendations

- **Bogotá is the priority candidate for transport investment.** It combines high `jams_delay`, long travel times and a relatively low GDP per capita for its population size, which is the profile where mobility investment is likely to generate the greatest economic return.
- **Lima** shows a similar profile and would be the second priority.
- **Buenos Aires** also shows significant congestion, but its higher GDP per capita gives it more fiscal capacity to address it.

## Limitations and next steps

- The analysis is **observational and covers a single year (2024)**, and only cities present in both datasets. The patterns describe associations and do not prove causality.
- The relationship between GDP per capita and congestion is assessed visually; correlation coefficients are not computed in this version.
- Planned extensions: incorporate earlier years (2019–2023) to study time trends, and cross-reference the results with public transport investment data to test causality.

## Repository contents

| File | Description |
|---|---|
| `ladb_mobility_economy_project_EN.ipynb` | Full analysis notebook, with code, documentation and saved outputs (tables and charts) |
| `README.md` | Project description |

## Viewing and reproducing the analysis

The notebook is saved with its outputs, so tables and charts can be read directly on GitHub without running any code.

The source CSV files are **not included** in this repository. In the notebook they are read from `/datasets/tomtom_traffic.csv` and `/datasets/oecd_city_economy.csv`. To re-run the analysis, place both files in a folder of your choice and update those two paths in the data loading cell. Required libraries: `pandas`, `numpy`, `seaborn` and `matplotlib`.

## Author

**Natalia Sepúlveda** — Data Analyst | Business Intelligence

[LinkedIn](https://www.linkedin.com/in/natalia-sepulveda-escobar) · [GitHub](https://github.com/nataliasepulveda-28) · [Portfolio](https://nataliasepulveda-28.github.io/portfolio/)

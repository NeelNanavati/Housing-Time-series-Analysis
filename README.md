# U.S. Housing Starts: Time Series Analysis

Exploratory time series analysis of monthly U.S. housing starts (January 2005 to December 2025), written in R Markdown. The project loads the data, checks it for problems, and uses plots and autocorrelation tools to describe the trend, seasonality, and short-term dependence in the series. These are the features that matter before building a forecast.

**Author:** Neel Nanavati

## Why housing starts?

Housing starts count the new privately owned housing units on which construction began in a given month. Builders respond quickly to mortgage rates, credit availability, household formation, and confidence in the economy, so the series is a useful gauge of business conditions.

## Data

| Item | Detail |
|---|---|
| Series | [HOUSTNSA](https://fred.stlouisfed.org/series/HOUSTNSA) |
| Producer | U.S. Census Bureau (hosted by FRED) |
| Frequency | Monthly |
| Units | Thousands of housing units |
| Seasonal adjustment | None (not seasonally adjusted) |
| Sample used | January 2005 to December 2025 (252 observations) |

Because the data are not seasonally adjusted, the seasonal pattern stays visible, which is what the seasonal plots examine.

## What the analysis does

1. **Load the data:** read the FRED CSV, rename columns, and restrict the sample to 2005-2025.
2. **Build and validate a tsibble:** declare the monthly index and check for duplicate months, missing values, and gaps in the calendar.
3. **Time plots and annual averages:** plot the full series, zoom in on 2018-2021 (the COVID shock and rebound), and compute yearly means.
4. **Seasonal and subseries plots:** compare the same months across years and look at each calendar month on its own.
5. **Lag plots and autocorrelation:** lag-1 and lag-12 scatter plots, the ACF of housing starts, and a simulated white noise ACF as a baseline.
6. **Discussion:** summarize the patterns found, explain what a 12-month-ahead forecast would mean, and note the effect of data revisions.

## Repository structure

```
.
├── A1-Nanavati-Neel.Rmd     # Main analysis (R Markdown)
├── A1-Nanavati-Neel.html    # Knitted report
├── HOUSTNSA.csv             # Data downloaded from FRED
├── results/                 # Saved plots (PNG)
└── README.md
```

## How to run it

1. Clone or download this repository.
2. Open `A1-Nanavati-Neel.Rmd` in RStudio.
3. Make sure `HOUSTNSA.csv` is in the same folder as the Rmd file.
4. Install the required packages (once):

   ```r
   install.packages(c("readr", "dplyr", "tsibble", "lubridate",
                      "ggplot2", "feasts", "ggtime"))
   ```

5. Click **Knit**. The plots are saved to the `results/` folder, which the script creates if it doesn't exist.

## R packages

`readr`, `dplyr`, `tsibble`, `lubridate`, `ggplot2`, `feasts`, `ggtime`

## Notes

- The white noise comparison uses `set.seed(3232026)` so the simulated series is the same on every run.
- FRED and Census data are revised over time, so a fresh download may differ slightly from the version used here.
- Data source: U.S. Census Bureau, retrieved from FRED, Federal Reserve Bank of St. Louis.

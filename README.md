# ML_73-London-Temperature-Prediction
# London Temperature Prediction | ML_73

A machine learning project using time-series regression to predict London's daily mean temperature from historical weather data.

## Project Information

| Field | Details |
|---|---|
| Project ID | ML_73 |
| Course | Machine Learning Laboratory |
| Course Code | 5CIUP521 |
| Location | London, United Kingdom |
| Dataset Period | 2010–2025 |
| Dataset Size | 5,844 daily records |
| Target Variable | Daily Mean Temperature (°C) |

## Project Overview

This project investigates daily mean temperature prediction in London using historical weather data, time-series feature engineering, and regression algorithms.

The workflow includes data collection, data cleaning, exploratory data analysis, feature engineering, model training, and chronological model evaluation.

**Dataset Source:** [Open-Meteo Historical Weather API](https://open-meteo.com/en/docs/historical-weather-api)

The data represents historical weather/reanalysis data for the selected London coordinates, not necessarily measurements from one specific weather station.

## Machine Learning Models

Three regression algorithms were implemented and compared:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor

A Seasonal Naive forecasting method using a 365-day lag was also included as a benchmark.

## Feature Engineering

The following features were developed:

- Calendar features: Year, Month, Day, Day of Week, Day of Year.
- Seasonal features: Year Sine and Year Cosine.
- Lag features: 1, 2, 3, 7, 14, 30 and 365 days.
- Rolling statistics: 7-day and 30-day rolling averages.

All rolling averages use previous observations to avoid target leakage.

## Model Evaluation

Models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

Five-fold expanding-window walk-forward validation was performed to evaluate model performance across chronological periods.

### Walk-Forward Validation Results

| Model | Mean MAE (°C) | Std MAE | Mean RMSE (°C) | Mean R² |
|---|---:|---:|---:|---:|
| Random Forest | **1.4615** | 0.0552 | **1.8881** | **0.8805** |
| Linear Regression | 1.4631 | 0.1034 | 1.8898 | 0.8785 |
| Decision Tree | 1.8296 | 0.0512 | 2.3394 | 0.8163 |
| Seasonal Naive | 3.1356 | 0.0817 | 3.9507 | 0.4775 |

Random Forest achieved the best average performance across the five validation folds. However, its improvement over Linear Regression was marginal.

## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Open-Meteo API
- Google Colab

## Project Structure

```text
ML_73-London-Temperature-Prediction/
│
├── ML_73.ipynb
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── london_temperature.csv
│
├── models/
│   ├── random_forest_model.pkl
│   └── feature_columns.pkl
│
└── outputs/
    ├── model_comparison.csv
    ├── walk_forward_summary.csv
    ├── walk_forward_fold_results.csv
    └── temperature_predictions.csv
```

## Methodology

1. Historical weather data collection.
2. Data cleaning and exploratory data analysis.
3. Time-series feature engineering.
4. Chronological train-test splitting.
5. Regression model development.
6. Model evaluation and comparison.
7. Walk-forward validation.
8. Result interpretation.

## Conclusion

The Random Forest Regressor achieved a mean MAE of 1.4615°C and mean R² of 0.8805 during five-fold walk-forward validation.

Linear Regression achieved nearly identical performance, demonstrating that a simpler regression model can also capture much of the temperature pattern.

The results show that historical temperature and seasonal features can provide useful information for rolling one-day-ahead temperature prediction.

## Limitations and Future Scope

- Incorporating additional weather variables such as humidity, wind speed and precipitation.
- Exploring recursive multi-day forecasting.
- Hyperparameter optimization.
- Further chronological validation.
- Developing an interactive Streamlit dashboard.

## Author

**Devansh Sharma**

GitHub: [@Devansh23-maker](https://github.com/Devansh23-maker)

---

Weather data provided by [Open-Meteo](https://open-meteo.com/).

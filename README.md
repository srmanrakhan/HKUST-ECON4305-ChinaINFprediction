# Forecasting China's Monthly Inflation

ECON 4305 (HKUST, Fall 2026-27), Group Project, Topic 4. One-month-ahead forecast of China's month-on-month CPI inflation (`INFL`) using lagged macroeconomic indicators.

## Files

| File | Contents |
| --- | --- |
| `china_economic_raw.csv` | Course dataset, Jan 1995 to Apr 2026 |
| `XGBoost_China_Inflation.ipynb` | XGBoost (with and without PCA) |
| `NeuralNetworks_China_Inflation.ipynb` | MLP and LSTM |

## Setup

- Features lagged one month, plus past inflation and month-of-year seasonality
- Data from 2005 onwards; short gaps forward-filled, the rest filled with the training median
- Train: Jan 2005 to Dec 2023 (228 months). Test: Jan 2024 to Apr 2026 (28 months)
- Hyperparameters tuned on training data only

## Results (test period)

| Model | RMSE | R² |
| --- | --- | --- |
| Decision Tree | 0.363 | 0.50 |
| XGBoost | 0.370 | 0.48 |
| MLP | 0.400 | 0.39 |
| Training mean (benchmark) | 0.517 | -0.02 |
| PCA + XGBoost | 0.526 | -0.05 |
| LSTM | 0.639 | -0.55 |

## How to run

```
pip install pandas numpy matplotlib scikit-learn xgboost tensorflow
```
Keep the notebooks and the CSV in the same folder, then run all cells.
The XGBoost and neural network notebooks are adapted from the course notebooks

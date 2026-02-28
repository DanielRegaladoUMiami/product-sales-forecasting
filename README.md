# Logitech Sales Forecasting — Interview Take-Home Project

End-to-end time series forecasting pipeline for Logitech product sales data. Originally completed as part of an MSBA interview case study at the University of Miami.

## Project Overview

Given ~44 months of monthly sales data across multiple product categories and regions, the objective was to:

1. **Clean and explore** the raw data (handle negatives, discontinued products, duplicates, missing values)
2. **Analyze** seasonality, growth trends, and category-level patterns
3. **Forecast** the next 12 months for all viable product series using multiple model families
4. **Summarize** findings in a professional executive report

## Repository Structure

```
├── Individual_Project_DanielRegalado.ipynb   # Full analysis notebook
├── data/
│   └── interview_use_case.csv                # Raw sales data
├── output/
│   └── forecast_best_model.csv               # 12-month forecasts (best model per series)
├── docs/
│   ├── Interview_Candidate_Assignment.pdf    # Original assignment brief
│   └── Logitech_Forecast_Summary.pdf         # Executive summary report
├── requirements.txt
└── .gitignore
```

## Models Used (14 total)

| Family | Models |
|--------|--------|
| **Statistical** | SARIMAX (24 configs), Log-SARIMAX (24 configs), ETS (10 configs) |
| **Automated** | AutoARIMA, AutoETS, AutoTheta, AutoCES, DynOptTheta, OptTheta, MSTL |
| **Machine Learning** | Gradient Boosting, Random Forest |
| **Baselines** | Seasonal Naive, Drift |
| **Ensemble** | Average of top-performing models per series |

Model selection uses **expanding-window cross-validation** (2 folds, 12-month horizon) with RMSE and MAPE as evaluation metrics. SARIMAX models are selected via AIC.

## Key Findings

- **87 viable product series** identified after cleaning (from 100+ raw series)
- **Strong December seasonality** across all regions (~1.8x average month)
- **Region B** dominates total volume; Product Groups C, A, I, G account for ~76% of sales
- **Best-performing models vary by series** — no single model dominates, justifying the multi-model approach

## Setup

```bash
pip install -r requirements.txt
jupyter notebook Individual_Project_DanielRegalado.ipynb
```

## Tools & Libraries

Python 3.10+ with pandas, numpy, matplotlib, seaborn, statsmodels, scikit-learn, and statsforecast (Nixtla).

## Author

**Daniel Regalado Cardoso**
MS Business Analytics — University of Miami

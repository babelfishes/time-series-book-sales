# Book Sales Forecasting: Model Comparison

## Overview
This project compares classical time series models and machine learning models for forecasting book sales using Nielsen BookScan data. The focus is on two popular titles:  

- **The Alchemist** by Paulo Coelho  
- **The Very Hungry Caterpillar** by Eric Carle  

The goal is to understand which modeling approaches—**classical (ARIMA/SARIMA)** or **machine learning (XGBoost, LSTM, hybrid)**—produce the most reliable sales forecasts for publishers.

## Problem Statement
Publishers need accurate sales forecasts to optimize inventory, reduce overstock or understock, and minimize financial risk. This project evaluates multiple forecasting methods on historical Nielsen BookScan data to identify which models provide the best predictive performance for book sales.

## Dataset
- **Source:** Nielsen BookScan (Google Sheets; access requires permission)  
- **Books analyzed:** 61 (main focus on 2 titles)  
- **Features:** Daily sales volume, ISBN, dates  
- **Preprocessing:**  
  - Missing daily volumes filled with 0  
  - Data resampled weekly  
  - Filtered ISBNs with no sales past July 2024  

## Methodology

### Classical Models
- ARIMA and SARIMA models selected based on AIC and Ljung–Box test
- Residual analysis to check model assumptions

### Machine Learning Models
- XGBoost: gradient boosting decision trees  
- LSTM: neural network for sequential forecasting  
- Hybrid Models: sequential and parallel combinations of ARIMA + LSTM  
- Hyperparameter tuning using Grid Search and KerasTuner  
- Cross-validation respecting temporal order

### Evaluation Metrics
- **MAE (Mean Absolute Error)**  
- **MAPE (Mean Absolute Percentage Error)**  
- Visual inspection of forecast plots

## Results
- **Classical models consistently outperformed ML models** for both titles, capturing trends and seasonality effectively.  
- **XGBoost and LSTM** struggled with irregular or volatile sales patterns.  
- **Hybrid models** added complexity but only slightly improved forecasts; ARIMA carried most predictive power.  
- Monthly aggregation smoothed weekly volatility and improved forecast stability slightly.

## Key Takeaways
1. Classical ARIMA/SARIMA models are most reliable for book sales forecasting.  
2. Machine learning models may struggle with small datasets or highly irregular sales patterns.  
3. Simple models can sometimes outperform more complex ML approaches.  
4. Understanding the sales trend and seasonality is critical to selecting the right model.  

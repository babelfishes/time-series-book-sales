# Book Sales Forecasting Using Classical and Machine Learning Methods

## Overview
This project analyzes historical Nielsen BookScan data to forecast book sales for two popular titles:  
- **The Alchemist** by Paulo Coelho  
- **The Very Hungry Caterpillar** by Eric Carle  

The goal is to help small- and medium-sized publishers improve demand forecasting and optimize inventory planning. Classical time series models (ARIMA/SARIMA) and several machine learning models (XGBoost, LSTM, hybrid methods) were applied and compared.

## Problem Statement
Publishers need reliable forecasting methods to reduce stockouts, avoid overprinting, and manage risk. This study evaluates multiple forecasting techniques using Nielsen BookScan data to determine which models offer the best predictive performance for book sales.

## Dataset
- **Data source:** Nielsen BookScan (Google Sheets, access requires permission)  
- **Number of books analyzed:** 61 (filtered to two titles for main analysis)  
- **Key features:** Sales volume per day, ISBNs, dates  
- **Preprocessing notes:**  
  - Missing daily volumes were filled with 0 to represent no-sales days  
  - Data resampled weekly  
  - Removed ISBNs without sales past July 2024  

## Methodology

### Data Processing
- Loaded spreadsheets into pandas DataFrames  
- Converted date columns to datetime index  
- Filtered dataset to focus on *The Alchemist* and *The Very Hungry Caterpillar*  

### Exploratory Analysis
- Most titles declined in sales from 2000–2012, then stabilized  
- ‘The Alchemist’ shows stable seasonal peaks (additive decomposition suitable)  
- ‘The Very Hungry Caterpillar’ shows growth and seasonal spikes (multiplicative decomposition suitable)  

### Classical Models
- ARIMA models selected using AIC and Ljung–Box test:  
  - **Alchemist:** MA(1), AIC 7304  
  - **Caterpillar:** AR(2)+MA(1), AIC 8438  
- Forecasts visually checked; residuals mostly normal  

### Machine Learning Models
- **XGBoost:** Initially unrealistic results (likely leakage); after tuning:  
  - Alchemist MAE: 264.51, MAPE: 47.63%  
  - Caterpillar MAE: 546.93, MAPE: 28.27%  
- **LSTM:** Struggled to capture trends; flatlined forecasts with worse errors  
- **Hybrid Models (Sequential & Parallel ARIMA+LSTM):** Slight improvement; ARIMA dominated predictive power  

### Monthly Aggregation
- Reduced weekly volatility  
- Slight improvement in SARIMA stability  
- Machine learning errors remained higher, but relative performance unchanged  

## Results
- Classical models (ARIMA/SARIMA) outperformed machine learning methods for these titles  
- ML models struggled with volatility and irregular sales patterns  
- Hybrid approaches added complexity but minimal improvement  
- Monthly aggregation smoothed trends but did not significantly change results  

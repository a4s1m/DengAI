# Dengue Fever Case Prediction Using Machine Learning

## Project Overview
This project focuses on predicting **weekly dengue fever cases** for two cities — **San Juan, Puerto Rico** and **Iquitos, Peru** — using historical **climate and environmental data**. The goal is to evaluate how weather-driven variables such as temperature, humidity, rainfall, and vegetation patterns influence dengue outbreaks, and to assess the effectiveness of multiple machine learning models in capturing seasonal disease dynamics.

---

## Research Objectives
- Predict weekly dengue case counts using environmental and climate indicators
- Compare multiple machine learning models for time-series forecasting
- Identify the most influential predictors of dengue outbreaks
- Capture and evaluate **seasonal trends** across two geographically distinct cities
- Determine the best-performing model using **Mean Absolute Error (MAE)**

---

## Dataset Overview

### Data Source
- **Provider:** DrivenData DengAI Challenge
- **Cities:**
  - San Juan, Puerto Rico (1990–2008)
  - Iquitos, Peru (2000–2010)

### Dataset Characteristics
- **Total training observations:** 1,456 weekly records
- **San Juan:** 936 weeks
- **Iquitos:** 520 weeks
- **Test observations:** 416 weeks
- **Features:** 24 environmental and climate variables

### Feature Categories
- **Time-based:** city, year, week of year
- **Temperature:** average, min, max, dew point, daily range
- **Humidity:** relative and specific humidity
- **Rainfall:** station, reanalysis, and satellite estimates
- **Vegetation:** NDVI measurements across four regions

---

## Data Preprocessing
To ensure consistency across all models, I jointly performed data preprocessing:

- Merged dengue case labels with environmental features using:
(city, year, week_of_year)

- Handled missing values using:
- **Forward fill** (gradual environmental changes)
- **Backward fill** (early missing observations)
- Encoded categorical city variable:
- Iquitos → 0
- San Juan → 1
- Removed redundant features (e.g., week start date)
- Final dataset contained:
- **23 predictor variables**
- **1 target variable (weekly dengue cases)**

---

## Train–Validation Strategy
Because dengue forecasting is inherently temporal, the data was split **by time**, not randomly:

- **Training set:** All data before 2008
- **Validation set:** Data from 2008
- **Samples:**
- Training: 1,309 observations
- Validation: 147 observations

This setup simulates a real-world forecasting scenario.

---

## Methodology

### Models Implemented
Four machine learning models were trained and evaluated:

1. **Bayesian Ridge Regression**  
 - Used as the baseline model
 - Handles multicollinearity and prevents overfitting
 - Provides interpretability of feature influence

2. **Random Forest**  
 - Ensemble of 500 decision trees
 - Reduces variance and captures non-linear patterns
 - Demonstrated strongest overall performance

3. **XGBoost**  
 - Gradient-boosted decision trees
 - Sequential error correction
 - High efficiency with strong predictive accuracy

4. **Neural Network (MLP)**  
 - Two hidden layers
 - Adam optimizer
 - Captures complex non-linear relationships
 - Requires careful tuning and longer training time

---

## Evaluation Metric
All models were evaluated using:

**Mean Absolute Error (MAE)**  
This metric measures the average absolute difference between predicted and actual weekly dengue cases and is well-suited for public health forecasting.

---

## Results & Analysis

### Model Performance
- **Best Model:** Random Forest
- **Strong Performers:** XGBoost and Neural Network
- **Baseline:** Bayesian Ridge Regression (higher error)

Random Forest consistently captured:
- Seasonal outbreak cycles
- City-specific trends
- Differences in outbreak intensity between San Juan and Iquitos

### Key Predictive Factors
- Temperature-related features (mean & average temperature)
- Humidity levels
- Rainfall patterns
- Week of the year (seasonality indicator)

Tree-based models significantly outperformed linear models, demonstrating the importance of non-linear relationships in dengue spread.

---

## Visualizations
- Time-series plots comparing **predicted vs actual dengue cases**
- Seasonal outbreak patterns visualized for both cities
- Feature importance rankings from Random Forest

These plots confirmed that the models successfully learned **recurring seasonal dynamics**.

---

## Key Insights
- Climate variables play a dominant role in dengue outbreaks
- Temperature and humidity are stronger predictors than vegetation alone
- Tree-based ensemble models are better suited for epidemiological forecasting than linear methods
- Machine learning can effectively support **early warning systems** for public health planning

---

## How to Run the Project

### Environment
- Python (Jupyter Notebook)

### Required Libraries
- pandas
- numpy
- scikit-learn
- xgboost
- matplotlib
- seaborn
- statsmodels 

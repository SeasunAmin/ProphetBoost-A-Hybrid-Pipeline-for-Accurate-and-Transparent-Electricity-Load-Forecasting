# ProphetBoost-A-Hybrid-Pipeline-for-Accurate-and-Transparent-Electricity-Load-Forecasting

ProphetBoost is a hybrid electricity load forecasting framework that integrates:
Prophet-based trend & seasonality decomposition
Stability-guided + embedded feature selection
XGBoost regression for high predictive accuracy
Unified benchmarking against SOTA methods (Transformer, DLinear, Deep RVFL, CNN-LSTM, CNN-ANN, ARIMA-LSTM)

This repository provides the complete implementation, ensuring full reproducibility for all experiments reported in the manuscript “ProphetBoost: A Hybrid Pipeline for Accurate and Transparent Electricity Load Forecasting.”

<img width="5184" height="3068" alt="Amin" src="https://github.com/user-attachments/assets/1e674d01-c78b-4cd6-b08a-693665041d13" />


### 🔍  ProphetBoost Pipeline Overview

The figure above illustrates the complete ProphetBoost workflow, highlighting how the framework combines decomposition, engineered features, stability-driven feature selection, and XGBoost modeling into a unified forecasting pipeline.


**Main stages:**

- **Data preprocessing**
  - Remove empty columns
  - Parse timestamps into Prophet’s `ds` format
  - Impute missing numeric values with the mean

- **Prophet decomposition**
  - Extract long-term trend \(g(t)\)
  - Model multiple seasonalities \(s(t)\) (daily, weekly, yearly)
  - Optionally capture holiday/special-event effects \(h(t)\)  
  These components are added as extra, interpretable features.

- **Feature engineering**
  - Temporal features: hour of day, day of week, weekend indicator
  - Load history: lag\_1, lag\_24
  - Rolling statistics: `roll3_mean`, `roll3_std`
  - Weather lags from four stations (e.g., `JEJU_DI_lag1`)

- **Dataset splitting**
  - Training: **2012–2018**
  - Testing: **2019–2020**  
  Splits are strictly chronological to avoid look-ahead leakage.

- **Hybrid feature selection**
  - Filter step removes near-zero variance predictors
  - Embedded + stability selection:
    - Train XGBoost on 30 bootstrap samples
    - Rank top-K features by gain in each run
    - Keep features that appear in at least 60% of runs

- **XGBoost training with selected features**
  - Train the final XGBoost model on the stable feature subset
  - Use time-series cross-validation and early stopping

- **Model evaluation and SHAP analysis**
  - Evaluate with MAE, MSE, RMSE, and MAPE
  - Use SHAP values to explain the contribution of each feature

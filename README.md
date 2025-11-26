# ProphetBoost-A-Hybrid-Pipeline-for-Accurate-and-Transparent-Electricity-Load-Forecasting

Accurate short-term electricity load forecasting is essential for reliable grid operation, resource planning, and energy management. Modern forecasting challenges require methods that can capture complex temporal patterns, remain interpretable, and maintain computational efficiency. ProphetBoost addresses this need by combining strong time-series decomposition, robust feature selection, and high-performance machine learning into a single, unified framework.

##  Description

ProphetBoost is a hybrid electricity load forecasting framework that integrates:

- **Prophet-based trend and seasonality decomposition** to capture long-term structure and multiple seasonal patterns  
- **Stability-guided + embedded feature selection** to isolate the most informative predictors from a large engineered feature space  
- **XGBoost regression** for accurate, efficient, and interpretable forecasting  
- **Unified benchmarking** against state-of-the-art models, including Transformer, DLinear, Deep RVFL, CNN–LSTM, CNN–ANN, and ARIMA–LSTM  
 

## 📘  ProphetBoost Pipeline Figure Explanation 
<img width="5184" height="3068" alt="Amin" src="https://github.com/user-attachments/assets/1e674d01-c78b-4cd6-b08a-693665041d13" />
The figure presents the end-to-end ProphetBoost workflow, showing how raw data is transformed into interpretable, high-accuracy electricity load forecasts. The pipeline integrates data preprocessing, Prophet-based decomposition, engineered features, a hybrid feature-selection mechanism, and XGBoost modeling with evaluation and SHAP explainability.



 ## 🔧 Feature Selection Process 
 <img width="1488" height="629" alt="image" src="https://github.com/user-attachments/assets/2b31e9b1-44e3-4a5a-bed5-19c1ef4379a9" />

The figure illustrates the hybrid feature selection strategy used in ProphetBoost. The process combines a simple statistical filter with an embedded XGBoost importance ranking and a stability-based selection mechanism. The goal is to identify a small set of highly informative and consistently important features from the full engineered feature set.


## 📊 Explanation of ProphetBoost Model Results (Panels A–D)
<img width="1383" height="985" alt="result" src="https://github.com/user-attachments/assets/1413c1b9-9379-463a-ba67-d3f706073bb2" />
This figure summarizes ProphetBoost’s performance on the test set: the learning curve (A) shows fast, stable convergence, while actual vs. predicted loads (B) overlap closely with near-zero, symmetric residuals (C). Feature importance (D) highlights recent load dynamics (roll3_mean, lag_1) and key weather indices as the dominant predictors.

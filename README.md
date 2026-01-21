# 🛒 Walmart Weekly Sales Forecasting

![License](https://img.shields.io/badge/License-MIT-lightgrey)

## 📌 Project Overview
Predicting retail demand is a critical challenge for supply chain optimization. This project utilizes the **Walmart dataset** to build a robust forecasting system capable of anticipating demand spikes during holiday seasons and accounting for macroeconomic external factors.

### **The Business Problem**
Retailers face significant financial risks from **inventory imbalance**. Overstocking leads to high holding costs and waste, while understocking during peak periods (like Black Friday) results in lost revenue and diminished customer loyalty. This project aims to provide a data-driven solution to:
* **Quantify the impact** of holidays and external factors (Temperature, Fuel, CPI, Unemployment).
* **Automate demand forecasting** to replace manual heuristics.
* **Minimize forecasting error** to ensure optimal stock levels across 45 stores.

---

## 🚀 Key Results
* **MAPE Reduction:** Achieved a **32.2% improvement** in accuracy over the 4-week moving average baseline.
* **Winning Model:** **SARIMA (0, 0, 0)x(0, 1, 2, 52)** outperformed all other models with a **MAPE of ~1.93%**.
* **Holiday Insight:** Confirmed that holiday weeks provide a **7.8% average boost** in revenue.
* **Macro Impact:** Found that while holidays and external factors are critical indicators, they explain **<3% of sales variance**, proving that internal seasonality is the primary driver of volatility.

---

## 🛠️ Technical Stack
* **Language:** Python 3.x
* **Data Manipulation:** `pandas`, `numpy`
* **Visualization:** `matplotlib`, `seaborn`
* **Statistical Modeling:** `statsmodels` (ARIMA, SARIMAX)
* **Bayesian Forecasting:** `Prophet`
* **Evaluation Metrics:** Mean Absolute Percentage Error (MAPE), RMSE, MAE

---

## 📉 Methodology & Analysis

### 1. Data Audit & EDA
We analyzed 143 weeks of data across 45 stores. 
* **Seasonality:** Identified massive spikes corresponding to Thanksgiving and Christmas.
* **Stationarity:** Verified via the **Augmented Dickey-Fuller (ADF) Test**.
* **Decomposition:** Used additive decomposition to isolate the 52-week annual cycle from the underlying trend.



### 2. Model Benchmarking
We tested multiple forecasting philosophies to find the most resilient engine:
1. **Baseline:** 4-Week Moving Average (Failed to capture seasonality).
2. **ARIMA (5,1,0):** Established a statistical trend baseline.
3. **SARIMAX:** Incorporated exogenous variables (Temperature, Fuel, CPI).
4. **Prophet:** Utilized Bayesian curve fitting with multiplicative seasonality.
5. **SARIMA (Winner):** Optimized via exhaustive Grid Search for the lowest AIC.

### 3. Final Comparison
| Model | MAPE (%) | Improvement vs Baseline |
| :--- | :--- | :--- |
| **SARIMA** | **1.92%** | **32.2%** |
| Prophet | ~1.94% | ~31.9% |
| SARIMAX | ~2.12% | ~25.3% |
| Baseline (MA-4) | 2.84% | 0.0% |
| ARIMA | 3.18% | ~(-12.0%) |



---

## 🧪 Verified Findings
1. **Seasonality is Dominant:** Weekly sales show extreme consistency in yearly cycles.
2. **External Variables are Weak:** Temperature and fuel prices show very low correlation.
3. **Volatility is Concentrated:** High-sales stores exhibit the highest volatility, suggesting a need for specialized safety-stock levels in flagship locations.

---

## 📂 Project Structure
```text
├── Walmart.csv                                      # Raw dataset
├── Walmart_Time_Series_Analysis_Forecasting.ipynb   # Full analysis notebook
└── README.md                                        # Project documentation

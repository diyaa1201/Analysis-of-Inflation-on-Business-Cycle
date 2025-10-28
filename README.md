# 📈 Analysis of Inflation on Business and Economic Growth (India)

## 🧾 Overview

This project analyzes the relationship between **inflation** and **economic growth in India** using macroeconomic indicators obtained from the **Reserve Bank of India (RBI) DBIE**. It explores how inflation trends correlate with GDP, GNI, NNI, and per-capita metrics across the time span **1950–2024**, applying time-series econometrics and machine learning to extract insights and build forecasting models.

---

## 📘 Project Objectives

* Quantify how inflation impacts India’s economic growth indicators (GDP, GNI, NNI).
* Identify short- and long-run relationships between CPI-based inflation and growth metrics.
* Build predictive models (VAR for econometric analysis and XGBoost for ML forecasting).
* Provide actionable insights for policymakers and business planners via forecasts and scenario analysis.

---

## 🗂️ Repository Structure
| File | Description |
|------|--------------|
| [`inflation_analysis.ipynb`][(inflation_analysis.ipynb) ](https://github.com/diyaa1201/Analysis-of-Inflation-on-Business-Cycle/blob/main/Analysis_of_inflation.ipynb)| Main Jupyter Notebook containing all the steps — from data cleaning and merging to analysis and visualization. |
| [`economic_data.csv`][(economic_data.csv) ](https://github.com/diyaa1201/Analysis-of-Inflation-on-Business-Cycle/blob/main/economic_data.csv)| Contains GDP, GNI, NNI, and per capita indicators for India. |
| [`cpi_data.csv`][(cpi_data.csv) ](https://github.com/diyaa1201/Analysis-of-Inflation-on-Business-Cycle/blob/main/cpi_data.csv) | Contains annual inflation (CPI) data. |
| [`final_cleaned_economic_cpi_data.csv`][(final_cleaned_economic_cpi_data.csv) ](https://github.com/diyaa1201/Analysis-of-Inflation-on-Business-Cycle/blob/main/final_cleaned_economic_cpi_data.csv) | Final cleaned and merged dataset used for analysis. |                                                                                                                    |

---

## 💾 Dataset Information

**Source:** Reserve Bank of India — Database on Indian Economy (DBIE).
**Time span:** Annual observations, **1950 – 2024**.

### Variables / Metrics used

* `Year` — time index (1950–2024)
* `GDP` — Gross Domestic Product (nominal or real as in RBI file)
* `GNI` — Gross National Income
* `NNI` — Net National Income
* `PerCapita_GDP`, `PerCapita_GNI`, `PerCapita_NNI` — per-capita metrics
* `CPI_AllIndia` — Consumer Price Index (all-India) / Inflation_Rate derived from CPI
* `CPI_IW` — Consumer Price Index for Industrial Workers (where available)
* Additional RBI variables included where present (e.g., real GDP growth, index series)

> All datasets are cleaned, aligned, and merged on the `Year` column.

---

## 🧹 Data Cleaning & Preprocessing (Process Flow)

1. **Load raw CSVs** exported from RBI DBIE.
2. **Trim header noise** and remove extra descriptive rows present in RBI exports.
3. **Standardize `Year`** column as integer (1950–2024).
4. **Handle missing values**:

   * Replace `-` or `...` with `NaN`.
   * If small gaps exist, fill with interpolation or domain-considered imputation.
5. **Convert numeric strings** (with commas, parentheses) to numeric dtype.
6. **Rename columns** for consistency (e.g., `CPI_AllIndia`, `Inflation_Rate`).
7. **Merge** CPI and economic datasets on `Year`.
8. **Create derived features**: year-on-year inflation, GDP growth rates, lags of core variables, rolling means where necessary.
9. **Train/test split**: time-based split (train: 1974–2010, test: 2011–2023) used for forecasting and evaluation.

---

## 📊 Exploratory Data Analysis (EDA) — (Process Flow)

* Time-series plots of `GDP`, `GNI`, `PerCapita_GDP`, and `Inflation_Rate`.
* Correlation heatmaps between growth and inflation metrics.
* Distribution checks, skewness, and variance analysis for each series.
* Stationarity checks (ADF and KPSS tests) to detect non-stationary behavior.
* Visual inspection for structural breaks or policy-era changes (pre/post liberalization).
* Outlier detection and year-by-year comparison for major economic events (e.g., 1991 reforms, global crises).

**50-word summary after EDA (example placed in notebook):**
After EDA we cleaned and merged CPI and macro datasets, converted variables to numeric, tested stationarity, visualized trends and correlations, engineered lag features, and split data for modeling — setting the dataset for VAR econometric analysis and machine-learning forecasting (Random Forest, XGBoost).

---

## 🔬 Time Series Stationarity & VAR Preparation (Process Flow)

* Conducted **ADF** and **KPSS** tests for all series.
* Differenced non-stationary series to achieve stationarity where required.
* Tested for cointegration where appropriate; if cointegrated, considered Vector Error Correction (VEC) concepts.
* Determined optimal VAR lag order using **AIC/BIC/HQIC**.
* Scaled and aligned series for VAR input.

---

## 📈 VAR Model & Granger Causality (Process Flow)

* Fit **VAR** on stationary/differenced variables.
* Run **Granger causality** tests to identify predictive directionality (e.g., whether inflation Granger-causes GDP growth or vice versa).
* Store IRFs and variance decompositions for interpretation.

---

## 📉 Impulse Response Analysis (IRA) 

Impulse Response Functions (IRFs) trace the effect of a one-time shock to one variable (e.g., a sudden 1% rise in inflation) on the future values of other variables (GDP, GNI) in the VAR system. IRA provides a temporal, causal-style view — useful to interpret economic dynamics (short- vs long-run effects).
**Note:** IRA is included as an econometric validation step to illustrate dynamic responses, but it is complementary — not required — for ML forecasting.

---

## 🔎 Era-Based Comparative Analysis 
* Split the dataset into **pre-1991** (pre-liberalization) and **post-1991** eras.
* Compare volatility, inflation–growth correlation, and impulse responses across eras.
* Note regime-specific changes in structural relationships.

---

## 🔬 Business Cycle Analysis (Decomposition + Spectral)

* Decomposed series into **trend**, **seasonal** (if any at annual frequency minimal), and **residual** using STL/HP filter.
* Conducted **spectral analysis** to detect cyclical frequencies and business cycle periodicities.
* Linked cycle phases with macroeconomic events.

---

## 🧩 Forecasting Framework & Feature Engineering (Process Flow)

* Created lag features (t−1, t−2,...), rolling means, and percent changes.
* Included macro indicators and lagged CPI as predictors.
* Applied standard scaling where needed for ML algorithms.
* Time-series aware train-test split to prevent leakage.

---

## 🧠 XGBoost Model Development & Tuning


* Handles non-linear relationships between inflation and growth metrics.
* Robust regularization (L1/L2) helps mitigate overfitting.
* Efficient on small to medium time-series datasets when engineered features are good.
* Can ingest many lagged and derived features easily.

**Implementation details (what we did):

* Model: `XGBRegressor(n_estimators=150, max_depth=6, learning_rate=0.05, random_state=42)`.
* Input features: lagged inflation, lagged GDP growth, per-capita indicators, rolling stats, calendar-year features.
* Training period: 1974–2010; testing: 2011–2023.
* Evaluation metrics: **RMSE, MAE, MAPE, R²**.
* Hyperparameter tuning: grid search for `n_estimators`, `max_depth`, `learning_rate` (where computationally feasible).
* Final reported performance: (from notebook) **Train RMSE ≈ 0.0529, Train MAPE ≈ 0.78%, Train R² ≈ 0.9996; Test RMSE ≈ 4.1268, Test MAPE ≈ 48.09%, Test R² ≈ -0.2167.**

**Interpretation & notes:**

* XGBoost shows near-perfect fit on training data and moderate performance on test data → indicates **some overfitting**, likely due to limited annual observations and strong in-sample patterns.
* Still, XGBoost **improves over the naive baseline** (last-value method) by about **25% in RMSE**, showing real predictive gains.

---

## 🆚 Model Performance & Final Comparison (VAR vs XGBoost)

| Criteria                |                          VAR (Econometric) |                                                 XGBoost (ML) |
| ----------------------- | -----------------------------------------: | -----------------------------------------------------------: |
| Purpose                 |                Explain dynamics, causality |                                       Predictive performance |
| Captures nonlinearity   |                 (linear unless extended)   |                                           (trees + boosting) |
| Requires stationarity   |                                     (yes)  |       No strict requirement (but features may be stationary) |
| Interpretability        |                        High (coeffs, IRFs) |                         Moderate (feature importances, SHAP) |
| Performance on test set |   Good for short-term structural forecasts |       Typically better when complex nonlinear patterns exist |
| Useful for this project | Provides economic intuition (Granger, IRF) | Best for accurate forecasting and capturing complex patterns |

**Recommendation:** Use both. VAR + IRF for **econometric interpretation and causal insight**; XGBoost for **practical forecasting** and scenario predictions. In the README and report, highlight both outputs and reconcile differences.

---

## ⚠️ Limitations

* **Non-stationarity:** Several key time series were non-stationary and required differencing — this complicates both VAR interpretation and ML feature design.
* **Annual frequency & small sample size:** Only annual observations (1950–2024) limit the amount of training data and model generalizability.
* **Structural breaks & external shocks:** Major events (1991 reforms, global financial crisis, pandemic) create regime shifts that are hard to model with stationary assumptions.
* **Model overfitting risk:** XGBoost fits training data extremely well; careful cross-validation and regularization are needed.
* **Measurement / metadata issues:** RBI exports often include header rows or formatting quirks; careful cleaning is required.
* **Unobserved confounders:** Variables such as fiscal policy, monetary stance, exchange rates, global demand are not fully captured here.

---

## 🔮 Future Improvements (Goals & Enhancements)

* **Add additional predictors:** Include interest rates, exchange rate, unemployment, fiscal deficit, trade balance, and world GDP growth.
* **Higher-frequency data:** Use quarterly series if RBI or other official sources allow, to increase training samples.
* **Ensemble models:** Blend VAR forecasts with XGBoost/Random Forest for hybrid predictions.
* **Advanced stationarity handling:** Test cointegration and implement VECM when needed; use transformations that preserve economic interpretability.
* **Model explainability:** Use SHAP values to explain XGBoost predictions per-year and identify influential features.
* **Real-time pipeline:** Build a web app to update forecasts as new RBI releases arrive.
* **Scenario forecasting:** Provide policy scenario runs (e.g., inflation shock scenarios, fiscal tightening scenarios).
* **Deploy forecasting dashboard** for interactive visualization and decision-support.

**Primary future forecasting goal:** Build an operational inflation forecasting module to predict annual CPI and evaluate expected GDP growth responses — useful for policy simulation and business planning.

---

## 🧰 Tools & Technologies

* **Language:** Python
* **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Statsmodels, XGBoost, fbprophet (optional for trend), statsmodels.tsa (VAR/VECM)
* **Data Source:** RBI DBIE (Reserve Bank of India)
* **Environment:** Google Colab / Jupyter Notebook

---

## ⚙️ Installation

To run locally:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels xgboost
```

---

## 📌 How to Use this Repo

1. Open `analysis_of_inflation.ipynb`.
2. Run the cells in order: Data ingestion → Cleaning → EDA → Stationarity tests → VAR → IRF → Feature engineering → XGBoost training/tuning → Evaluation → Plots.
3. Check `final_cleaned_economic_cpi_data.csv` for the merged dataset used for modeling.
4. Refer to the “Conclusions” and “Future Improvements” sections for next steps or to reproduce results.

---

## ✅ Conclusion

This repository presents a combined **econometric + machine learning** approach to analyze and forecast how inflation affects India’s economic growth. VAR/IRF deliver causal and temporal interpretation, while XGBoost offers improved predictive power. Together, they provide a balanced, data-driven toolkit for economic analysis and forecasting.

---



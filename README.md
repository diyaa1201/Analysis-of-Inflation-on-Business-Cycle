# 📈 Analysis of Inflation on Business and Economic Growth (India)

### 🧾 Overview
This project analyzes the relationship between **inflation** and **economic growth in India** using real-world macroeconomic indicators obtained from the **World Bank Open Data** and **Government of India (MOSPI)** sources.  
It explores how inflation trends correlate with GDP, GNI, and other measures of economic growth over time, applying **data warehousing** and **data mining** techniques to uncover meaningful insights.

---

## 📘 Project Objectives
- Examine how inflation impacts India’s economic growth and income levels.
- Identify correlations between inflation, GDP, GNI, and per capita income.
- Visualize macroeconomic trends and fluctuations over the years.
- Apply data preprocessing, analysis, and visualization techniques in Python.

---

## 🗂️ Repository Structure
| File | Description |
|------|--------------|
| [`inflation_analysis.ipynb`][(inflation_analysis.ipynb) ](https://github.com/diyaa1201/Analysis-of-Inflation-on-Business-Cycle/blob/main/Analysis_of_inflation.ipynb)| Main Jupyter Notebook containing all the steps — from data cleaning and merging to analysis and visualization. |
| [`economic_data.csv`][(economic_data.csv) ](https://github.com/diyaa1201/Analysis-of-Inflation-on-Business-Cycle/blob/main/economic_data.csv)| Contains GDP, GNI, NNI, and per capita indicators for India. |
| [`cpi_data.csv`][(cpi_data.csv) ](https://github.com/diyaa1201/Analysis-of-Inflation-on-Business-Cycle/blob/main/cpi_data.csv) | Contains annual inflation (CPI) data. |
| [`final_cleaned_economic_cpi_data.csv`][(final_cleaned_economic_cpi_data.csv) ](https://github.com/diyaa1201/Analysis-of-Inflation-on-Business-Cycle/blob/main/final_cleaned_economic_cpi_data.csv) | Final cleaned and merged dataset used for analysis. |

> 📌 Click on the notebook link above to directly open the analysis in GitHub.

---

## 💾 Dataset Information

### **1️⃣ Macroeconomic Indicators Dataset**
**Source:** [Reserve Bank Of India]
**Variables:**
- `Year` — Time period (1950–2024)  
- `GDP` — Gross Domestic Product (in USD)  
- `GNI` — Gross National Income (in USD)  
- `NNI` — Net National Income (in USD)  
- `PerCapita_GDP`, `PerCapita_GNI`, `PerCapita_NNI` — Per capita metrics  

---

### **2️⃣ Inflation (CPI) Dataset**
**Source:** [Reserve Bank Of India]
**Variables:**
- `YEAR` — Year of record  
- `Inflation_Rate` — Annual % change in the Consumer Price Index (CPI)

---

### **3️⃣ Merged Dataset**
Created by merging the above two datasets on the **Year** column.  
Used for **EDA** (Exploratory Data Analysis) and **visualization** of inflation–growth patterns.

---

## 🧹 Data Cleaning & Preprocessing
- Standardized year formats and converted to integers.  
- Renamed columns for consistency.  
- Removed missing or irrelevant rows.  
- Converted numeric fields to appropriate data types.  
- Merged datasets to form a single clean DataFrame.  

---

## 📊 Exploratory Data Analysis (EDA)
Performed using **Python (Pandas, NumPy, Matplotlib, Seaborn)**:
- 📈 Time-series visualization of GDP, GNI, and Inflation Rate.  
- 🔥 Correlation heatmaps to identify variable relationships.  
- 📉 Trendline comparison between Inflation Rate and GDP growth.  
- 🧮 Outlier detection and year-wise fluctuation analysis.  

---

## 💡 Key Findings
- Periods of **high inflation** correspond with **slower GDP growth**.  
- **Per capita income** growth shows resilience to short-term inflation spikes.  
- Strong **post-2014 correlation** between inflation control and economic stability.  

---

## 🧰 Tools & Technologies
| Category | Tools Used |
|-----------|-------------|
| **Languages** | Python |
| **Libraries** | Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Statsmodels |
| **Data Sources** | World Bank Open Data, MOSPI |
| **Environment** | Jupyter Notebook / Google Colab |

---

## ⚙️ Installation
If you want to run the notebook locally, install dependencies using:
```bash
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn

**Analysis of Inflation on Business and Economic Growth**


📘 Overview
This project analyzes the relationship between inflation and economic growth in India using real-world macroeconomic indicators. It explores how inflation trends correlate with GDP, GNI, and other growth measures over time, applying data warehousing and data mining techniques.

# Inflation Analysis Project

## Project Overview
This project analyzes [mention what, e.g., global inflation trends, US CPI data, the impact of specific factors] using Python. The goal is to [mention your goal, e.g., identify key drivers, forecast future inflation, or visualize historical trends].

## Repository Contents
- `inflation_analysis.ipynb`: The main Jupyter Notebook containing the complete code, from data loading to visualization and analysis.

pip install pandas numpy matplotlib seaborn statsmodels scikit-learn
📂 Dataset Information
Source
The datasets were collected from the World Bank Open Data and Government of India (MOSPI) sources.


**Datasets Used: Macroeconomic Indicators Dataset**
Source: World Bank Data


Variables:
Year — Time period (2000–2024)
GDP — Gross Domestic Product (in USD)
GNI — Gross National Income (in USD)
NNI — Net National Income (in USD)
PerCapita_GDP, PerCapita_GNI, PerCapita_NNI — Per capita metrics
Inflation (CPI) Dataset
Source: World Bank CPI Data


Variables:
YEAR — Year of record
Inflation_Rate — Annual percentage change in Consumer Price Index (CPI)
Merged Dataset
Created by merging the above two datasets on the Year column.
Used for exploratory data analysis (EDA) and visualization of inflation–growth patterns.



🧹 Data Cleaning & Preprocessing
Converted inconsistent year formats to integers.
Renamed columns for uniformity across datasets.
Removed null or irrelevant rows (e.g., missing economic indicators).
Converted numeric values to appropriate types (float/int).
Merged datasets to form a single clean data frame for analysis.



📊 Exploratory Data Analysis (EDA)
Time-series visualization of GDP, GNI, and Inflation Rate.
Correlation heatmaps to identify relationships.
Trendline comparison between Inflation Rate and GDP growth.
Outlier detection and year-wise fluctuation study.


💡 Key Findings
High inflation periods correspond with dips in GDP growth.
Per capita income growth rates are more resilient to short-term inflation spikes.
Strong correlation between inflation control and economic stability post-2014.


🧰 Tools & Technologies
Languages: Python
Libraries: Pandas, NumPy, Matplotlib, Seaborn
Data Source: World Bank Open Data
IDE: Jupyter Notebook / Google Colab

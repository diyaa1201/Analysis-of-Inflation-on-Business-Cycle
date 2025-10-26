Economic Indicators and CPI Inflation Analysis
Project Overview
This project analyzes the relationship between macroeconomic indicators and consumer price inflation in India over a 55-year period (1970-2024). The analysis combines economic growth data with inflation metrics to understand how economic development correlates with price levels over time.
**Dataset 1:** Economic Indicators
Description:Comprehensive macroeconomic data tracking India's economic performance from 1950-2024, containing key national accounts and per capita metrics.
Attributes & Definitions:
National Accounts (in ₹ Crores)
Gross Domestic Product (GDP): Total monetary value of all finished goods and services produced within a country's borders in a specific time period
Net Domestic Product (NDP): GDP minus depreciation of capital assets
Gross National Income (GNI): GDP plus net income from abroad
Per Capita Indicators (in ₹):
Per Capita GDP (₹): GDP divided by population, indicating average economic output per person
Per Capita GNI (₹): GNI divided by population, showing average income per person

**Dataset 2:** Consumer Price Index (CPI) Data
Description
Inflation measurement data tracking changes in price levels of consumer goods and services across different population segments and commodity groups.
Attributes & Definitions:
CPI Series (Base Year = 100):
CPI_AL: Consumer Price Index for Agricultural Labourers - Measures inflation for rural agricultural workers
CPI_IW: Consumer Price Index for Industrial Workers - Tracks inflation for urban industrial workforce
CPI_IW_Food: Food-specific CPI for Industrial Workers - Measures food inflation for urban workers

New CPI Series (Base: 2012 = 100):
Rural: CPI for rural population centers
Urban: CPI for urban population centers
Combined: All-India combined CPI (most widely used inflation measure)
Food_Beverages: Food and beverages specific inflation index



> Data Merging Process
Preprocessing Steps:
Data Cleaning: Removed header rows, standardized formats, handled missing values
Type Conversion: Converted string values with commas to numeric formats
Missing Value Treatment: Used interpolation for minimal missing CPI data points

Merge Methodology:
Merge Type: Inner join on Year column
Key Used: Fiscal year (April-March) in format YYYY_YY (e.g., 2024_25)
Period Covered: 1970-71 to 2024-25 (55 years)
Final Dataset: 55 rows × 9 columns of complete data

Final Merged Dataset Columns:
Year - Fiscal year (1970_71 to 2024_25)
Gross Domestic Product - Economic output (₹ Crores)
Net Domestic Product - GDP minus depreciation (₹ Crores)
Gross National Income - Total national income (₹ Crores)
Per Capita GDP (₹) - GDP per person
Per Capita GNI (₹) - Income per person
CPI_AL - Agricultural labourers inflation index
CPI_IW - Industrial workers inflation index
CPI_IW_Food - Food inflation for industrial workers

_**Key Transformations:**_
Standardized year formats across datasets
Handled inconsistent numeric formatting (commas, dashes)
Preserved complete time series without data loss
Maintained data integrity for time-series analysis

_**Next Steps: Exploratory Data Analysis**_
The EDA phase will examine:
Correlation between economic growth and inflation
Time-series trends in GDP and CPI
Distribution analysis of key variables
Identification of economic regimes and inflationary periods
_**Usage**_
This dataset is ideal for:
Macroeconomic research
Inflation-economic growth relationship studies
Time-series forecasting models
Policy impact analysis
Economic trend identification                                                                                                            

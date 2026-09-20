# 🚗 BMW Global Sales, Demand \& Time-Series Modeling

<div align="center">

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=matplotlib&logoColor=white)](https://matplotlib.org/)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

*Comprehensive multi-year time-series analysis exploring BMW global sales trends, regional revenue concentration, and electric vehicle (EV) adoption shifts across 10+ international markets.*

</div>

\---

## 📌 Project Overview

This project conducts a **deep-dive analytical study** of BMW's global automotive sales performance — combining time-series forecasting, regional revenue analysis, and EV adoption modelling. It answers the strategic questions that define BMW's competitive positioning in a rapidly electrifying automotive market.

**Coverage:**

|Metric|Scope|
|-|-|
|🌍 Markets Covered|10+ international markets|
|📅 Time Period|Multi-year historical data|
|🔋 EV vs ICE Analysis|Electric vs Internal Combustion Engine split|
|📈 Forecasting Horizon|Short \& medium-term demand projection|

\---

## 🎯 Analytical Objectives

|Objective|Approach|
|-|-|
|Identify global sales trends|Time-series decomposition \& trend analysis|
|Map regional revenue concentration|Geographic segmentation \& heat mapping|
|Analyse EV adoption trajectory|EV share growth modelling over time|
|Forecast future demand|ARIMA / Prophet time-series forecasting|
|Benchmark market performance|Year-over-Year (YoY) \& CAGR calculation|
|Detect seasonality patterns|Seasonal decomposition (STL)|

\---

## 🖼️ Dashboard \& Visualisation Preview

> \*Add your Power BI dashboard and Python plot screenshots here\*

|Global Sales Trend|Regional Revenue Map|EV Adoption Curve|
|-|-|-|
|*<img width="996" height="173" alt="Global\_sales\_trend" src="https://github.com/user-attachments/assets/4b3fadac-7d5b-4907-9116-bf18218c07b2" />*|*<img width="302" height="227" alt="image" src="https://github.com/user-attachments/assets/712ab5b5-5aab-41e8-ab16-3d2f798d68fa" />*|*<img width="343" height="234" alt="image" src="https://github.com/user-attachments/assets/a664f517-f97c-41f8-8ec9-3c8712045f2f" />*|

\---

## 🔑 Key Analysis Components

### 1️⃣ Global Sales Trend Analysis

* Multi-year total volume trends (units sold)
* Year-over-Year (YoY) growth rate calculation
* CAGR across the full analysis period
* Peak and trough identification

### 2️⃣ Regional Revenue Concentration

* Revenue and volume breakdown across 10+ markets
* Top 3 market contribution as % of global sales
* Emerging vs mature market comparison
* Regional growth rate benchmarking

### 3️⃣ Electric Vehicle (EV) Adoption Shifts

* EV vs ICE unit sales split over time
* EV adoption rate growth curve by region
* BEV (Battery Electric) vs PHEV (Plug-in Hybrid) breakdown
* EV market share trajectory and inflection point detection

### 4️⃣ Time-Series Demand Forecasting

* Trend \& seasonality decomposition
* ARIMA / Prophet model for demand forecasting
* Confidence interval visualisation
* Forecast vs Actual accuracy measurement (MAPE)

\---

## 🐍 Python Analysis Highlights

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from statsmodels.tsa.seasonal import seasonal\_decompose
from statsmodels.tsa.arima.model import ARIMA

# Load BMW sales data
df = pd.read\_csv('bmw\_global\_sales.csv', parse\_dates=\['date'])
df.set\_index('date', inplace=True)

# Time-series decomposition
decomposition = seasonal\_decompose(df\['units\_sold'], model='additive', period=12)
decomposition.plot()
plt.suptitle('BMW Global Sales — Trend \& Seasonality Decomposition')
plt.tight\_layout()
plt.show()
```

```python
# EV Adoption Share Over Time
ev\_share = df.groupby(\['year', 'powertrain\_type'])\['units\_sold'].sum().unstack()
ev\_share\['ev\_share\_pct'] = ev\_share\['EV'] / ev\_share.sum(axis=1) \* 100

ax = ev\_share\['ev\_share\_pct'].plot(
    kind='line', marker='o', color='#1f77b4',
    figsize=(12, 5), linewidth=2
)
ax.set\_title('BMW EV Adoption Rate — Global Market Share Over Time', fontsize=14)
ax.set\_ylabel('EV Market Share (%)')
ax.set\_xlabel('Year')
plt.tight\_layout()
plt.show()
```

```python
# ARIMA Demand Forecasting
model = ARIMA(df\['units\_sold'], order=(2, 1, 2))
model\_fit = model.fit()

forecast = model\_fit.forecast(steps=12)
print(f"12-Month Demand Forecast:\\n{forecast}")

# Plot forecast vs actual
fig, ax = plt.subplots(figsize=(14, 5))
df\['units\_sold'].plot(ax=ax, label='Actual Sales', color='steelblue')
forecast.plot(ax=ax, label='Forecasted Demand', color='orange', linestyle='--')
ax.set\_title('BMW Global Sales — ARIMA Demand Forecast', fontsize=14)
ax.legend()
plt.tight\_layout()
plt.show()
```

\---

## 📊 Power BI Dashboard Sections

* **🌍 Global Overview** — Total units sold, revenue, YoY growth KPI cards
* **📈 Sales Trend** — Multi-year line chart with trend line and forecast overlay
* **🗺️ Regional Map** — Choropleth map of sales by country/region
* **🔋 EV vs ICE Split** — Stacked area chart showing powertrain evolution
* **🏆 Market Ranking** — Bar chart of top 10 markets by volume
* **📅 Seasonality View** — Month-wise heat map of sales patterns

\---

## 📂 Repository Structure

```
bmw-global-sales-analysis/
│
├── 📁 data/
│   ├── raw/                          # Raw BMW sales datasets (CSV)
│   └── processed/                    # Cleaned \& enriched data
│
├── 📁 notebooks/
│   ├── 01\_data\_cleaning.ipynb        # Data loading, cleaning, validation
│   ├── 02\_eda.ipynb                  # Exploratory Data Analysis
│   ├── 03\_regional\_analysis.ipynb    # Regional revenue concentration
│   ├── 04\_ev\_adoption.ipynb          # EV vs ICE trend analysis
│   └── 05\_time\_series\_forecast.ipynb # ARIMA / Prophet forecasting
│
├── 📁 dashboard/
│   └── BMW\_Sales\_Dashboard.pbix      # Power BI dashboard file
│
├── 📁 screenshots/
│   └── \*.png                         # Dashboard \& plot screenshots
│
├── requirements.txt                  # Python dependencies
└── README.md
```

\---

## 📦 Python Dependencies

```txt
pandas>=2.0.0
numpy>=1.24.0
matplotlib>=3.7.0
seaborn>=0.12.0
statsmodels>=0.14.0
prophet>=1.1.4
scikit-learn>=1.3.0
plotly>=5.15.0
jupyter>=1.0.0
```

\---

## 💡 Key Insights Uncovered

> \*(Update with your actual findings)\*

* 📈 **Global Growth:** BMW global sales grew at X% CAGR over the analysis period
* 🌍 **Top Market:** \[Country] accounted for X% of total global volume
* 🔋 **EV Surge:** EV unit share grew from X% to X% — a Xx increase in adoption rate
* 📉 **Demand Dip:** \[Year] saw a X% decline driven by \[reason — supply chain, COVID, etc.]
* 📅 **Seasonality:** Strongest sales consistently in \[Q4/Q1], weakest in \[Q2/Q3]
* 🔮 **Forecast:** ARIMA model projects X units sold in next 12 months (MAPE: X%)

\---

## 🛠️ Tools \& Technologies

|Tool|Purpose|
|-|-|
|**Python**|Data analysis, time-series modelling, visualisation|
|**Pandas / NumPy**|Data wrangling and numerical computation|
|**Matplotlib / Seaborn**|Static chart generation|
|**Statsmodels / Prophet**|ARIMA and Prophet forecasting models|
|**Power BI Desktop**|Executive dashboard and interactive reporting|
|**Jupyter Notebooks**|Analysis documentation and reproducibility|

\---

## 📬 Connect With Me

**Megharaju Vakiti** — Data Analyst

[!\[LinkedIn](https://img.shields.io/badge/LinkedIn-Megharaju%20Vakiti-0077B5?style=flat-square\&logo=linkedin\&logoColor=white)](https://www.linkedin.com/in/megharaju-vakiti)
[!\[GitHub](https://img.shields.io/badge/GitHub-Megharaju--Vakiti-181717?style=flat-square\&logo=github\&logoColor=white)](https://github.com/Megharaju-Vakiti)

\---

<div align="center">
  <em>⭐ If you found this project useful, please give it a star!</em>
</div>

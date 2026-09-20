# 🚗 BMW Global Sales, Demand & Time-Series Modeling

<div align="center">

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=python&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

*Comprehensive multi-year time-series analysis exploring BMW global sales trends, regional revenue concentration, and electric vehicle (EV) adoption shifts across 10+ international markets.*

</div>

---

## 📌 Project Overview

This project conducts a **deep-dive analytical study** of BMW's global automotive sales performance — combining time-series forecasting, regional revenue analysis, and EV adoption modelling. It answers the strategic questions that define BMW's competitive positioning in a rapidly electrifying automotive market.

**Coverage:**
| Metric | Scope |
|--------|-------|
| 🌍 Markets Covered | 10+ international markets |
| 📅 Time Period | Multi-year historical data |
| 🔋 EV vs ICE Analysis | Electric vs Internal Combustion Engine split |
| 📈 Forecasting Horizon | Short & medium-term demand projection |

---

## 🎯 Analytical Objectives

| Objective | Approach |
|-----------|----------|
| Identify global sales trends | Time-series decomposition & trend analysis |
| Map regional revenue concentration | Geographic segmentation & heat mapping |
| Analyse EV adoption trajectory | EV share growth modelling over time |
| Forecast future demand | ARIMA / Prophet time-series forecasting |
| Benchmark market performance | Year-over-Year (YoY) & CAGR calculation |
| Detect seasonality patterns | Seasonal decomposition (STL) |

---

## 🖼️ Dashboard & Visualisation Preview

> *Add your Power BI dashboard and Python plot screenshots here*

| Global Sales Trend | Regional Revenue Map | EV Adoption Curve |
|---|---|---|
| *(screenshot)* | *(screenshot)* | *(screenshot)* |

---

## 🔑 Key Analysis Components

### 1️⃣ Global Sales Trend Analysis
- Multi-year total volume trends (units sold)
- Year-over-Year (YoY) growth rate calculation
- CAGR across the full analysis period
- Peak and trough identification

### 2️⃣ Regional Revenue Concentration
- Revenue and volume breakdown across 10+ markets
- Top 3 market contribution as % of global sales
- Emerging vs mature market comparison
- Regional growth rate benchmarking

### 3️⃣ Electric Vehicle (EV) Adoption Shifts
- EV vs ICE unit sales split over time
- EV adoption rate growth curve by region
- BEV (Battery Electric) vs PHEV (Plug-in Hybrid) breakdown
- EV market share trajectory and inflection point detection

### 4️⃣ Time-Series Demand Forecasting
- Trend & seasonality decomposition
- ARIMA / Prophet model for demand forecasting
- Confidence interval visualisation
- Forecast vs Actual accuracy measurement (MAPE)

---

## 🐍 Python Analysis Highlights

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from statsmodels.tsa.seasonal import seasonal_decompose
from statsmodels.tsa.arima.model import ARIMA

# Load BMW sales data
df = pd.read_csv('bmw_global_sales.csv', parse_dates=['date'])
df.set_index('date', inplace=True)

# Time-series decomposition
decomposition = seasonal_decompose(df['units_sold'], model='additive', period=12)
decomposition.plot()
plt.suptitle('BMW Global Sales — Trend & Seasonality Decomposition')
plt.tight_layout()
plt.show()
```

```python
# EV Adoption Share Over Time
ev_share = df.groupby(['year', 'powertrain_type'])['units_sold'].sum().unstack()
ev_share['ev_share_pct'] = ev_share['EV'] / ev_share.sum(axis=1) * 100

ax = ev_share['ev_share_pct'].plot(
    kind='line', marker='o', color='#1f77b4',
    figsize=(12, 5), linewidth=2
)
ax.set_title('BMW EV Adoption Rate — Global Market Share Over Time', fontsize=14)
ax.set_ylabel('EV Market Share (%)')
ax.set_xlabel('Year')
plt.tight_layout()
plt.show()
```

```python
# ARIMA Demand Forecasting
model = ARIMA(df['units_sold'], order=(2, 1, 2))
model_fit = model.fit()

forecast = model_fit.forecast(steps=12)
print(f"12-Month Demand Forecast:\n{forecast}")

# Plot forecast vs actual
fig, ax = plt.subplots(figsize=(14, 5))
df['units_sold'].plot(ax=ax, label='Actual Sales', color='steelblue')
forecast.plot(ax=ax, label='Forecasted Demand', color='orange', linestyle='--')
ax.set_title('BMW Global Sales — ARIMA Demand Forecast', fontsize=14)
ax.legend()
plt.tight_layout()
plt.show()
```

---

## 📊 Power BI Dashboard Sections

- **🌍 Global Overview** — Total units sold, revenue, YoY growth KPI cards
- **📈 Sales Trend** — Multi-year line chart with trend line and forecast overlay
- **🗺️ Regional Map** — Choropleth map of sales by country/region
- **🔋 EV vs ICE Split** — Stacked area chart showing powertrain evolution
- **🏆 Market Ranking** — Bar chart of top 10 markets by volume
- **📅 Seasonality View** — Month-wise heat map of sales patterns

---

## 📂 Repository Structure

```
bmw-global-sales-analysis/
│
├── 📁 data/
│   ├── raw/                          # Raw BMW sales datasets (CSV)
│   └── processed/                    # Cleaned & enriched data
│
├── 📁 notebooks/
│   ├── 01_data_cleaning.ipynb        # Data loading, cleaning, validation
│   ├── 02_eda.ipynb                  # Exploratory Data Analysis
│   ├── 03_regional_analysis.ipynb    # Regional revenue concentration
│   ├── 04_ev_adoption.ipynb          # EV vs ICE trend analysis
│   └── 05_time_series_forecast.ipynb # ARIMA / Prophet forecasting
│
├── 📁 dashboard/
│   └── BMW_Sales_Dashboard.pbix      # Power BI dashboard file
│
├── 📁 screenshots/
│   └── *.png                         # Dashboard & plot screenshots
│
├── requirements.txt                  # Python dependencies
└── README.md
```

---

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

---

## 💡 Key Insights Uncovered

> *(Update with your actual findings)*

- 📈 **Global Growth:** BMW global sales grew at X% CAGR over the analysis period
- 🌍 **Top Market:** [Country] accounted for X% of total global volume
- 🔋 **EV Surge:** EV unit share grew from X% to X% — a Xx increase in adoption rate
- 📉 **Demand Dip:** [Year] saw a X% decline driven by [reason — supply chain, COVID, etc.]
- 📅 **Seasonality:** Strongest sales consistently in [Q4/Q1], weakest in [Q2/Q3]
- 🔮 **Forecast:** ARIMA model projects X units sold in next 12 months (MAPE: X%)

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Python** | Data analysis, time-series modelling, visualisation |
| **Pandas / NumPy** | Data wrangling and numerical computation |
| **Matplotlib / Seaborn** | Static chart generation |
| **Statsmodels / Prophet** | ARIMA and Prophet forecasting models |
| **Power BI Desktop** | Executive dashboard and interactive reporting |
| **Jupyter Notebooks** | Analysis documentation and reproducibility |

---

## 📬 Connect With Me

**Megharaju Vakiti** — Data Analyst

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Megharaju%20Vakiti-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/megharaju-vakiti)
[![GitHub](https://img.shields.io/badge/GitHub-Megharaju--Vakiti-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Megharaju-Vakiti)

---

<div align="center">
  <em>⭐ If you found this project useful, please give it a star!</em>
</div>

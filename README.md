# 🌱 Carbon Emission Reduction in Data Centres Through Smart Scheduling

**Module:** IS6611 Applied Research in Business Analytics | Cork University Business School  
**Group:** 11 (6 members)  
**Year:** 2025–2026

---

## 📌 Project Overview

I completed this group project as a member of Group 11. Our team designed an end-to-end, carbon-aware workload scheduling approach for high-performance computing (HPC). The system forecasts grid carbon intensity up to 48 hours ahead, then recommends when flexible jobs should run while respecting their deadlines and available cluster capacity.

The aim is to reduce electricity-related Scope 2 emissions without delaying time-critical work or changing the computation itself.

---

## 🎯 Objective

- Investigate whether delay-tolerant HPC workloads can be shifted to cleaner electricity periods
- Forecast grid carbon intensity up to 48 hours ahead
- Recommend feasible, lower-carbon job start times while accounting for job duration, deadlines, node requirements, and cluster capacity
- Estimate emissions reductions under ideal, capacity-constrained, and forecast-uncertain scenarios
- Present scheduling and sustainability insights through an interactive dashboard

---

## 🔬 Methodology

| **Step** | **Technique / data** |
| --- | --- |
| Demand data | ORNL Summit per-node power telemetry, supplied as Apache Parquet; per-minute measurements across five snapshot days |
| Electricity supply data | Hourly Tennessee Valley Authority (TVA) generation by fuel type, retrieved from the U.S. EIA Open Data API; 2019–2022 |
| Data integration | Cleaned missing values and duplicates, standardised timestamps, aligned time zones, classified active nodes, aggregated demand hourly, calculated carbon intensity, and joined demand with supply |
| Descriptive analysis | Assessed cluster activity, hourly grid carbon variation, and workload shifting potential |
| Forecast evaluation | Compared six approaches using a chronological train/test split and rolling-origin evaluation for 48-hour forecasts |
| Forecast models | XGBoost, Random Forest, Decision Tree, ARIMA, SARIMA, and a naive baseline that replays the previous day's 24-hour carbon profile |
| Forecast selection | XGBoost had the best point-error metrics, but its forecast flattened within-day variation. We selected the naive baseline for scheduling because it better preserved the daily carbon-intensity shape used to identify cleaner windows |
| Individual-job scheduling | Greedy scheduler evaluates feasible windows and recommends the lowest-carbon start time within a job's deadline |
| Fleet-level optimisation | Linear programming (LP) with PuLP and CBC optimises schedules across competing jobs under shared node-capacity constraints |
| Dashboard | Streamlit dashboard with operational scheduling and sustainability/compliance views, including charts and audit-oriented outputs |

---

## 📊 Key Findings

- The HPC cluster was active **76.5%** of the time in the analysed sample.
- TVA grid carbon intensity varied by an average **51.2 gCO₂/kWh** between the cleanest and dirtiest hour of a day.
- Estimated annual emissions reduction from workload shifting was **314 tCO₂/year** under ideal conditions, **87 tCO₂/year** with cluster node capacity enforced, and **34 tCO₂/year** when 48-hour forecast uncertainty was included.
- In a representative example, an 8-hour, 20-node job with a 36-hour deadline was scheduled into a cleaner window. Estimated emissions fell from **59.03 kg CO₂** to **45.01 kg CO₂**, saving **14.03 kg CO₂ (23.8%)** for that example.
- No single hour was consistently cleanest across days; even the most frequently clean hour, 09:00, was optimal on only **9.4%** of days. This supports forecasting day-specific conditions instead of relying on a fixed schedule.

These are scenario and sample-based estimates from the project, not measured production savings or guarantees for other facilities. The theoretical annual estimate decreases as practical capacity and forecast uncertainty are included.

---

## 👤 My Contribution

I developed the **LP prescriptive optimisation model**, performed scenario analysis, supported result validation, assembled report sections, and contributed to drafting the final write-up. I also participated in weekly project meetings and optimisation-related decisions.

The project-level tools and methods below were used across the group. My specifically documented contributions were the LP optimisation model and scenario analysis; I am not claiming that I built every component listed.

---

## 🛠️ Tools & Technologies

`Python` `pandas` `NumPy` `PyArrow` `EIA Open Data API` `requests` `python-dotenv` `XGBoost` `Random Forest` `Decision Tree` `ARIMA` `SARIMA` `PuLP` `CBC` `Streamlit` `Plotly` `Matplotlib` `Seaborn`

---

## 💡 Key Learnings

- Applied descriptive, predictive, and prescriptive analytics to an energy and sustainability problem
- Built and evaluated a capacity-constrained LP scheduling model for competing workloads
- Learned that the lowest forecast error does not always produce the most useful operational forecast: preserving within-day variation mattered for choosing cleaner job windows
- Saw how capacity limits and forecast uncertainty can materially reduce theoretical emissions-saving potential
- Connected scheduling analysis with Scope 2 reporting and auditability considerations

---

## 📁 Repository Contents

Add the project materials that the group and course permit me to share. A suggested layout is:

```text
.
├── README.md
├── src/                  # application and analysis code, if approved to publish
├── data/                 # only public or approved data; avoid restricted source files
├── docs/                 # report, diagrams, or methodology, if approved
└── requirements.txt      # Python dependencies, if applicable
```

The report describes the data pipeline and dashboard, but this README does not assume those files are already present in this repository. I should update this section to match the actual files I add.

---

## ▶️ Running the Project

The report describes a Python pipeline and Streamlit dashboard, but does not provide a complete installation and run command in the available project materials. I should add verified setup instructions after placing the code, dependency list, and required EIA configuration in the repository. I should not commit API keys or `.env` files; if configuration is required, I can provide a `.env.example` containing variable names only.

---

## 🔎 Data & Reproducibility

The report describes ORNL Summit power telemetry and TVA generation history from EIA. Before sharing source data, I should check its redistribution terms and the course rules. If raw data cannot be redistributed, I can provide source links, retrieval steps, and a permitted derived sample instead.

---

## 👥 Team & Course

I completed this work with Group 11 for **IS6611 Applied Research in Business Analytics** at Cork University Business School. The report documents all six members and their individual responsibilities. I should confirm group agreement before including teammates' names or publishing shared work.

---

## ✅ Before Publishing

- Confirm that the group and course permit public release
- Remove credentials and private data
- Check that data redistribution is allowed
- Make sure the README matches the code, data, and dashboard actually included
- Add a licence only if the group has the rights to license all repository contents

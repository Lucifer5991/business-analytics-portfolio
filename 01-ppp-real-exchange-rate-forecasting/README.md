# 📈 Purchasing Power Parity & Real Exchange Rate Forecasting — Ireland and USA

**Module:** IS6025 Business Forecasting | University College Cork  
**Team Size:** 6 members  
**Year:** 2025–2026

---

## 📌 Project Overview

This project investigates whether **Purchasing Power Parity (PPP)** holds between Ireland and the United States using monthly macroeconomic data from January 2013 to December 2023, sourced from the **FRED (Federal Reserve Economic Data)** database.

---

## 🎯 Objective

- Test the validity of PPP between Ireland and the USA
- Build a time-series model to forecast the real exchange rate for 2024
- Provide data-backed macroeconomic conclusions

---

## 🔬 Methodology

| Step | Technique |
|---|---|
| Data Source | FRED Monthly Data (Jan 2013 – Dec 2023) |
| Stationarity Testing | ADF (Augmented Dickey-Fuller) & KPSS Tests |
| Cointegration Testing | Engle-Granger Two-Step Method |
| Model Selection | Box-Jenkins Methodology (ACF/PACF Analysis) |
| Final Model | ARIMA(2,1,1) — AIC: -705.49 |
| Regression | OLS (Ordinary Least Squares) |

---

## 📊 Key Findings

- The real exchange rate series was found to be **non-stationary at level** but stationary after first differencing (I(1))
- **Engle-Granger cointegration test** found no long-run equilibrium — PPP was **not supported** for the Ireland–USA pair
- **ARIMA(2,1,1)** was selected as the best-fit model based on AIC
- A **12-month 2024 real exchange rate forecast** was produced

---

## 🛠️ Tools & Technologies

`Python` `ARIMA` `OLS Regression` `ADF/KPSS Tests` `Engle-Granger Cointegration` `FRED Data` `Box-Jenkins Methodology`

---

## 💡 Key Learnings

- Applied advanced time-series analysis techniques in a real-world macroeconomic context
- Understood the limitations of PPP theory in modern, open economies
- Gained experience in model selection and forecast evaluation

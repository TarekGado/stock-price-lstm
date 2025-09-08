# Stock Price Prediction — LSTM

**Goal:** Predict **next-day closing price** for **AAPL** using an **LSTM** model with technical + macroeconomic features.

## 1) Data Sources
- **Yahoo Finance**: AAPL, NASDAQ (^IXIC), VIX (^VIX)
- **FRED**: GDP (`GDP`), CPI (`CPIAUCSL`), Unemployment (`UNRATE`), Fed Funds (`FEDFUNDS`)

## 2) Tools & Libraries
Python 3.13, `pandas`, `yfinance`, `pandas_datareader`,  
`scikit-learn`, `tensorflow` (for LSTM), `matplotlib/plotly`, `streamlit`.

## 3) Features
- **Technical**: EMA_20, RSI(14)  
- **Macro**: GDP (quarterly→daily ffill), CPI + CPI_MoM + CPI_YoY (monthly→daily ffill),  
  Unemployment, Fed Funds (monthly→daily ffill)  
- **Market**: NASDAQ (^IXIC), VIX (^VIX)

## 4) Model & Why
- **LSTM**: captures non-linear patterns and uses multiple exogenous inputs.
- Trained on rolling 70%/15%/15% split (train/validation/test).
- Safe scaling (fit on train, apply to val/test).
- Windowing: 60-day lookback → next-day target.

## 5) Results (Test Set)
- **LSTM**: MAE = **2.92**, RMSE = **3.92**, MAPE = **1.25%**

## Results

### Test predictions
![Test Prediction](reports/figures/aapl_test_pred_lstm.png)

### Validation predictions
![Validation Prediction](reports/figures/aapl_val_pred_lstm.png)

## 6) Repo Structure

# Stock Price Prediction (AAPL) — LSTM

This project predicts **next-day closing price** for **Apple (AAPL)** using an **LSTM** model with both **technical indicators** and **macroeconomic factors**.

> Single-script workflow: see `scripts/apple_stock_predection.py`.

---

## ✨ Highlights

- **Data**: Yahoo Finance (AAPL, NASDAQ ^IXIC, VIX ^VIX) + FRED (GDP, CPI, Unemployment, Fed Funds).
- **Features**:
  - Technical: **EMA_20**, **RSI(14)** (computed in pure pandas).
  - Macro: **GDP** (Q → daily ffill), **CPI** with **CPI_MoM** & **CPI_YoY** (M → daily ffill),
    **Unemployment**, **Fed Funds** (M → daily ffill).
  - Market: **NASDAQ** (^IXIC), **VIX** (^VIX).
- **Leak-safe pipeline**:
  1. Chronological split (default **70/15/15** train/val/test).
  2. **Scale on train only**, apply to val/test.
  3. **Window per split** (no leakage): 60-day lookback → 1-day ahead target.
- **Metrics**: MAE, RMSE, MAPE (printed and can be saved to `reports/metrics/`).
- **Figures**: Predicted vs. True charts saved under `reports/figures/`.

---

## 📂 Repository Structure


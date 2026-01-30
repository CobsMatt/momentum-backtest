# Systematic Momentum Strategy (Python) — Backtest + Memo

A rules-based **cross-sectional momentum** strategy tested on the **top 30 S&P 500 constituents by index weight** (as of current list), with **SPY** as benchmark.

## What’s inside
- `notebooks/momentum_backtest.ipynb` — full analysis + backtest
- `reports/strategy_memo.md` — 1–2 page strategy memo (print-friendly)
- `data/results_monthly.csv` — monthly returns + turnover
- `data/weights_monthly.csv` — monthly portfolio weights
- `figures/light/` — charts for PDF/memo
- `figures/dark/` — optional “codey” dark charts for style

## Strategy (Baseline)
- Signal: **12–1 momentum** (past 12-month return, skipping most recent month)
- Selection: top 10 stocks monthly (ranked by momentum)
- Weighting: equal weight
- Rebalance: monthly
- Costs: 10 bps × monthly turnover (turnover from weight changes)

## Results (Net of Costs, 2021-10 to 2026-01)
- Momentum CAGR: **28.12%**
- SPY CAGR: **13.27%**
- Max drawdown (Momentum vs SPY): **-20.10% vs -23.93%**
- Annualized volatility (Momentum vs SPY): **21.97% vs 15.73%**
- Sharpe (rf=0): **1.24 vs 0.87**
- Avg monthly turnover: **0.169 (~16.9%)**

Robustness (CAGR):
- 3–1 momentum: **35.48%**
- 6–1 momentum: **33.65%**
- 12–1 momentum: **28.37%**

## Notes / Limitations
- Universe defined using current top constituents (composition effects).
- Sample starts when full data coverage + lookback availability begins.
- Future work: point-in-time constituents, volatility targeting, larger universes, regime filters.

## How to run
1. Create venv + install dependencies:
   ```bash
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   py -m pip install -r requirements.txt
# Regime-Shift: Macro-Aware Tactical Asset Allocation Engine

A tactical asset allocation system that identifies hidden market regimes (Bull, Bear, and Crisis) using a Hidden Markov Model (HMM) and dynamically adjusts portfolio allocations across equities, bonds, and gold. The strategy is evaluated using a leak-free walk-forward backtesting framework with transaction costs.

## Overview

Traditional portfolios maintain fixed allocations regardless of market conditions. This project adapts portfolio weights based on the current market regime by combining:

- Hidden Markov Models (HMM) for regime detection
- Convex optimization for portfolio allocation
- Walk-forward backtesting to avoid lookahead bias

## Workflow

```text
Market Data
     │
     ▼
Feature Engineering
     │
     ▼
HMM Regime Detection
     │
     ▼
Regime-Based Portfolio Optimization
     │
     ▼
Walk-Forward Backtesting
     │
     ▼
Performance Evaluation
```

## Data

The project uses daily market data from Yahoo Finance.

| Asset             | Symbol              |
| ----------------- | ------------------- |
| Nifty 50          | `^NSEI`           |
| US Treasury Bonds | `IEF`             |
| Gold              | `GLD`             |
| Market Volatility | India VIX /`^VIX` |

## Features

The model uses:

- Momentum (5, 21, and 63-day)
- Annualized volatility (5, 21, and 63-day)
- Market volatility index (VIX)

## Method

1. Download historical market data.
2. Generate momentum and volatility features.
3. Train a 3-state Gaussian Hidden Markov Model.
4. Label regimes based on volatility characteristics.
5. Optimize portfolio weights for each regime using convex optimization.
6. Evaluate performance using walk-forward backtesting.

## Backtesting

The strategy includes:

- Walk-forward training
- No future data leakage
- Portfolio rebalancing every 5 trading days
- Transaction costs
- Comparison against:
  - 60/40 Portfolio
  - Equal Weight Portfolio

## Results

The notebook generates:

- Market regime visualization
- Transition matrix
- Portfolio allocation over time
- Equity curve
- Drawdown chart
- Performance metrics including:
  - Sharpe Ratio
  - Sortino Ratio
  - Maximum Drawdown
  - Calmar Ratio
  - Portfolio Turnover

## Installation

```bash
pip install numpy pandas matplotlib scipy yfinance hmmlearn cvxpy jupyter
```

## Running the Project

Execute the notebook:

```bash
jupyter nbconvert --to notebook --execute Regime_Shift_Capstone.ipynb --output Regime_Shift_Capstone.ipynb
```

or simply open the notebook in Jupyter and run all cells.

## Repository Structure

```
├── Regime_Shift_Capstone.ipynb
└── README.md
```

## Tech Stack

- Python 3
- NumPy
- Pandas
- Matplotlib
- SciPy
- yfinance
- hmmlearn
- cvxpy

## Notes

- Uses walk-forward validation to prevent lookahead bias.
- Portfolio statistics are computed using only historical information available at each rebalance.
- Includes a synthetic data fallback to ensure reproducibility when market data is unavailable.

  
## Quick Links

1. **Data & Feature Engineering**
   - https://www.youtube.com/watch?v=fX5bYmnHqqE
   - https://www.youtube.com/watch?v=Bru4Mkr601Q

2. **Hidden Markov Models (HMM)**
   - https://www.youtube.com/watch?v=kXqu-TqEl7Q
   - https://www.youtube.com/watch?v=9GA2WlYFeBU

3. **Portfolio Optimization**
   - https://www.youtube.com/watch?v=az7M5X3BEWU
   - https://www.youtube.com/watch?v=sjq3toGtr0U

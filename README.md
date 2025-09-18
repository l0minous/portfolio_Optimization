# Portfolio Optimization using Modern Portfolio Theory

Implementing Modern Portfolio Theory (MPT) to optimize asset allocation across a diversified portfolio of ETFs, analysis uses historical price data to find optimal portfolio weights that maximize the Sharpe ratio and minimize portfolio volatility.

## Overview

Analyzing a portfolio consisting of five sample ETFs:
- **TLT** - iShares 20+ Year Treasury Bond ETF
- **GLD** - SPDR Gold Shares ETF  
- **SPY** - SPDR S&P 500 ETF Trust
- **QQQ** - Invesco QQQ Trust (Nasdaq-100)
- **VWO** - Vanguard FTSE Emerging Markets ETF

## Features

- **Data Fetching**: Automated retrieval of historical price data using Yahoo Finance API
- **Return Analysis**: Calculation of daily and annualized returns for each asset
- **Risk Assessment**: Computation of covariance matrices and portfolio volatility
- **Monte Carlo Simulation**: Generation of 3,000 random portfolio combinations to visualize the efficient frontier
- **Portfolio Optimization**: Mathematical optimization to find:
  - Maximum Sharpe ratio portfolio
  - Minimum variance portfolio
- **Visualization**: Interactive plots showing the Markowitz bullet and optimal portfolios

## Key Results

### Optimal Sharpe Ratio Portfolio
- **Return**: 9.20%
- **Volatility**: 10.59%
- **Sharpe Ratio**: 0.87
- **Allocation**: 
  - TLT: 31.78%
  - GLD: 27.39%
  - QQQ: 40.84%
  - SPY: 0%
  - VWO: 0%

### Minimum Variance Portfolio
- **Volatility**: 9.10%
- **Allocation**:
  - TLT: 48.47%
  - GLD: 17.77%
  - SPY: 33.76%
  - QQQ: 0%
  - VWO: 0%

## Dependencies

```python
pandas
matplotlib
numpy
yfinance
scipy
```

## Installation

```bash
pip install pandas matplotlib numpy yfinance scipy
```

## Usage

1. **Run the analysis**:
   ```python
   python portfolio_optimization.py
   ```

2. **Customize the portfolio**:
   - Modify the `stocks` list to include different assets
   - Adjust the number of Monte Carlo simulations in `portfolio_simulation()`
   - Change optimization constraints (e.g., maximum weight per asset)

## Key Functions

- `fetch_data(assets)`: Downloads historical price data for specified tickers
- `portfolio_simulation(assets, iterations)`: Runs Monte Carlo simulation to generate random portfolios
- `portfolio_stats(weights, returns)`: Calculates portfolio metrics (return, volatility, Sharpe ratio)
- `minimize_sharpe()`, `minimize_volatility()`: Objective functions for optimization

## Methodology

1. **Data Collection**: Historical adjusted closing prices from 2005-2024
2. **Return Calculation**: Log returns to ensure additivity and normal distribution assumptions
3. **Risk Modeling**: Covariance matrix estimation using historical data
4. **Optimization**: Sequential Least Squares Programming (SLSQP) algorithm with constraints:
   - Weights sum to 1 (fully invested)
   - No short selling (weights ≥ 0)
   - Maximum 100% allocation per asset


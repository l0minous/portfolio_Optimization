# Portfolio Optimization using Modern Portfolio Theory

Implementing Modern Portfolio Theory (MPT) to optimize asset allocation across a diversified portfolio, featuring professional data visualizations and quantitative analysis. This project uses historical price data to find optimal portfolio weights that maximize the Sharpe ratio and minimize portfolio volatility.

## Overview

Analyzing a portfolio consisting of five assets:
- **NVDA** - NVIDIA Corporation
- **AAPL** - Apple Inc.
- **SPY** - SPDR S&P 500 ETF Trust
- **PLTR** - Palantir Technologies Inc.
- **AMZN** - Amazon.com Inc.

## Features

- **Data Fetching**: Automated retrieval of historical price data using Yahoo Finance API
- **Return Analysis**: Calculation of daily and annualized returns for each asset
- **Correlation Analysis**: Visualization of asset correlations to identify diversification opportunities
- **Risk Assessment**: Computation of covariance matrices and portfolio volatility
- **Monte Carlo Simulation**: Generation of 3,000 random portfolio combinations to visualize the efficient frontier
- **Portfolio Optimization**: Mathematical optimization to find:
  - Maximum Sharpe ratio portfolio
  - Minimum variance portfolio
- **Visualizations**: 
  - Correlation heatmap with color-coded relationships
  - Enhanced efficient frontier with Sharpe ratio gradient
  - Optimal portfolio allocation (pie and bar charts)
  - Normalized asset performance comparison

## Key Results

### Optimal Sharpe Ratio Portfolio
- **Return**: 14.84%
- **Volatility**: 15.55%
- **Sharpe Ratio**: 0.95
- **Allocation**: 
  - NVDA: 0%
  - AAPL: 40%
  - SPY: 40%
  - PLTR: 0%
  - AMZN: 20%

### Minimum Variance Portfolio
- **Return**: 11.94%
- **Volatility**: 15.31%
- **Sharpe Ratio**: 0.78
- **Allocation**:
  - NVDA: 7.49%
  - AAPL: 40%
  - SPY: 40%
  - PLTR: 0%
  - AMZN: 12.51%

## Dependencies
```python
pandas
matplotlib
numpy
yfinance
scipy
seaborn
```

## Installation
```bash
pip install pandas matplotlib numpy yfinance scipy seaborn
```

## Usage

1. **Run the analysis**:
```python
   jupyter notebook portfolio_optimization_enhanced.ipynb
```

2. **Customize the portfolio**:
   - Modify the `stocks` list to include different assets
   - Adjust the number of Monte Carlo simulations in `portfolio_simulation()`
   - Change optimization constraints (e.g., maximum weight per asset)

## Key Functions

- `fetch_data(assets)`: Downloads historical price data for specified tickers
- `portfolio_simulation(assets, iterations)`: Runs Monte Carlo simulation to generate random portfolios
- `portfolio_stats(weights, returns)`: Calculates portfolio metrics (return, volatility, Sharpe ratio)
- `visualize_optimal_weights(weights, assets)`: Creates dual visualization of optimal portfolio allocation
- `plot_enhanced_efficient_frontier()`: Plots efficient frontier with Sharpe ratio color gradient
- `minimize_sharpe()`, `minimize_volatility()`: Objective functions for optimization

## Methodology

1. **Data Collection**: Historical adjusted closing prices fetched in real-time via yfinance
2. **Correlation Analysis**: Heatmap visualization to identify diversification patterns
3. **Return Calculation**: Log returns to ensure additivity and normal distribution assumptions
4. **Risk Modeling**: Covariance matrix estimation using historical data
5. **Monte Carlo Simulation**: 3,000 random portfolio allocations to map the efficient frontier
6. **Optimization**: Sequential Least Squares Programming (SLSQP) algorithm with constraints:
   - Weights sum to 1 (fully invested)
   - No short selling (weights ≥ 0)
   - Maximum 40% allocation per asset

## Visualizations

1. **Correlation Heatmap**: Shows relationships between assets using diverging colormap
2. **Efficient Frontier**: 3,000 portfolios colored by Sharpe ratio with optimal portfolio marked
3. **Optimal Allocation**: Dual format (pie + bar) showing algorithmically-determined weights
4. **Asset Performance**: Normalized price comparison showing relative growth

## Technologies Used

Python, pandas, NumPy, Matplotlib, Seaborn, yfinance, SciPy

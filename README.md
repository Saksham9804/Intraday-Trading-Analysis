# Intraday Trading Analysis

A comprehensive analysis of high-frequency trading patterns using 5-minute interval data and daily price movements. This project explores intraday price behavior, volatility patterns, and trading strategies across multiple timeframes.

## Project Overview

This project analyzes financial market data at two different granularities to identify trading opportunities and understand price dynamics. The analysis combines 5-minute intraday bars with daily price data to create a multi-timeframe trading framework.

## Dataset

**5-Minute Intraday Data** (`simulated_5min_data.csv`)

**Columns**:
- `datetime`: Timestamp in 5-minute intervals
- `open`: Opening price for the interval
- `high`: Highest price during the interval
- `low`: Lowest price during the interval
- `close`: Closing price for the interval
- `volume`: Trading volume for the interval

**Coverage**:
- Time Period: September 29, 2021 - September 20, 2023
- Total Records: 177,877 5-minute bars
- Trading Hours: 24-hour data (includes extended hours)

**Daily Price Data** (`simulated_daily_data.csv`)

**Columns**:
- `Date`: Trading date
- `Open`: Opening price
- `High`: Daily high price
- `Low`: Daily low price
- `Close`: Closing price
- `Adj Close`: Adjusted closing price
- `Volume`: Daily trading volume

**Coverage**:
- Time Period: September 17, 2014 - September 18, 2023
- Total Records: 3,289 trading days
- Data Type: End-of-day OHLCV data

## Methodology

**Intraday Analysis**
- Analyze 5-minute price movements and volume patterns
- Identify intraday volatility clusters
- Study time-of-day effects on price behavior
- Calculate intraday technical indicators

**Multi-Timeframe Strategy**
- Combine daily trend analysis with intraday execution
- Use daily data for trend direction
- Use 5-minute data for precise entry/exit timing
- Risk management based on intraday volatility

**Key Metrics**
- Intraday volatility patterns
- Volume-weighted average price (VWAP)
- Time-of-day momentum effects
- Support/resistance levels

## Getting Started

**Prerequisites**
```bash
pip install pandas numpy matplotlib seaborn
```

**Loading Data**
```python
import pandas as pd

# Load 5-minute data
df_5min = pd.read_csv('simulated_5min_data.csv')
df_5min['datetime'] = pd.to_datetime(df_5min['datetime'])

# Load daily data
df_daily = pd.read_csv('simulated_daily_data.csv')
df_daily['Date'] = pd.to_datetime(df_daily['Date'])
```

**Basic Analysis**
```python
# Calculate intraday returns
df_5min['returns'] = df_5min['close'].pct_change()

# Group by time of day
df_5min['time'] = df_5min['datetime'].dt.time
time_patterns = df_5min.groupby('time')['returns'].mean()
```

## Files in Repository

- `Intraday.ipynb`: Jupyter notebook with complete analysis
- `simulated_5min_data.csv`: High-frequency 5-minute interval data
- `simulated_daily_data.csv`: Daily OHLCV price data
- `README.md`: This file

## Analysis Features

**Intraday Patterns**
- Opening range breakouts
- Mid-day consolidation periods
- Power hour volatility
- Extended hours behavior

**Volume Analysis**
- Volume profile analysis
- Volume-weighted indicators
- Abnormal volume detection
- Liquidity patterns throughout the day

**Volatility Studies**
- Realized volatility by time of day
- High-low range analysis
- Volatility clustering detection
- Intraday volatility forecasting

## Key Insights

1. Intraday data reveals price patterns not visible in daily data
2. Volume and volatility exhibit strong time-of-day seasonality
3. 5-minute intervals provide granular entry/exit opportunities
4. Multi-timeframe analysis improves trade timing accuracy

## Limitations

- Data represents simulated/historical prices only
- High-frequency data requires careful handling of outliers
- Transaction costs and slippage not included in analysis
- Market microstructure effects may differ in live trading
- Extended hours data may have lower liquidity
- Past patterns do not guarantee future performance

## Potential Applications

- Intraday momentum strategies
- Mean reversion trading
- VWAP execution algorithms
- Opening range breakout systems
- Time-weighted order execution
- High-frequency statistical arbitrage

## Disclaimer

**This project is for educational and research purposes only.**

This is not financial advice. Past performance does not guarantee future results. High-frequency trading involves significant risk. Always do your own research and consult with financial professionals before making investment decisions.

---

Built with Python, Pandas, NumPy, Matplotlib, Seaborn

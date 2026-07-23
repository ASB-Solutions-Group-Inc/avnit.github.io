---
layout: post
title: "Beta Calculator"
subtitle: "Quantifying systematic risk and building hedging-aware trading strategies"
tags: [python, finance, machine-learning, portfolio-analysis]
comments: false
---

Beta measures how much a stock moves when the market moves. This walkthrough computes beta from historical returns in Python, then uses it to classify risk and build hedging-aware portfolios.

*Author: Avnit Bambah — originally written 03/12/2018 (updated).*

## What Is Beta and Why Does It Matter for Trading?

Beta (β) measures a stock's **systematic risk** relative to the market index (typically S&P 500 / SPY). It answers the core question:

> **How much does this stock move when the market moves?**

### Interpreting Beta
- **β = 1.0**: Stock moves in lockstep with the market. For every 1% the market moves, the stock moves ~1%.
- **β > 1.0**: Stock is more volatile than the market (amplified moves). Higher risk, higher potential reward.
- **β < 1.0**: Stock is less volatile than the market (dampened moves). Lower volatility.
- **β < 0.0**: Stock moves inverse to the market (rare; useful for hedging).

### Trading Strategy Implications

**Defensive Portfolio (Lower Beta):**
- Choose β < 0.8 stocks for downside protection
- Reduces portfolio volatility
- Better for risk-averse investors or market downturns

**Aggressive Portfolio (Higher Beta):**
- Overweight β > 1.2 stocks for amplified returns
- Capitalizes on bull markets
- Requires strong conviction and risk tolerance

**Market-Neutral Hedging:**
- Pair long positions (high β) with short positions (low β)
- Reduces net beta exposure while maintaining alpha capture
- Typical quant fund strategy

---

## Step 1: Load Market Data and Prepare Returns


```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from pandas_datareader import data

# Configure inline plotting for Jupyter notebooks
%matplotlib inline
```

**What each import does:**
- `pandas`: Data manipulation and time-series analysis
- `numpy`: Numerical computations (covariance, variance calculations)
- `matplotlib.pyplot`: Visualization of results
- `pandas_datareader`: Fetches historical stock data from Yahoo Finance

---

## Step 2: Load Your Portfolio Holdings

```python
# Load a CSV file containing your portfolio ticker symbols
# Expected format: single column with ticker symbols (AAPL, MSFT, etc.)
df = pd.read_csv("./holdings-xlk.csv")
```

This reads your portfolio holdings. The CSV file should contain one ticker symbol per row.


---

## Step 3: Build Complete Ticker List (Portfolio + Market Benchmark)

```python
# Core tickers: market benchmark + representative index holdings
base_tickers = ['AAPL', 'MSFT', 'SPY', 'CME', 'GOOG', 'VVI', 'agg']

# Add holdings from CSV file
symbols_df = df.iloc[:, [0]]  # Extract first column
symbols_list = symbols_df.values.tolist()

# Clean up formatting and add to ticker list
tickers = base_tickers.copy()
for i in range(1, len(symbols_list)):
    ticker = str(symbols_list[i]).replace('[\'', '').replace('\']', '')
    if ticker not in tickers:  # Avoid duplicates
        tickers.append(ticker)

print(f"Total tickers to analyze: {len(tickers)}")
print(tickers)
```

**Output:**
```
Total tickers to analyze: 26
['AAPL', 'MSFT', 'SPY', 'CME', 'GOOG', 'VVI', 'agg', 'BETR', 'BUFF', ...]
```

**SPY (S&P 500 ETF) acts as our market benchmark** — we'll calculate each stock's beta relative to SPY's returns.




---

## Step 4: Fetch Historical Price Data from Yahoo Finance

```python
# Configuration
DATA_SOURCE = 'yahoo'
START_DATE = '2000-01-01'
END_DATE = '2018-03-24'

# Fetch adjusted closing prices for all tickers
try:
    panel_data = data.DataReader(tickers, DATA_SOURCE, START_DATE, END_DATE)
    print(f"Successfully fetched data from {START_DATE} to {END_DATE}")
except Exception as e:
    print(f"Error fetching data: {e}")

# Extract only adjusted closing prices (ignore OHLCV data)
close_prices = panel_data.loc['Adj Close']

# Create complete date range (business days only, matches market trading days)
business_dates = pd.date_range(start=START_DATE, end=END_DATE, freq='B')

# Reindex to fill gaps and align all tickers to same dates
close_prices = close_prices.reindex(business_dates)

print(f"Price data shape: {close_prices.shape}")
print(f"Data quality: {(1 - close_prices.isna().sum().sum() / close_prices.size) * 100:.1f}% complete")
```

**What's happening:**
1. **Data retrieval**: Pulls historical adjusted close prices from Yahoo Finance
2. **Reindexing**: Fills gaps to ensure consistent date alignment across all tickers
3. **Business days only**: Uses 'B' frequency to match market trading days (excludes weekends)


---

## Step 5: Calculate Daily Percentage Returns

```python
# Shift prices forward by 1 day to compute returns
# Mathematically: daily_return = (price_today / price_tomorrow - 1) * 100
close_prices_tomorrow = close_prices.shift(-1)

# Calculate daily returns as percentage change
daily_returns_pct = ((close_prices / close_prices_tomorrow) - 1) * 100

print("Daily returns matrix computed successfully")
print(f"Shape: {daily_returns_pct.shape} ({len(business_dates)} trading days × {len(tickers)} stocks)")
```

**Understanding the Return Formula:**

$$\text{Return}_{t} = \frac{P_t}{P_{t+1}} - 1$$

This gives us the 1-day return. We multiply by 100 to express as percentages.

**Example:** If Stock A closes at $100 and opens tomorrow at $102, the 1-day return is +2%.

These daily returns become our fundamental data for computing beta — we'll measure how each stock's returns co-vary with SPY's returns over the entire period.

---

## Step 6: Calculate Covariance Matrix

```python
# Compute pairwise covariances between all stocks' daily returns
covariance_matrix = daily_returns_pct.cov()

print("Covariance matrix shape:", covariance_matrix.shape)
print("\nFirst few stocks' covariance with SPY:")
print(covariance_matrix['SPY'].head(10))
```

**What is covariance?**

$$\text{Cov}(X, Y) = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \bar{X})(Y_i - \bar{Y})$$

- Positive covariance → stocks tend to move together
- Negative covariance → stocks move in opposite directions
- Magnitude indicates strength of relationship

SPY's covariance with itself (SPY's variance) appears on the diagonal.

---

## Step 7: Extract Market Returns and Calculate Variance

```python
# SPY is located at column index 20 (S&P 500 benchmark)
# Market benchmark index position
MARKET_INDEX = 20  # Named constant instead of magic number

# Extract market (SPY) returns
market_returns = daily_returns_pct.iloc[:, MARKET_INDEX]

# Remove NaN values (missing trading days)
market_returns_clean = market_returns.dropna()

# Calculate variance (covariance of a variable with itself)
market_variance = market_returns_clean.var()

print(f"Market (SPY) average daily return: {market_returns_clean.mean():.4f}%")
print(f"Market variance (σ²): {market_variance:.6f}")
print(f"Market std dev (σ): {np.sqrt(market_variance):.4f}%")
```

**Interpreting Market Variance:**

Variance tells us how much SPY's daily returns deviate from their mean. Higher variance = more volatile market environment.

A market variance of ~1.48 means SPY's daily returns typically deviate by roughly ±1.2% from the mean.

---

## Step 8: Calculate Individual Stock Betas

```python
# Calculate beta for each stock relative to the market
# Formula: β = Cov(stock, market) / Var(market)

beta_values = {}

for stock in daily_returns_pct.columns:
    stock_returns = daily_returns_pct[stock].dropna()
    
    # Covariance between this stock and market
    covariance_with_market = np.cov(stock_returns, market_returns_clean)[0, 1]
    
    # Beta = Covariance / Market Variance
    beta = covariance_with_market / market_variance
    beta_values[stock] = beta

# Create DataFrame for visualization
beta_df = pd.DataFrame(list(beta_values.items()), columns=['Stock', 'Beta'])
beta_df = beta_df.sort_values('Beta', ascending=False)

print("Top 10 stocks by beta (most market-sensitive):")
print(beta_df.head(10))
print("\nBottom 10 stocks by beta (least market-sensitive):")
print(beta_df.tail(10))
```

**The Beta Formula Explained:**

$$\beta = \frac{\text{Cov}(\text{Stock Return}, \text{Market Return})}{\text{Var}(\text{Market Return})}$$

This is the **CAPM beta** — the fundamental measure of systematic risk. It tells us:
- How many basis points the stock moves for each basis point the market moves
- How much of the stock's variance is explained by market movements (systematic vs idiosyncratic risk)

---

## Step 9: Interpret Beta Results and Build Trading Strategy

```python
# Categorize stocks by beta range
beta_df['Category'] = pd.cut(beta_df['Beta'], 
                              bins=[-np.inf, 0.8, 1.0, 1.2, np.inf],
                              labels=['Defensive', 'Market-Tracking', 'Aggressive', 'Very Aggressive'])

print("Beta Distribution by Category:")
print(beta_df['Category'].value_counts().sort_index())

# Example strategy: Construct a hedged portfolio
print("\n" + "="*60)
print("TRADING STRATEGY EXAMPLE: Market-Neutral Hedge")
print("="*60)

# Select defensive and aggressive stocks
defensive_stocks = beta_df[beta_df['Category'] == 'Defensive'].head(3)['Stock'].tolist()
aggressive_stocks = beta_df[beta_df['Category'] == 'Aggressive'].head(3)['Stock'].tolist()

print(f"\nDefensive positions (low β, downside protection):")
for stock in defensive_stocks:
    beta = beta_df[beta_df['Stock'] == stock]['Beta'].values[0]
    print(f"  {stock}: β = {beta:.3f} — Long position")

print(f"\nAggresssive positions (high β, upside amplification):")
for stock in aggressive_stocks:
    beta = beta_df[beta_df['Stock'] == stock]['Beta'].values[0]
    print(f"  {stock}: β = {beta:.3f} — Short position (hedge)")

# Calculate net portfolio beta
portfolio_beta = np.mean([beta_df[beta_df['Stock'] == s]['Beta'].values[0] for s in defensive_stocks]) \
                 - np.mean([beta_df[beta_df['Stock'] == s]['Beta'].values[0] for s in aggressive_stocks])

print(f"\nPortfolio Net Beta: {portfolio_beta:.3f}")
if portfolio_beta < 0.2:
    print("✓ Market-neutral: Protected from market swings while capturing alpha")
elif portfolio_beta < 0.8:
    print("✓ Defensively positioned: Reduced downside in market correction")
else:
    print("⚠ Bullish bias: Amplifies market movements (higher risk)")
```

**Key Insights:**

1. **Beta clustering**: Most stocks have β between 0.8–1.2 (market-like behavior)
2. **Outliers matter**: A few stocks with very high/low beta significantly impact portfolio risk
3. **Hedging principle**: Pair longs and shorts by beta to neutralize market risk
4. **Regulatory risk**: Market conditions change; beta is historical, not predictive

---

## Limitations & Assumptions

- **Look-back bias**: Historical beta doesn't guarantee future relationships
- **Regime changes**: Beta shifts during market crises (loses predictive power in tail events)
- **Liquidity mismatch**: Works best for large-cap stocks with continuous trading
- **Non-linear relationships**: Assumes linear correlation with market (fails for tail risk hedging)

---

## Conclusion

Beta is your **first line of defense** in portfolio construction. Use it to:
- **Classify risk**: Know which stocks amplify or dampen market moves
- **Hedge efficiently**: Pair high-β positions with low-β shorts
- **Optimize allocation**: Match portfolio beta to your risk tolerance
- **Monitor drift**: Track beta changes to detect regime shifts

In the modern market, combine beta with factor exposure (momentum, value, quality) for a complete risk framework.



# stock-price-forecaster
A baseline ML study using Linear Regression to forecast stock prices on NSE India and global markets
# Stock Price Forecasting — A Baseline ML Study
### Linear Regression on Historical Closing Prices (NSE India & Global Markets)

A Python-based stock price predictor built in Jupyter Notebook. The tool fetches 
5 years of live data for any stock on NSE India or global exchanges, trains a 
Linear Regression model on historical closing prices, and outputs a predicted 
price N days ahead with a BUY/HOLD/SELL signal.

## Tech Stack
- Python
- pandas
- numpy
- scikit-learn
- yfinance
- matplotlib
- Jupyter Notebook

## Methodology
- **Features:** Closing price plus N lagged closing prices (N = user's chosen forecast horizon)
- **Target:** Closing price exactly N trading days in the future
- **Train/test split:** Temporal — first 80% training, last 20% testing. No shuffling.
- **Evaluation:** MAE compared against a naive baseline ("future price = today's price")

## Sample Results — 30 Day Forecast Horizon

| Stock    | Market    | Model MAE | Naive MAE | Beat Baseline? |
|----------|-----------|-----------|-----------|----------------|
| RELIANCE | NSE India | ₹63.17    | ₹70.78    | ✅ Yes        |
| TCS      | NSE India | ₹251.36   | ₹207.59   | ❌ No         |
| INFY     | NSE India | ₹108.42   | ₹105.69   | ❌ No         |
| AAPL     | NASDAQ    | \$22.39   | \$18.69   | ❌ No         |
| TSLA     | NASDAQ    | \$68.25   | \$39.42   | ❌ No         |
| GOOGL    | NASDAQ    | \$37.59   | \$33.78   | ❌ No         |

1 out of 6 stocks (16.7%) beat the naive forecast. The model learns long-run 
price persistence — a known limitation of price-level forecasting documented 
in the notebook.

## Limitations
- Price autocorrelation means a significant portion of predictive power comes 
  from persistence rather than learned signal
- Single point prediction only — does not model the daily path to the target
- Uses closing prices only — no volume, volatility, or macroeconomic features

## How to Run
1. Clone the repository
2. Open `Stock Price Forecasting - A Baseline ML Study.ipynb` in Jupyter Notebook
3. Run all cells in order
4. Enter market (IN or GLOBAL), stock name, and forecast horizon when prompted

## Version
This is **Version 1** — price level prediction using lagged closing prices.

**Version 2 (in progress)** will restructure the problem as return prediction 
with technical indicators (RSI, MACD, moving averages, momentum, volatility) 
and evaluate via strategy backtesting against buy-and-hold benchmarks.

# 📈 Financial Market Analysis Tool

A professional Python-based financial analytics application for FICC (Fixed Income, Credit, and Currencies) and trading analysis built with Streamlit.

## Features

- **Multi-Asset Support**: Analyze stocks, indices, cryptocurrencies, and forex pairs simultaneously
- **Price Analysis**: Historical price data visualization and time-series charts
- **Returns Analysis**: Daily percentage returns with statistical distribution histograms
- **Volatility Metrics**: 
  - 30-day rolling volatility (annualized)
  - Annual volatility statistics
  - Volatility trends over time
- **Correlation Analysis**: Cross-asset correlation matrix with heatmap visualization
- **Data Export**: Download raw price data as CSV for further analysis
- **Professional UI**: Clean, intuitive Streamlit interface with organized sections

## Prerequisites

- Python 3.8 or higher
- pip (Python package manager)

## Installation

### 1. Install Required Dependencies

```bash
pip install streamlit yfinance pandas numpy matplotlib
```

Or install from requirements file:

```bash
pip install -r requirements.txt
```

### 2. Run the Application

```bash
streamlit run "Financial Market Analysis Tool.py"
```

The app will open in your default browser at `http://localhost:8501`

## Usage

### Step 1: Enter Asset Tickers
In the input field, enter comma-separated ticker symbols:
- **Stocks**: AAPL, MSFT, GOOGL, RELIANCE.NS
- **Indices**: ^GSPC (S&P 500), ^NSEI (Nifty 50), ^IXIC (NASDAQ)
- **Forex**: EURUSD=X, USDINR=X, GBPUSD=X
- **Crypto**: BTC-USD, ETH-USD

Example: `AAPL, MSFT, SPY, EURUSD=X`

### Step 2: Select Date Range
- **Start Date**: Beginning of analysis period (default: 2020-01-01)
- **End Date**: End of analysis period (default: today's date)

### Step 3: Run Analysis
Click the **"Run Analysis"** button to fetch data and generate all analytics.

### Step 4: Review Results
The app generates:
1. **Raw Price Data**: Table of historical adjusted close prices
2. **Price Time-Series**: Chart showing price trends for all assets
3. **Daily Returns**: Table of daily percentage returns
4. **Returns Distribution**: Histograms showing return distributions
5. **Rolling Volatility**: 30-day rolling annualized volatility chart
6. **Annualized Volatility**: Summary statistics for each asset
7. **Correlation Matrix**: Table and heatmap of return correlations

### Step 5: Export Data
Download the price data as CSV using the **"Download Price Data (CSV)"** button for further analysis in Excel or other tools.

## Technical Details

### Key Metrics

**Returns**: Simple daily percentage change of adjusted close prices
```
Returns = (Price_t - Price_t-1) / Price_t-1
```

**Annualized Volatility**: Standard deviation of daily returns scaled to annual frequency
```
Annual Volatility = Daily Volatility × √252
(252 = trading days per year)
```

**Rolling Volatility**: 30-day window of annualized volatility, recalculated daily
```
Rolling Vol_t = Std Dev(Returns_t-30:t) × √252
```

**Correlation**: Pearson correlation coefficient between daily returns of asset pairs

### Data Source

Market data is sourced from **Yahoo Finance** via the `yfinance` library, providing:
- Real-time and historical price data
- Adjusted closing prices (accounting for splits and dividends)
- Global coverage of stocks, indices, FX, and crypto

## Example Workflow

```
1. Input: "RELIANCE.NS, ^NSEI, USDINR=X"
2. Date Range: 2023-01-01 to 2024-12-04
3. Click "Run Analysis"
4. View:
   - Historical prices for Reliance, Nifty 50, and INR/USD
   - Correlation between these assets
   - Individual volatility trends
5. Download CSV for spreadsheet analysis
```

## Troubleshooting

### Issue: "No data returned"
- **Cause**: Invalid ticker symbol or date range with no trading data
- **Solution**: Verify ticker symbols at Yahoo Finance and adjust dates

### Issue: "Empty DataFrame"
- **Cause**: yfinance data fetch failed
- **Solution**: Check internet connection and try again

### Issue: Streamlit app not opening
- **Cause**: Port 8501 already in use
- **Solution**: Run on different port:
  ```bash
  streamlit run "Financial Market Analysis Tool.py" --server.port 8502
  ```

## File Structure

```
Financial Market Analysis Tool.py   # Main Streamlit application
README.md                           # This file
requirements.txt                    # Python dependencies
```

## Requirements

See `requirements.txt`:
```
streamlit>=1.28.0
yfinance>=0.2.32
pandas>=2.0.0
numpy>=1.24.0
matplotlib>=3.7.0
```

## Performance Notes

- **Data Fetching**: First run may take 10-30 seconds depending on date range and number of assets
- **Caching**: Streamlit caches results; re-running with same inputs is instant
- **Browser**: Works on Chrome, Firefox, Safari, Edge (recommended: Chrome)

## Limitations

- Historical data limited to ~40 years (Yahoo Finance availability)
- Forex pairs require `=X` suffix (e.g., EURUSD=X)
- Real-time data may lag by 15-20 minutes
- Cryptocurrency data may have gaps or lower coverage

## Future Enhancements

- Advanced risk metrics (VaR, Sharpe ratio, Sortino ratio)
- Technical indicators (RSI, MACD, Bollinger Bands)
- Portfolio optimization and backtesting
- Multi-timeframe analysis (intraday, weekly, monthly)
- Machine learning-based forecasting
- Options analytics and Greeks
- Fixed income analytics (bond yields, duration)

## License

This tool is for educational and research purposes only.

## Disclaimer

Market data may have delays or inaccuracies. Always verify data before making trading decisions. This tool is not financial advice. Use at your own risk.

## Support & Contact

For issues or feature requests, ensure all dependencies are installed and try updating:
```bash
pip install --upgrade streamlit yfinance pandas numpy matplotlib
```
**Built using Python, Pandas, Matplotlib & Streamlit**

Last Updated: December 4, 2025

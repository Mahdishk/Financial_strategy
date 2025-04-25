# Financial Strategy Backtesting

This project implements a financial trading strategy for cryptocurrencies (Bitcoin and Ethereum) using technical indicators such as the **Awesome Oscillator (AO)** and **Relative Strength Index (RSI)**. The strategy is backtested on historical data fetched from Yahoo Finance, and performance metrics such as net profit, maximum drawdown, Sharpe ratio, and Sortino ratio are calculated.

---

## Features

1. **Data Fetching:**
   - Historical price data for Bitcoin (`BTC-USD`) and Ethereum (`ETH-USD`) is downloaded using the `yfinance` library.
   - Data is processed for two timeframes:
     - **Daily data**
     - **10-day aggregated data**

2. **Technical Indicators:**
   - **Awesome Oscillator (AO):**
     - Calculated as the difference between a short-term and long-term simple moving average (SMA).
   - **Relative Strength Index (RSI):**
     - Measures the speed and change of price movements to identify overbought or oversold conditions.

3. **Trading Strategy:**
   - **Entry Conditions:**
     - **Long Entry:** AO > 0 and RSI < 70.
     - **Short Entry:** AO < 0 and RSI > 30.
   - **Exit Conditions:**
     - **Long Exit:** RSI > 65, AO decreasing, or a 5% stop-loss.
     - **Short Exit:** RSI < 35, AO increasing, or a 5% stop-loss.

4. **Backtesting:**
   - Simulates trades based on the strategy and calculates portfolio performance over time.
   - Metrics calculated:
     - **Net Profit**
     - **Maximum Drawdown**
     - **Sharpe Ratio**
     - **Sortino Ratio**

5. **Visualization:**
   - Displays trade details and portfolio performance for each timeframe.

---

## File Structure

### finance_strategy.ipynb
This Jupyter Notebook contains the following key components:

1. **Data Fetching and Preprocessing:**
   - Downloads historical data for the specified tickers and date range.
   - Calculates AO and RSI indicators.
   - Aggregates daily data into 10-day periods.

2. **Trading Strategy Simulation:**
   - Implements the trading logic for entering and exiting positions.
   - Tracks trades and calculates profits for both long and short positions.

3. **Backtesting:**
   - Evaluates the strategy's performance using portfolio simulation.
   - Calculates key performance metrics.

4. **Results Display:**
   - Outputs trade details and performance metrics for both daily and 10-day timeframes.

---

## How to Use

1. **Install Dependencies:**
   Ensure you have the required Python libraries installed:
   ```bash
   pip install yfinance pandas numpy matplotlib
   ```

2. **Run the Notebook:**
   Open the finance_strategy.ipynb file in Jupyter Notebook or JupyterLab and execute the cells sequentially.

3. **Customize Parameters:**
   - Modify the `tickers` list to include other cryptocurrencies or assets.
   - Adjust the date range (`start_date` and `end_date`) to test different periods.
   - Tune the strategy parameters (e.g., AO windows, RSI thresholds, stop-loss) to optimize performance.

4. **View Results:**
   - The notebook will display trade details and performance metrics for each ticker and timeframe.
   - Analyze the results to evaluate the strategy's effectiveness.

---

## Key Functions

### 1. `calculate_ao(data, short_window, long_window, price_col)`
Calculates the Awesome Oscillator (AO) using short-term and long-term SMAs.

### 2. `calculate_rsi(data, periods, price_col)`
Calculates the Relative Strength Index (RSI) based on price changes over a specified period.

### 3. `simulate_strategy(data, timeframe_name)`
Simulates the trading strategy and generates a list of trades based on entry and exit conditions.

### 4. `backtest_strategy(trades, data, initial_capital, R, S)`
Performs backtesting by simulating portfolio performance and calculating key metrics.

---

## Example Output

### Backtest Results for `BTC-USD` (Daily Data):
```
Net Profit: $120.50
Max Drawdown: -0.0450
Sharpe Ratio: 1.2345
Sortino Ratio: 1.5678
```

### Backtest Results for `ETH-USD` (10-Day Data):
```
Net Profit: $85.30
Max Drawdown: -0.0320
Sharpe Ratio: 1.0456
Sortino Ratio: 1.2345
```

---

## Notes

- The strategy is for educational purposes only and should not be used for live trading without further validation.
- Performance depends on the chosen parameters, timeframes, and market conditions.
- Ensure data integrity by verifying the downloaded data before running the strategy.

---

## License

This project is open-source and available under the MIT License.
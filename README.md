# 📈 VWAP Pullback Intraday Trading Bot (OANDA)

A Python-based intraday trading bot that automatically identifies and executes VWAP pullback continuation trades on index CFDs (e.g. S&P 500) using the OANDA v20 API.

This project demonstrates:
- real-time market data ingestion
- indicator computation
- rule-based trade signal generation
- automated order execution with broker-managed risk

⚠️ FOR EDUCATIONAL AND RESEARCH PURPOSES ONLY  
This project was created for programming practice and portfolio purposes only.

---

## 🚀 Strategy Overview

The bot implements a VWAP Pullback Continuation strategy, a widely used intraday framework in professional trading.

### Core Idea
Trade in the direction of the session bias after a temporary pullback.

### Long Setup
- Price above VWAP (bullish bias)
- Price pulls back below EMA(20)
- Price reclaims EMA(20)
- Enter long at market
- Stop below recent structure
- Take profit at a fixed risk-reward ratio

### Short Setup
- Price below VWAP (bearish bias)
- Price pulls back above EMA(20)
- Price rejects EMA(20)
- Enter short at market
- Stop above recent structure
- Take profit at a fixed risk-reward ratio

---

## 🧠 Indicators Used

- VWAP (session-reset, price-based)
- EMA(20) for pullback timing
- Mid price (bid/ask averaged)
- Recent structure highs/lows for risk placement

All indicators are computed using pandas and pandas_ta.

---

## ⚙️ Features

- Live candle data from OANDA
- Bid/ask-aware pricing
- Automated market orders
- Server-side stop loss and take profit
- Position check to prevent double entries
- Configurable timeframe and candle count
- Clean modular code structure

---

## 🏗 Project Structure

    .
    ├── stock_classifier_v3.ipynb   # Main notebook
    ├── config_example.py           # Template for API credentials
    ├── .gitignore                  # Protects secrets
    ├── README.md                   # Project documentation

Note: config.py is intentionally ignored by git and must be created locally.

---

## 🔐 Setup Instructions

### 1. Clone the repository

    git clone https://github.com/aidankaras/algorithmic_stock_trading.git
    cd algorithmic_stock_trading

### 2. Install dependencies

    pip install oandapyV20 pandas pandas_ta

### 3. Create your config file

Create a file named config.py (DO NOT COMMIT THIS FILE):

    OANDA_API_KEY = "YOUR_API_KEY"
    OANDA_ACCOUNT_ID = "YOUR_ACCOUNT_ID"

Use an OANDA practice account for testing.

---

## ▶️ How to Run

Open the notebook and run cells in order, or call:

    run_bot()

What happens when you run it:
1. Fetches latest completed candles
2. Computes indicators
3. Evaluates the most recent closed candle
4. If conditions are met and no position is open, places a trade
5. Exits automatically via stop loss or take profit

---

## 🔄 Trade Lifecycle (Important)

- The bot enters trades automatically
- The bot does NOT manually exit trades
- Stop loss and take profit are handled by OANDA
- Re-running the bot while a position is open will NOT place new trades

---

## ⚠️ Risk Disclaimer

Trading leveraged instruments such as CFDs involves substantial risk and may not be suitable for all investors.

This software:
- does not guarantee profitability
- does not account for slippage or extreme volatility
- is provided as-is, without warranty

You are solely responsible for any trades executed using this code.

---

## 📌 Future Improvements

Planned enhancements:
- Time-of-day trading filters
- Trade logging to CSV or database
- Backtesting framework

---

## 📬 Contact

If you are reviewing this project as part of a portfolio or interview and have questions about the strategy, design choices, or implementation, feel free to reach out.

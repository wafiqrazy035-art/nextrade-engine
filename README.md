<div align="center">

```
 ███╗   ██╗███████╗██╗  ██╗████████╗██████╗  █████╗ ██████╗ ███████╗
 ████╗  ██║██╔════╝╚██╗██╔╝╚══██╔══╝██╔══██╗██╔══██╗██╔══██╗██╔════╝
 ██╔██╗ ██║█████╗   ╚███╔╝    ██║   ██████╔╝███████║██║  ██║█████╗
 ██║╚██╗██║██╔══╝   ██╔██╗    ██║   ██╔══██╗██╔══██║██║  ██║██╔══╝
 ██║ ╚████║███████╗██╔╝ ██╗   ██║   ██║  ██║██║  ██║██████╔╝███████╗
 ╚═╝  ╚═══╝╚══════╝╚═╝  ╚═╝   ╚═╝   ╚═╝  ╚═╝╚═╝  ╚═╝╚═════╝ ╚══════╝
```

# NexTrade Engine

**AI Trading Engine — Lightweight, Multi-Market, Runs on Mobile**

[![PyPI version](https://badge.fury.io/py/nextrade-engine.svg)](https://badge.fury.io/py/nextrade-engine)
[![Python](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20MacOS%20%7C%20Android-lightgrey)](https://pypi.org/project/nextrade-engine)

*The first AI trading engine designed to think like a human trader — lightweight enough to run on your phone.*

</div>

---

## ✨ Why NexTrade?

| Feature | NexTrade | TensorFlow | PyTorch |
|---------|----------|------------|---------|
| Mobile Ready | ✅ Yes | ❌ Heavy | ❌ Heavy |
| No GPU needed | ✅ Yes | ⚠️ Optional | ⚠️ Optional |
| Setup time | ✅ 30 seconds | ❌ Hours | ❌ Hours |
| Trading-focused | ✅ Built-in | ❌ Manual | ❌ Manual |
| Multi-language | ✅ 4 languages | ❌ No | ❌ No |
| Terminal wizard | ✅ Auto guide | ❌ No | ❌ No |

---

## 🚀 Installation

```bash
pip install nextrade-engine
```

That's it. No CUDA, no GPU, no complex setup.

---

## ⚡ Quick Start

```python
import nextrade

# Get real-time signal
nextrade.start("momentum", market="BTCUSD")

# Train ML engine
nextrade.train_ml("BTCUSD", "H1")

# Signal with ML
nextrade.start("adaptive", market="BTCUSD", use_ml=True)
```

When you type `import nextrade`, a wizard automatically appears in your terminal showing all available strategies and how to use them.

---

## 📖 Full Usage Guide

### 1. Get Trading Signals

```python
import nextrade

# Basic signal — rule-based engine
nextrade.start("momentum", market="BTCUSD")
nextrade.start("reversal", market="EURUSD", timeframe="H4")
nextrade.start("scalping", market="XAUUSD", timeframe="M15")
nextrade.start("swing",    market="AAPL",   timeframe="D1")
nextrade.start("adaptive", market="ETHUSD")  # AI picks best strategy

# With ML engine
nextrade.train_ml("BTCUSD", "H1")  # train first
nextrade.start("adaptive", market="BTCUSD", use_ml=True)
```

**Available strategies:**
| Strategy | Description | Best for |
|----------|-------------|----------|
| `momentum` | Follow strong trends | Trending markets |
| `reversal` | Seek price reversals | Overbought/oversold |
| `scalping` | Quick entries, small targets | High frequency |
| `swing` | Hold hours to days | Major swings |
| `adaptive` | AI auto-selects | Any market condition |

### 2. Train the ML Engine

```python
import nextrade

# Train with different markets and timeframes
nextrade.train_ml("BTCUSD", "H1")          # Bitcoin, 1-hour
nextrade.train_ml("EURUSD", "H4", bars=2000)  # Forex, 4-hour
nextrade.train_ml("AAPL",   "D1")          # Stock, daily

# Check ML status
nextrade.ml_status()
```

**Output example:**
```
 NexTrade ML Status
 ─────────────────────────────────────
 Winrate         :  50.3%
 Price Predictor :  55.7%
 Pattern Classif :  40.9%
 Signal Filter   :  45.0%
 Total Features  :  30
 Samples Train   :  592
```

### 3. Scan Multiple Markets

```python
import nextrade

# Scan 4 markets at once
nextrade.scan(["BTCUSD", "EURUSD", "XAUUSD", "AAPL"])

# Scan with ML
nextrade.train_ml("BTCUSD")
nextrade.scan(["BTCUSD", "ETHUSD", "SOLUSD"], use_ml=True)
```

**Output example:**
```
 NexTrade Market Scanner
 ──────────────────────────────────────────────────────
 MARKET         HARGA      SIGNAL   CONF   ENGINE
 ──────────────────────────────────────────────────────
 BTCUSD     71,659.82     SELL    63.2%   ML+rule
 EURUSD          1.152     HOLD    45.1%   rule
 XAUUSD      3,234.50      BUY    71.4%   rule
 AAPL           172.30      BUY    58.9%   rule
 ──────────────────────────────────────────────────────
 ★  BUY  : XAUUSD (71.4%)
 ★  SELL : BTCUSD (63.2%)
```

### 4. Backtest Strategy

```python
import nextrade

# Backtest on 1 year of real BTC data
nextrade.backtest("momentum", market="BTCUSD", timeframe="D1")

# Custom parameters
nextrade.backtest(
    strategy    = "adaptive",
    market      = "EURUSD",
    timeframe   = "H4",
    bars        = 1000,
    sl_pct      = 1.5,   # stop loss 1.5%
    tp_pct      = 3.0,   # take profit 3%
    agresivitas = 40,
)
```

**Output example:**
```
 NexTrade Backtest Engine
 ────────────────────────────────────────────────
 Strategy    :  momentum
 Total Bars  :  365 candles
 Capital     :  $10,000
 Stop Loss   :  2.0%
 Take Profit :  4.0%
 ────────────────────────────────────────────────

 Backtest Results
 ────────────────────────────────────────────────
 Total Trades   :  52
 Win / Loss     :  24 / 28
 Winrate        :  46.1%
 Total Return   :  +42.57%  ($14,256)
 Profit Factor  :  1.43
 Max Drawdown   :  19.73%
 Risk:Reward    :  1 : 1.75
 ────────────────────────────────────────────────
 Grade          :  B — Good, usable
```

### 5. AI Brain System

```python
import nextrade

# Train brain with real data
nextrade.train("hybrid", market="BTCUSD", timeframe="D1")

# Check brain status
nextrade.brain_status()

# Set signal aggressiveness (0=conservative, 100=aggressive)
nextrade.set_agresivitas(20)  # very selective
nextrade.set_agresivitas(50)  # balanced
nextrade.set_agresivitas(80)  # aggressive
```

**Brain status output:**
```
 🧠  NexTrade Brain — Model Status
 ─────────────────────────────────────────────
 IQ Model       :  ████████░░░░░░░░  48 / 100  (Developing)
 Active Neurons :  236 / 2,000  connected  (11.8%)
 Aggressiveness :  ████░░░░░░░░░░░░  30%  (Conservative)
 Learning Mode  :  HYBRID
 Win Rate       :  56.0%  (560/1000 correct)
 Last Trained   :  2026-04-08 09:00:00
```

### 6. Multi-Language Support

```python
import nextrade

# Switch language
nextrade.set_language('en')  # English
nextrade.set_language('id')  # Bahasa Indonesia
nextrade.set_language('my')  # Bahasa Melayu
nextrade.set_language('ar')  # العربية

# All output follows selected language automatically
nextrade.start("momentum", market="BTCUSD")

# Show all available languages
nextrade.language()
```

### 7. Market Regime Detection

```python
import nextrade

# Detect current market condition
r = nextrade.regime("BTCUSD", "H1")
print(r["regime"])  # TRENDING / RANGING / VOLATILE

r = nextrade.regime("EURUSD", "H4")
print(r["trend_strength"])
print(r["volatility"])
```

---

## 📊 Supported Markets

### Forex
`EURUSD` `GBPUSD` `USDJPY` `AUDUSD` `USDCAD` `XAUUSD` (Gold) `XAGUSD` (Silver)

### Crypto
`BTCUSD` `ETHUSD` `BNBUSD` `SOLUSD` `XRPUSD` `DOGEUSD`

### Stocks
`AAPL` `TSLA` `GOOGL` `MSFT` `NVDA` `BBCA` `BBRI` `TLKM`

### Indices
`SPX500` `NASDAQ` `IHSG` `NIKKEI`

### Timeframes
`M1` `M5` `M15` `M30` `H1` `H4` `D1` `W1`

---

## 🧠 How NexTrade ML Works

NexTrade uses **3 specialist models** combined by an ensemble meta-learner:

```
Raw OHLCV Data
      ↓
Feature Engineering (30 features)
      ↓
┌─────────────┬──────────────────┬───────────────┐
│   Price     │    Pattern       │    Signal     │
│  Predictor  │   Classifier     │    Filter     │
│(RandomForest│(GradientBoosting)│  (Logistic    │
│             │                  │  Regression)  │
└─────────────┴──────────────────┴───────────────┘
      ↓              ↓                  ↓
         Ensemble Layer (adaptive weights)
                      ↓
              BUY / SELL / HOLD
              + Confidence Score
              + Probability breakdown
```

**30 features used:**
- Price returns (1, 5, 10, 20 bars)
- EMA crossovers (8, 21, 50 periods)
- RSI (7, 14, 21 periods)
- MACD, Stochastic, Williams %R, CCI
- ATR, Bollinger Bands
- Volume analysis (OBV, VWAP)
- Candlestick patterns
- Position in 20-bar range

---

## 📱 Run on Mobile (Android)

**Using Pydroid 3:**
1. Install **Pydroid 3** from Play Store
2. Open Pip → type `nextrade-engine` → Install
3. Create new file, type:

```python
import nextrade
nextrade.train_ml("BTCUSD", "H1")
nextrade.start("adaptive", market="BTCUSD", use_ml=True)
```

4. Tap Run ▶️

**Using Termux:**
```bash
pkg install python
pip install nextrade-engine
python -c "import nextrade; nextrade.start('momentum', market='BTCUSD')"
```

---

## 🗺️ Roadmap

### ✅ Released
- [x] Rule-based signal engine (BUY/SELL/HOLD)
- [x] AI Brain system (IQ, neurons, learning modes)
- [x] Real market data (Forex, Crypto, Stocks, Indices)
- [x] Market Scanner (multi-market at once)
- [x] Backtest engine with grade system
- [x] ML Engine (3 specialist models + ensemble)
- [x] Multi-language support (EN, ID, MY, AR)
- [x] Mobile support (Android via Pydroid/Termux)

### 🔄 In Progress
- [ ] Reinforcement Learning (RL) engine
- [ ] Auto parameter optimization
- [ ] Walk-forward backtesting

### 📋 Planned
- [ ] Telegram bot integration (auto signals)
- [ ] Web dashboard
- [ ] Broker API integration (MT4/MT5, Binance)
- [ ] Portfolio management
- [ ] Risk management module
- [ ] More languages (Chinese, Spanish, French)
- [ ] Windows/Mac desktop app

---

## 🏗️ Project Structure

```
nextrade/
├── nextrade/
│   ├── __init__.py          # Main API & terminal wizard
│   ├── lang.py              # Multi-language system
│   ├── core/
│   │   ├── brain.py         # AI Brain (IQ, neurons, learning)
│   │   └── regime.py        # Market regime detector
│   ├── indicators/
│   │   ├── adaptive.py      # Adaptive RSI, EMA, Momentum
│   │   ├── pattern.py       # Candlestick pattern scorer
│   │   └── confluence.py    # Signal confluence engine
│   ├── ml/
│   │   ├── features.py      # 30-feature engineering layer
│   │   └── model.py         # 3 specialist models + ensemble
│   ├── data/
│   │   └── fetcher.py       # Real market data (yfinance)
│   ├── backtest/
│   │   └── engine.py        # Vectorized backtest engine
│   └── utils/
│       └── terminal_ui.py   # Terminal colors & wizard UI
├── README.md
├── LICENSE
└── pyproject.toml
```

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

## 🌟 Support

If NexTrade helped you, please give it a ⭐ on GitHub!

- 🐛 **Bug reports:** [Open an issue](https://github.com/wafiqrazy035-art/nextrade-engine/issues)
- 💡 **Feature requests:** [Open an issue](https://github.com/wafiqrazy035-art/nextrade-engine/issues)
- 📦 **PyPI:** [nextrade-engine](https://pypi.org/project/nextrade-engine/)

---

<div align="center">
Made with ❤️ for traders everywhere — from desktop to mobile.
</div>

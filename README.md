#  Alpha_Gen — WorldQuant Alpha Generation & Submission Tool

A Python-based toolkit for generating, evaluating, and submitting quantitative trading alphas to the **WorldQuant BRAIN** platform. Built for researchers, quant enthusiasts, and Alphathon participants.

---

## 📌 Overview

Alpha_Gen is a collection of ideas, scripts, and utilities that automate the end-to-end workflow of working with WorldQuant BRAIN — from constructing alpha expressions and simulating backtests to submitting passing alphas to the platform.

> **Alpha**: A portfolio construction algorithm that assigns weights to financial instruments using mathematical expressions over market data fields (price, volume, fundamentals, sentiment, etc.).

---

## ✨ Features

- 🧠 **Alpha Generation** — Construct alpha expressions using WorldQuant's Fast Expression Language operators and data fields
- 📊 **Backtesting & Simulation** — Evaluate alphas via WorldQuant BRAIN's backtesting engine (Sharpe ratio, fitness, turnover, returns)
- ✅ **Alpha Evaluation** — Filter and rank generated alphas based on performance metrics
- 📤 **Automated Submission** — Submit passing alphas to WorldQuant BRAIN programmatically
- 🔄 **Correlation Checking** — Ensure submitted alphas pass WorldQuant's correlation test for diversity

---

## 🗂️ Project Structure

```
Alpha_Gen/
├── alphagenv1/              # Core alpha generation module (v1)
│   ├── *.py                 # Alpha generation, simulation & submission scripts
│   └── *.html / *.sh        # Supporting utilities & shell scripts
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| **Python** | Core language |
| **WorldQuant BRAIN API** | Alpha simulation, evaluation, and submission |
| **HTML** | Supporting UI / result display |
| **Shell / Batch scripts** | Automation and environment setup |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- A WorldQuant BRAIN account
- API credentials (username & password)

### 1. Clone the Repository

```bash
git clone https://github.com/VJ70/Alpha_Gen.git
cd Alpha_Gen
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

> If no `requirements.txt` is present, common dependencies include:
> ```bash
> pip install requests pandas numpy scipy
> ```

### 3. Configure Credentials

Set your WorldQuant BRAIN credentials as environment variables or in a config file:

```bash
export WQ_USERNAME="your_worldquant_username"
export WQ_PASSWORD="your_worldquant_password"
```

### 4. Run the Alpha Generator

```bash
cd alphagenv1
python main.py --username $WQ_USERNAME --password $WQ_PASSWORD
```

---

## 📐 Understanding Alphas

WorldQuant alphas are mathematical expressions over financial data fields. The platform scores each alpha using:

| Metric | Description |
|---|---|
| **Sharpe Ratio** | Risk-adjusted return consistency |
| **Fitness** | `sqrt(abs(Returns) / max(turnover, 0.125)) * Sharpe` |
| **Turnover** | Daily portfolio rebalancing frequency |
| **Returns** | Annualized backtest returns |
| **Correlation** | Must be sufficiently uncorrelated to existing submitted alphas |

Example alpha expression:
```
rank(ts_delta(close, 5)) * (-1)
```

---

## 🔄 Workflow

```
Define Data Fields
      ↓
Construct Alpha Expressions
      ↓
Simulate on WorldQuant BRAIN (5-year backtest)
      ↓
Evaluate Metrics (Sharpe, Fitness, Turnover)
      ↓
Correlation Check vs. Previously Submitted Alphas
      ↓
Submit Passing Alphas (1 per day limit)
```

---

## ⚠️ Important Notes

- **Submission Rate Limit**: WorldQuant enforces a daily submission limit. Avoid bulk-submitting alphas in a single session — submit one per day to comply with platform rules.
- **Correlation Test**: Each new alpha is compared against your previously submitted alphas. It must be sufficiently uncorrelated to pass.
- **Backtest Period**: WorldQuant simulates over a multi-year historical window. Ensure your expressions handle missing data appropriately (e.g., using `ts_backfill`).
- **Credentials Security**: Never hardcode your WorldQuant credentials in source files. Use environment variables or a `.env` file (add it to `.gitignore`).

---

## 💡 Common Alpha Operators

| Operator | Description |
|---|---|
| `rank(x)` | Cross-sectional rank of x |
| `ts_rank(x, d)` | Time-series rank over d days |
| `ts_delta(x, d)` | Change in x over d days |
| `ts_mean(x, d)` | Rolling mean of x over d days |
| `zscore(x)` | Cross-sectional z-score |
| `winsorize(x, p)` | Clip outliers at percentile p |
| `log(x)` | Natural logarithm |
| `correlation(x, y, d)` | Rolling correlation over d days |

---

## 🤝 Contributing

Contributions, alpha ideas, and improvements are welcome!

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-alpha-strategy`
3. Commit your changes: `git commit -m 'Add new alpha generation strategy'`
4. Push to branch: `git push origin feature/new-alpha-strategy`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Vaishnavi** — [VJ70](https://github.com/VJ70)

---

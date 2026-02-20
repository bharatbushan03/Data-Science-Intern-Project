# Trader Performance vs Market Sentiment
### Primetrade.ai Data Science Intern — Round-0 Assignment

**Objective:** Analyze how Bitcoin market sentiment (Fear/Greed) relates to trader behavior and performance on the Hyperliquid exchange.

---

## Project Structure

```
prj/
├── p1.ipynb                  # Part A (Data Prep) + Part B (Analysis)
├── p2.ipynb                  # Part C (Strategies) + Bonus (ML + Clustering)
├── fear_greed_index.csv      # Dataset 1: Bitcoin F&G Index (daily)
├── historical_data.csv       # Dataset 2: Hyperliquid trader history (~211K trades)
└── README.md
```

---

## Setup & How to Run

### Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

### Running the Notebooks

Open in Jupyter or VS Code with Jupyter extension:

1. **Start with `p1.ipynb`** — Data preparation and analysis
2. **Then run `p2.ipynb`** — Strategies and bonus predictive model

Each notebook is **self-contained** (p2.ipynb re-runs the pipeline internally).

---

## Notebooks at a Glance

### `p1.ipynb` — Data Preparation (Part A) + Analysis (Part B)

| Section | What It Does |
|---------|-------------|
| A1–A2 | Load & document both datasets (shape, dtypes, missing values, duplicates) |
| A3 | Parse timestamps, align to daily resolution |
| A4 | Create key metrics: daily PnL, win rate, avg size, long/short ratio, trade count |
| A5 | Merge datasets by date (inner join) |
| B1 | Mann-Whitney U tests + box plots: Fear vs Greed performance comparison |
| B2 | Trader behavior changes across sentiment regimes (violin plots) |
| B3 | Trader segmentation: High/Low Leverage · Frequent/Infrequent · Consistent Winners |
| B4 | 3+ data-backed insights with charts |

### `p2.ipynb` — Actionable Output (Part C) + Bonus

| Section | What It Does |
|---------|-------------|
| Part C | Two strategy rules validated with evidence tables and bar charts |
| Bonus ML | Logistic Regression, Random Forest, Gradient Boosting to predict next-day profitability |
| Bonus Cluster | K-Means (K=4) on lifetime account features → 4 behavioral archetypes |

---

## Key Findings

| # | Insight |
|---|---------|
| 1 | Higher Fear/Greed score correlates positively with total market PnL |
| 2 | Leverage usage spikes during Fear market regimes |
| 3 | High-leverage traders show lower win rates specifically on Fear days |

## Strategy Rules

1. **On Fear days (index < 40):** Reduce leverage to ≤ population median — high-leverage traders consistently underperform during this regime.
2. **Sentiment-gated trade frequency:** Trade frequently on Greed days; use only high-conviction setups on Fear days.

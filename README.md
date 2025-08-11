# Trader Behavior vs Market Sentiment Analysis

## Overview
This project analyzes the relationship between trading behavior — profitability, risk-taking, trading volume, and win rate — and Bitcoin market sentiment (Fear, Neutral, Greed).

By combining **Bitcoin market sentiment data** with **historical trader activity**, we uncover patterns, trends, and potential signals that could help improve trading strategies.

---

## Datasets

### 1. Bitcoin Market Sentiment Dataset
**Columns:**
- `timestamp` — Unix timestamp of the sentiment measurement
- `value` — Numerical sentiment score
- `classification` — Sentiment category (e.g., Fear, Extreme Fear, Neutral, Greed)
- `date` — Date in `YYYY-MM-DD` format

### 2. Historical Trader Data from Hyperliquid
**Columns:**
- `Account` — Trader’s account identifier
- `Coin` — Cryptocurrency traded
- `Execution Price` — Price at trade execution
- `Size Tokens` — Number of tokens traded
- `Size USD` — USD value of the trade
- `Side` — Trade type (BUY or SELL)
- `Timestamp IST` — Trade date/time in IST
- `Start Position` — Starting position before trade
- `Direction` — Trade direction (Buy or Sell)
- `Closed PnL` — Profit/Loss after closing position
- `Transaction Hash` — Transaction ID
- `Order ID` — Trade order identifier
- `Crossed` — Whether the trade crossed the spread (TRUE/FALSE)
- `Fee` — Transaction fee
- `Trade ID` — Unique trade ID
- `Timestamp` — Trade timestamp

---

## Methodology

### 1. Data Preprocessing
- Converted timestamps to UTC datetimes.
- Mapped sentiment classifications to binary and ordinal labels.
- Standardized column names.
- Converted numeric columns (price, size, PnL, fee) to correct data types.

### 2. Daily Aggregations
Calculated daily metrics for trader activity:
- `total_trades` — Number of trades per day
- `total_volume_usd` — Total traded USD volume
- `avg_trade_size_usd` — Mean USD trade size
- `total_pnl` — Sum of profit/loss per day
- `win_rate` — Proportion of profitable trades
- `pct_buy` — Share of buy trades
- `fees_paid` — Total fees paid

### 3. Dataset Merge
- Merged aggregated trader metrics with daily sentiment data based on date.

---

## Exploratory Data Analysis (EDA)
- **Distributions:** Histograms and KDE plots for PnL, volume, win rate, fees, etc.
- **Boxplots:** Comparison of trader metrics by sentiment category.
- **Correlation Heatmap:** Spearman correlation between sentiment scores and trading metrics.
- **Rolling Trends:** 7-day moving averages for PnL and volume.
- **Scatterplots:** Volume vs PnL, colored by sentiment.
- **Category Counts:** Frequency of each sentiment category.
- **Pairplots:** Metric relationships with sentiment coloring.
- **Time Series:** PnL and trade counts over time by sentiment.

---

## Statistical Analysis

### Mann-Whitney U Test
Compared **Fear vs Greed** days for:
- Total PnL
- Volume
- Win Rate
- Trade Size

Identified statistically significant differences in trading behavior across sentiment states.

---

## Outputs
- **Merged Dataset:** `merged_sentiment_trader.csv`
- **EDA Visuals:** All generated PNG charts saved in `/outputs/`
- **Charts ZIP:** All PNG files compressed into a `.zip` file for download

---

## Usage
1. Run the notebook in Google Colab or a local environment.
2. Upload the CSV files into `/content/`.
3. Execute all cells to:
   - Process data
   - Perform EDA
   - Run statistical analysis
   - Export results
4. Download:
   - Merged dataset (`merged_sentiment_trader.csv`)
   - Zipped EDA charts from `/outputs/`

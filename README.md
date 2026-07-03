# Trader Performance vs Market Sentiment Analysis

## Objective
Analyze how Bitcoin market sentiment (Fear/Greed) relates to trader 
behavior and performance on Hyperliquid, and derive actionable 
strategy recommendations.

## Datasets
1. **Bitcoin Fear/Greed Index** — Date, Classification
2. **Hyperliquid Historical Trader Data** — Account, Symbol, Side, 
   Size USD, Closed PnL, execution details, etc.

## Setup
```bash
pip install pandas matplotlib numpy
jupyter notebook
```
Open `Trader_Sentiment_Analysis.ipynb` and run all cells top to bottom.

## Methodology
1. **Data Cleaning** — checked shape, missing values, duplicates in both datasets
2. **Alignment** — converted timestamps to daily granularity, merged trader data with sentiment classification by date
3. **Metrics built** — daily Closed PnL per account, win rate, average Size USD, buy/sell ratio, trade frequency
4. **Segmentation** — consistent winners (avg Closed PnL > 0) vs inconsistent traders (avg Closed PnL ≤ 0); high vs low Size USD traders

## Key Insights
[See below — link to notebook section or paste summary]

## Strategy Recommendations
[Paste your final 3 strategies here]

## Files
- `Trader_Sentiment_Analysis.ipynb` — full analysis
- `/charts` — exported visualizations
- `README.md` — this file
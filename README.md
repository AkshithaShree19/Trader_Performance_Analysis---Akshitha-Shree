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

1. **Greed days deliver the highest average PnL, but with smaller position 
sizes.** Average Closed PnL is highest during Greed (87) and lowest during 
Neutral (22) and Extreme Greed (25), with Fear in between (50). This isn't 
driven by traders sizing up — average trade size during Greed (~3,183) is 
the smallest of all four regimes, suggesting profitability comes from 
better trade selection/timing, not bigger bets.

2. **Fear dominates trading activity, accounting for ~73% of all trades.** 
Of ~184,000 total trades, Fear days alone account for 133,871, far 
exceeding Greed, Neutral, and Extreme Greed combined. Despite this, 
average PnL during Fear (50) remains below Greed (87) — traders are most 
active exactly when average returns are lower, pointing to reactive 
rather than opportunistic trading.

3. **Traders size up during Fear and Extreme Greed, not during Greed or 
Neutral.** Average trade size is highest during Extreme Greed (~5,660) and 
Fear (~5,260), dropping sharply during Greed (~3,183) and Neutral (~3,059). 
Greed also shows a 57.5% sell skew versus a near-balanced ~50/50 split on 
other sentiment days — traders take larger, decisive positions at 
sentiment extremes while trading smaller and more defensively during 
plain Greed.

## Strategy Recommendations

1. **Scale exposure selectively during Greed — gated by trader 
consistency.** Grouping average Closed PnL by account shows a clear split 
between consistent winners (mean Closed PnL > 0) and inconsistent traders 
(mean Closed PnL ≤ 0). Increase exposure during Greed only for accounts 
with a historically positive average Closed PnL; keep inconsistent 
accounts flat regardless of sentiment.

2. **Cut position size during Fear — especially for high Size USD 
traders.** Fear days show more volatile, lower average outcomes, amplified 
for traders with high average Size USD. On Fear days, these traders should 
cut position size by ~30–50% and avoid new entries; traders with smaller 
average Size USD can maintain normal activity.

3. **Treat Greed-day sell-side skew as a crowding signal, not a bullish 
one.** Buy/sell activity is balanced during Fear and Neutral days, but 
Greed shows a clear sell skew (57.5% sell vs. 42.5% buy). Don't treat 
Greed as a default signal to add long exposure — monitor sell-side skew 
as an early warning of profit-taking, and size new entries more 
conservatively when the sell ratio exceeds ~55%.

## Files
- `Track_Sentiment_Analysis.ipynb` — full analysis
- `README.md` — this file

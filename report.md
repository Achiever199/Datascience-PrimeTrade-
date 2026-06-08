# Bitcoin Market Sentiment vs Trader Performance
## Data Science Assignment — Hyperliquid Historical Analysis

**Dataset Period:** May 2023 – May 2025  
**Total Trades Analysed:** 211,218  
**Traders:** 32 unique accounts  
**Assets:** 246 unique coins  
**Total PnL Generated:** $10,254,487

---

## 1. Dataset Overview

| Dataset | Records | Key Columns |
|---|---|---|
| Fear & Greed Index | 2,644 daily rows | date, value (0–100), classification |
| Hyperliquid Trader Data | 211,224 rows | Account, Coin, Side, Size USD, Closed PnL, Timestamp |

Both datasets were merged on date (IST timestamp → UTC date), resulting in **211,218 matched trades** spanning 2 years. Approximately **104,402 trades** were closing trades (Closed PnL ≠ 0) used for win-rate analysis.

---

## 2. Sentiment Distribution of Trades

| Sentiment | Trade Count | % of Total | Trading Days |
|---|---|---|---|
| Fear | 61,837 | 29.3% | 91 |
| Greed | 50,303 | 23.8% | 193 |
| Extreme Greed | 39,992 | 18.9% | 114 |
| Neutral | 37,686 | 17.8% | 67 |
| Extreme Fear | 21,400 | 10.1% | 14 |

**Observation:** Despite having only 14 trading days, Extreme Fear produced 21,400 trades — among the most concentrated activity of any sentiment. This signals panic-driven, high-frequency activity during sharp market dips.

---

## 3. Core Finding: PnL vs Sentiment

| Sentiment | Avg PnL / Trade | Total PnL | Win Rate |
|---|---|---|---|
| Extreme Greed | **$67.89** | $2,715,171 | **89.2%** |
| Fear | $54.29 | $3,357,155 | 87.3% |
| Greed | $42.74 | $2,150,129 | 76.9% |
| Neutral | $34.31 | $1,292,921 | 82.4% |
| Extreme Fear | $34.54 | $739,110 | 76.2% |

### Key Takeaways

**A. Extreme Greed is the most profitable sentiment** — highest avg PnL per trade ($67.89) and highest win rate (89.2%). Traders are riding momentum effectively when the market is euphoric.

**B. Fear outperforms Greed in absolute terms** — The Fear period generated the most total PnL ($3.36M) and the second-highest win rate (87.3%). This is the classic contrarian signal: skilled traders buy fear and profit when markets recover.

**C. Extreme Fear underperforms** — Despite producing high trade counts, average PnL ($34.54) and win rate (76.2%) were the lowest, indicating that extreme volatility makes consistent profitability harder.

**D. Neutral is a "no man's land"** — Lowest total PnL contribution and mid-tier win rate. Directionless markets produce mediocre results.

---

## 4. Trade Behaviour by Sentiment

### BUY vs SELL Ratios

| Sentiment | BUY % | SELL % |
|---|---|---|
| Extreme Fear | **51.1%** | 48.9% |
| Fear | 49.0% | **51.0%** |
| Neutral | 50.3% | 49.7% |
| Greed | 48.9% | **51.1%** |
| Extreme Greed | 44.9% | **55.1%** |

**Insight:** During Extreme Greed, traders are predominantly *selling* (55.1% SELL). This is counter-intuitive at first glance — but it makes sense for sophisticated traders who are taking profits as the market peaks. During Extreme Fear, there is a slight buying bias (51.1% BUY), confirming a buy-the-dip instinct.

### Average Trade Size (USD)

| Sentiment | Avg Trade Size |
|---|---|
| Fear | **$7,816** |
| Extreme Fear | $5,350 |
| Greed | $5,737 |
| Neutral | $4,783 |
| Extreme Greed | **$3,112** |

**Insight:** The largest trades happen during Fear periods ($7,816 avg). This reflects high conviction bets when prices are depressed. Interestingly, Extreme Greed has the *smallest* average trade size ($3,112) — suggesting many small, fast trades during euphoria (scalping momentum).

---

## 5. Top Asset Performance by Sentiment

| Coin | Total PnL | Best Sentiment |
|---|---|---|
| @107 | $2,783,913 | Greed |
| HYPE | $1,948,485 | Extreme Greed |
| SOL | $1,639,556 | Fear |
| ETH | $1,319,979 | Fear |
| BTC | $868,045 | Fear |

**Insight:** SOL, ETH, and BTC generate most of their profits during Fear — classic accumulation assets. HYPE profits most during Extreme Greed, consistent with it being a high-beta speculative token.

---

## 6. Trader Performance Analysis

### Top 5 Traders (Total PnL)

| Rank | Account (prefix) | Total PnL | Trades | Avg PnL/Trade |
|---|---|---|---|---|
| 1 | 0xb1231a4a | $2,143,383 | 14,733 | $145.48 |
| 2 | 0x083384f8 | $1,600,230 | 3,818 | $419.13 |
| 3 | 0xbaaaf657 | $940,164 | 21,192 | $44.36 |
| 4 | 0x513b8629 | $840,423 | 12,236 | $68.68 |
| 5 | 0xbee1707d | $836,081 | 40,184 | $20.81 |

**Trader Archetypes Identified:**

- **0x083384f8 — The Precision Trader:** Only 3,818 trades but the highest avg PnL/trade ($419). Quality over quantity. Best performance in Fear periods.
- **0xbee1707d — The Volume Trader:** 40,184 trades with a smaller avg ($20.81). Scalping strategy, consistent across all sentiments.
- **0xb1231a4a — The Balanced Performer:** High total volume AND high per-trade avg. Best performance during Extreme Greed.

### Best Sentiment per Top Trader

| Trader | Best Sentiment | Worst Sentiment |
|---|---|---|
| 0xb1231a4a | Extreme Greed | Extreme Fear |
| 0x083384f8 | Fear | Extreme Greed |
| 0xbaaaf657 | Fear | Extreme Greed |
| 0x513b8629 | Neutral | Extreme Fear |
| 0xbee1707d | Extreme Greed | Neutral |

**Key Finding:** There is no universal "best" sentiment — top traders have different edges. Some excel in Fear (contrarians), others in Greed (momentum traders). Strategy diversity is a hallmark of the top performers.

---

## 7. Hidden Patterns Discovered

### Pattern 1 — "Sell the Greed" Strategy Works
During Extreme Greed, traders lean 55% SELL. The high win rate (89.2%) validates this: those taking profits near market peaks are overwhelmingly correct. **Strategy: Reduce long exposure and take profits during Extreme Greed signals.**

### Pattern 2 — Fear is Not the Enemy
Both Fear and Extreme Fear produce positive average PnL. The traders in this dataset are actually performing *better* during fear periods than during neutral ones. **Strategy: Don't freeze during fear — the data shows it is a consistent opportunity window for disciplined traders.**

### Pattern 3 — Biggest Bets in Fear
The highest average trade sizes occur during Fear ($7,816). Top traders are sizing up their positions when markets are most fearful. **Strategy: Increase position sizing conviction during Fear periods, not during Greed.**

### Pattern 4 — Extreme Sentiment = Extreme Concentration
Extreme Fear lasted only 14 days but generated 21,400 trades — 1,528 trades/day vs ~261/day during Greed. This signals that extreme volatility triggers frantic trading. However, the lower win rate (76.2%) in Extreme Fear shows this busyness doesn't always translate to better results. **Strategy: During Extreme Fear, slow down and be selective rather than over-trading.**

### Pattern 5 — Trader Style Must Match Sentiment
The heatmap reveals that no single trader dominates across all sentiments. The #1 trader by PnL has their *worst* performance in Extreme Fear, while another top trader performs best exactly there. **Strategy: Traders should identify their sentiment-specific edge and size up only when conditions match their style.**

---

## 8. Strategic Recommendations

| # | Recommendation | Evidence |
|---|---|---|
| 1 | **Use Fear periods to accumulate** | Highest avg trade size + strong win rates in Fear |
| 2 | **Take profits actively during Extreme Greed** | 89.2% win rate, predominantly SELL-biased |
| 3 | **Reduce trade frequency during Extreme Fear** | High trade count but lowest win rate |
| 4 | **Match your strategy to your sentiment edge** | Top traders each have a distinct best-sentiment |
| 5 | **Favour BTC/ETH/SOL in Fear, HYPE/@107 in Greed** | Asset-level PnL breakdown by sentiment |
| 6 | **Avoid over-trading in Neutral markets** | Lowest total PnL contribution despite ~17% of trades |

---

## 9. Limitations & Next Steps

- **Leverage data** was not available in usable form — incorporating leverage ratios would refine risk-adjusted performance metrics.
- **Entry timing within a sentiment day** was not analysed — intra-day patterns could yield additional alpha signals.
- **Causality vs correlation** — sentiment may lag price action; a lead-lag analysis would strengthen the findings.
- **Next step:** Build a real-time sentiment-triggered alert system using the Fear & Greed API to flag optimal entry/exit zones.

---

*Analysis performed using Python (pandas, matplotlib, seaborn) on 211,218 Hyperliquid trades merged with the CNN Bitcoin Fear & Greed Index.*

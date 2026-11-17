# Negative results, and what each one taught

Most ideas fail. Each failure below was tested with a plan written in advance. Each rules out a mechanism, a market or a cost level, which is why it is reported.

## Opening-range breakouts across four futures markets

**Design:**
- An exploration block, then confirmation, validation and sealed blocks.
- A catalogue of six entry families, 81 exits and 28 filters: 307,557 variants.

**Result:**
- The 30-minute breakout showed nothing (−0.005σ, p 0.61).
- The 5-minute breakout earned about one round-trip cost.
- In the full catalogue, the best variants' in-sample Sharpes of 2.8, 1.8 and 1.5 became **−0.35** walk-forward.
- A deflated Sharpe based on the "effective number of trials" passed, which was misleading: that estimate (48 independent trials) is far too small for a search of 300,000 variants.

**Lessons:**
- Measuring breakout outcomes from the stop level overstates continuation (19-40% false alarms in raw t-tests). Measure from the close.
- In a large search, the walk-forward, not a deflated Sharpe, is the honest test.

## Opening-move continuation on Nasdaq-100 futures

**Hypothesis:** sudden opening moves reverse. The data said the opposite on the exploration years (even years): large opening moves, scaled by overnight volatility, continued to midday (t 4.2).

**Result:**
- A frozen rule (follow the move at 09:45, exit at 13:00) had a train Sharpe of 0.99.
- **On the sealed odd years it had a Sharpe of 0.03.** Gross continuation fell 85%; random opens earned the same.
- Filters chosen on the train years scored a probability of backtest overfitting of 0.79: their ranking was noise.

**Lesson:** a relative effect can hold out of sample while its tradable level does not. Test the level, not just the ranking.

## Overnight vs intraday returns of internationally held US stocks

**Hypothesis:** stocks popular with foreign investors earn more overnight, while foreign markets are open.

**Result:**
- Overnight returns concentrate in high-volatility, high-turnover names, but a long-overnight book has a market beta of 1.7 and alpha below its costs after 2009.
- An opening-gap fade passed its training rule (net +10 bp a trade), then **failed a sealed test on 2022-26 IEX minute data** at a 09:35 entry (−9.7 bp a trade, t −2.8).

**Lesson:** a reversal measured from the official opening print is partly bid-ask bounce. Test the entry you could actually get.

## Index overnight drift by volatility regime

**Result:**
- The overnight drift is real (SPY +3.5 bp a night, t 4.7) but does not depend on the volatility regime or the day's move.
- Net of futures costs, every rule lost over 1993-2020.
- The test block was never opened.

## S&P 500 deletions

**Result:**
- On the development years, deleted firms lagged SPY and matched controls by about 15% over a year in event time.
- In calendar time the lag held only against controls (t −2.25), not against SPY: a weak candidate.
- The sealed test of a short-deletions / long-controls book failed with the wrong sign (+4.6% a year against controls, t 0.43).

**Lesson:** event-time drifts that weaken in calendar time are often overlapping-window artefacts.

## Session-seasonality rules that did not survive

Eight of nine session rules failed their sealed odd-year test.
- Four replicated gross but cost about as much as they earned.
- The rest did not replicate.

See the [gold paper](../papers/gold_session_window.md).

## Smaller ideas

- **A 15-minute higher-high / higher-low pattern on NQ:** no edge after costs at any horizon.
- **Cross-sectional month-end ideas (losers, dividend months, pre-turn-of-month losers):** each failed its primary test (see the appendix of the [month-end paper](../papers/month_end_flows.md)).
- **Overnight share of returns (EDA):**
  - a stable stock trait;
  - Bollinger-band touches behave like a random walk;
  - momentum is a tug of war between sessions (overnight +0.25% a month, intraday −0.32%).

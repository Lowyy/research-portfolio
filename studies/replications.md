# Replicating published strategies

Published strategies are a good test of method. The claims are specific, the authors' choices are visible, and what happens after publication is a free out-of-sample period.

## Optimal mean-reversion pairs (Huang & Wang 2016)

The paper fits Ornstein-Uhlenbeck processes to ETF pairs and trades them at thresholds that are optimal under the model.

- **The 2015 numbers reproduce.**
  - With the published hedge ratios, 6 of 9 pairs reach an out-of-sample Sharpe of 1.9 or more in 2015.
  - Fitted parameters match for most pairs, though not all: the hedge ratio within 0.05 for 7 of 9, the OU parameter θ for 4 of 9 (formally below my pre-set replication bar).
- **The edge is the selection, not the model.**
  - Across all 525 pairs of a comparable 2014 universe, out-of-sample Sharpe averages 0.09, and in-sample Sharpe does not predict it (rank correlation about 0).
  - Choosing the estimation window on the test period, as the paper does, lifts the average to 0.75.
- **After publication:**
  - the paper's nine pairs (2015-11 to 2026-04, net, one-day lag) have a Sharpe of −0.13;
  - a yearly walk-forward of the method reaches 0.43 (t 1.39).

## Internal bar strength on SPY (published dip-buying rule)

Buy SPY when it closes near the low of its daily range and below a band; sell on recovery.

- **Real but modest.** 1993-2026: Sharpe 0.77 at the close, 0.63 trading the next open, against 0.51 for buy-and-hold.
  - A random-entry placebo gives p = 0.001.
  - It does not reach the published Sharpe.
- **Since 2010 it lags SPY.** Next-open Sharpe is 0.32 in 2020-26.
- **The same rule on QQQ:** strong before 2010, about equal to buy-and-hold after.

## Linear mean reversion on SPY (published rule)

- **Replicates:** 518 trades and a 73% win rate, as published.
  - On my protocol: Sharpe 0.76 against 0.51 for SPY.
  - A trend-filtered random-entry placebo gives p = 0.008.
- **Caveat:** its parameters are the best of 90 neighbours; the median neighbour has a Sharpe of 0.58. The gain over buy-and-hold is lower drawdown, not higher return.
- **Since publication:** 17 trades, Sharpe 0.86 against SPY's 0.83. Too few to judge.

## What these taught me

1. **Reproduce the number first, then ask where it comes from.** Here it came from selection: of pairs, of windows, of parameters.
2. **After publication, a strategy gets a free test.** Use it.
3. **A placebo** (random entries with the same exposure) separates "the rule works" from "being long SPY works".

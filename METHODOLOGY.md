# How I test ideas (and try not to fool myself)

Every study in this portfolio follows the same protocol. It exists because most backtests are wrong in the same few ways: too many variants tried, data reused, costs ignored, and only the winners reported.

## 1. Write the plan before computing anything

Each step starts with a short `plan.md`, committed to version control before the first number exists. It states:
- **the hypothesis and the mechanism**: who is forced to trade, when, and who absorbs it;
- **the data, the splits, and when each signal is read and traded;**
- **the costs**, fixed in advance:
  - US ETFs: 2-4 bp a trade;
  - CME futures: commission plus one tick of slippage per side;
  - limit orders filled only on a trade-through;
- **the primary test and its pass mark**, with expectations written down so that wrong predictions are visible;
- **the reading rule**: what each outcome would mean, decided before seeing it.

Outcomes are appended with a date. Earlier text is never edited, so the record shows what was believed before the data came in.

## 2. Describe the market before trading it

Exploration (EDA) comes first and stays descriptive: magnitudes, shapes, stability across eras, and placebos where one exists. No cost assumptions and no pass/fail rules at this stage.

## 3. Only out-of-sample results count

- Test data is sealed in advance: later years, alternate years (train on even years, test on odd), or other markets and countries. A test is run **once**.
- A change suggested by a result (a different window, threshold or leg) is a new hypothesis. It needs data not yet used, or it is labelled exploratory.
- Every variant tried is counted and reported. Several tests at once are corrected for multiplicity (Holm).

## 4. Validate the survivors

What passes a sealed test is then examined from the other side:
- **Block-bootstrap intervals** for Sharpe ratio, return and drawdown (stationary bootstrap, Politis & Romano 1994).
- **Probabilistic and deflated Sharpe ratios** (Bailey & López de Prado 2012, 2014), with the number of trials taken from the research record.
- **Probability of backtest overfitting** by combinatorially symmetric cross-validation (Bailey, Borwein, López de Prado & Zhu 2017) on the family of candidates the result could have been selected from.
- **Monte Carlo** of realistic one- and five-year outcomes, including scenarios where the edge halves or disappears.
- **Capacity** from volume and a square-root impact rule.
- **Post-mortems** when live behaviour departs from the backtest.

## 5. Report failures as fully as successes

Most ideas fail. The studies table in the README lists every one with its verdict. A clean negative result is information: it rules out a mechanism, a market or a cost level.

## 6. Portfolio construction without overfitting

Weights are set from risk, not from backtested returns, which are the input that cannot be estimated (Chopra & Ziemba 1993; DeMiguel, Garlappi & Uppal 2009):
- equal risk contribution or fixed weights;
- intermittent trades sized by a tail-loss budget;
- total size set by drawdown tolerance.

A walk-forward comparison of weighting schemes checks that the simple choice is not worse than optimisation.

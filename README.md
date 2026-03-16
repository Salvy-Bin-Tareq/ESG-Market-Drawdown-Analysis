# ESG-Market-Drawdown-Analysis
Quantitative study examining whether ESG ratings predict peak-to-trough stock drawdowns during two market crises: COVID-19 crash (2020) and inflation downturn (2022). Built using Python and SQL on 84 US-listed firms. OLS regression with HC1 robust standard errors. Henley Business School, ICM 406.
# ESG Ratings & Market Drawdown Resilience

**Henley Business School — ICM 406: Programming for Finance**
Awarded Distinction for technical execution

---

## What this project is about

I wanted to test something that gets talked about a lot in sustainable finance but rarely gets stress-tested properly: do firms with stronger ESG profiles actually hold up better when markets fall apart?

To answer that, I looked at two very different crises — the COVID-19 crash in early 2020 (a fast, panic-driven shock) and the inflation-driven downturn in early 2022 (a slow, rate-sensitive squeeze). Same question, two completely different market environments. That contrast turned out to be the most interesting part of the whole project.

---

## What I built

This was a full end-to-end research pipeline, built from scratch.

**Data collection:** Pulled daily adjusted price data for 200 large US-listed firms using yfinance, iterating through a predefined ticker universe and handling failed downloads, missing data, and rate limits. Prices were stored and queried using SQLite — creating structured tables for raw prices, ESG scores, and firm controls, then joining them with SQL before passing to Python for analysis.

**ESG data:** Collected firm-level ESG scores (Total, Environmental, Social, Governance pillars) from a web source and merged them with the price universe at the ticker level. After cleaning and filtering for complete cases, the final regression sample came down to 84 firms.

**Feature engineering:** Calculated peak-to-trough drawdowns for each firm within each crisis window — finding the maximum price decline from local peak to subsequent trough in adjusted prices. Also computed alternative downside risk measures (downside deviation, volatility, 5-day worst-case loss) for robustness checks.

**Control variables:** Pulled market capitalisation and debt-to-equity ratios via yfinance for each firm. Applied log transformation to market cap to reduce skewness before including in regressions.

---

## Methodology

Cross-sectional OLS regressions with HC1 heteroskedasticity-robust standard errors — run separately for COVID-19 and the inflation downturn, then combined into a pooled model with an event dummy and ESG interaction term to test whether the ESG effect changed between crises.

Also ran ESG pillar decompositions (E, S, G separately) to identify which component was actually driving the results, and a rolling cross-sectional regression (60-day window, month-end) to track how the ESG beta evolved over the full 2020–2025 period.

---

## What I found

The honest answer is: it depends on the crisis.

| Event | ESG coefficient | Significance | Direction |
|---|---|---|---|
| COVID-19 crash | β = −0.00071 | p < 0.05 | Higher ESG firms fell harder |
| Inflation downturn | β = +0.00056 | p < 0.10 | Higher ESG firms held up better |

Breaking it down by pillar, the Social score (ESG_S) drove almost all of the COVID result (β = −0.00166, p < 0.01). Environmental and Governance scores added very little once controls were included. During the inflation window, the Governance pillar (ESG_G) reversed direction and became marginally significant — a pattern that points to crisis-specific mechanisms rather than any universal ESG protection channel.

The robustness checks told a similar story — when drawdown was replaced with volatility or worst-case 5-day losses, ESG lost its significance, suggesting the effect is specific to peak-to-trough drawdowns rather than a general risk-reduction story.

The takeaway: ESG is not a universal shock absorber. Whether it helps or hurts depends entirely on the type of crisis — which has real implications for how ESG is used in portfolio risk management and sustainable investing strategy.

---

## Stack
`Python` `SQL (SQLite)` `Pandas` `NumPy` `Matplotlib` `Statsmodels` `yfinance` `OLS Regression` `HC1 Robust Standard Errors`

---

## Author
**Salvy Bin Tareq**
MSc Finance & FinTech — Henley Business School, University of Reading
[LinkedIn](https://www.linkedin.com/in/salvytareq)

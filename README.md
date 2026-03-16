# ESG-Market-Drawdown-Analysis
Quantitative study examining whether ESG ratings predict peak-to-trough stock drawdowns during two market crises: COVID-19 crash (2020) and inflation downturn (2022). Built using Python and SQL on 84 US-listed firms. OLS regression with HC1 robust standard errors. Henley Business School, ICM 406.
# ESG Ratings & Market Drawdown Resilience

**Henley Business School — ICM 406: Programming for Finance**
Awarded Distinction for technical execution

---

## What this project is about

I wanted to test something that gets talked about a lot in sustainable finance but rarely gets stress-tested properly: do firms with stronger ESG profiles actually hold up better when markets fall apart?

To answer that, I looked at two very different crises — the COVID-19 crash in early 2020 (a fast, panic-driven shock) and the inflation-driven downturn in early 2022 (a slow, rate-sensitive squeeze). Same question, two completely different market environments.

## What I built

Built the full pipeline myself in Python and SQL — pulling daily price data for 200 large US-listed firms, cleaning and querying the data, merging in ESG scores at the firm level, and running cross-sectional OLS regressions on a final sample of 84 firms. Controls included firm size (log market cap) and leverage (debt-to-equity ratio).

## What I found

The honest answer is: it depends on the crisis.

| Event | ESG coefficient | Result |
|---|---|---|
| COVID-19 crash | β = −0.00071 (p < 0.05) | Higher ESG firms fell harder |
| Inflation downturn | β = +0.00056 (p < 0.10) | Higher ESG firms held up better |

Breaking it down by pillar, the Social score (ESG_S) drove almost all of the COVID result (β = −0.00166, p < 0.01). Environmental and Governance scores added very little once controls were included.

The takeaway: ESG is not a universal shock absorber. Whether it helps or hurts depends on the type of crisis — which has real implications for how ESG is used in portfolio risk management.

## Stack
`Python` `SQL` `Pandas` `Matplotlib` `OLS` `HC1 Robust Standard Errors`

## Author
**Salvy Bin Tareq**
MSc Finance & FinTech — Henley Business School, University of Reading
[LinkedIn](https://www.linkedin.com/in/salvytareq)

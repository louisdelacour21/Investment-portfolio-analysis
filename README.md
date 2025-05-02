# Investment-portfolio-analysis
# Portfolio Optimization Project

## Introduction

This project presents a quantitatively constructed U.S. equity portfolio, built by selecting 20 stocks from the S\&P 500. The main objective is to maximize **risk-adjusted returns** between **July 1 and December 31, 2024**, using the **Sharpe Ratio** as a core selection metric.

The portfolio uses **equal weights** for initial analysis and employs **advanced techniques** such as **Monte Carlo simulation**, **Fama-French and Fama-MacBeth regressions**, and **bi-weekly rebalancing** to optimize performance and mitigate risk.

---

## Strategy Overview

* **Universe**: S\&P 500 constituents
* **Selection Metric**: Top 20 stocks with highest **absolute Sharpe Ratios**
* **Sharpe Ratio Formula**:

  $$
  \text{Sharpe} = \frac{R_{\text{annual}} - R_f}{\sigma_{\text{annual}}}
  $$

  where $R_f = 4.21\%$ (risk-free rate)
* **Weighting**: Equal weights initially, then optimized via simulation
* **Time Frame**: July 1 to December 31, 2024 (126 trading days)

---

## Performance Metrics

Evaluated across:

* **Total Return**
* **Annualized Volatility**
* **Sharpe Ratio**
* **Alpha** (Jensen’s Alpha relative to benchmark)

---

## Selected Companies

| Ticker | Company                   |
| ------ | ------------------------- |
| PLTR   | Palantir Technologies     |
| UAL    | United Airlines Holdings  |
| GEV    | GE Vernova                |
| AXON   | Axon Enterprise           |
| FOXA   | Fox Corporation           |
| FI     | Fiserv                    |
| KMI    | Kinder Morgan             |
| DASH   | DoorDash                  |
| CBRE   | CBRE Group                |
| NI     | NiSource                  |
| WMT    | Walmart                   |
| TSLA   | Tesla                     |
| BLK    | BlackRock                 |
| ETR    | Entergy                   |
| TPR    | Tapestry                  |
| FFIV   | F5 Networks               |
| EXPE   | Expedia Group             |
| K      | Kellanova                 |
| LYV    | Live Nation Entertainment |
| GILD   | Gilead Sciences           |

---

## Data & Methodology

* **Return Calculation**: Daily returns and annualization
* **Volatility**: Standard deviation of daily returns × √252
* **Sharpe Ranking**: Based on absolute value (long/short neutrality)
* **Portfolio Correlation**: Average = 0.1668 → low correlation
* **Volatility Formula**:

  $$
  \sigma_p = \sqrt{W^T \Sigma W}
  $$

---

## Monte Carlo Simulation for Optimal Weights

* **100,000 portfolios** generated
* Minimum weight per stock: 2.5%
* Best Sharpe Ratio portfolio weights selected
* Example weights (partial):

  ```json
  {
    "PLTR": 0.1209, "K": 0.1868, "AXON": 0.0410,
    "WMT": 0.0253, "TSLA": 0.0295, ...
  }
  ```

---

## Fama-French & Fama-MacBeth Analysis

* **PLTR**, **TSLA**, **GEV**, and **UAL** showed **high alpha and beta** → strong performance and volatility
* **K**, **GILD** → near-zero alpha → behavior driven by risk factors
* **Fama-MacBeth regression**: Intercept-only significance → strong stock-specific returns in short window

---

##  Mean-Variance Optimization (MVO)

* **Unconstrained**: High alpha but large position risk (e.g., K at 22.5%)
* **Constrained** (0.1–7%): More balanced but lower IR
* **Monte Carlo chosen** over MVO due to better diversification and stability

---

## 🔄 Bi-Weekly Resampling (Rebalancing)

* Every 15 days from Jan 1 to Feb 28, 2025
* Rationale:

  * Counteract portfolio drift
  * Maintain optimal risk-return profile
  * Balance transaction costs vs. drift
* Re-optimization performed at each interval based on trailing 15-day returns

---

##  Final Metrics (Jan 1 – Feb 28, 2025)

| Metric                | Value             |
| --------------------- | ----------------- |
| Portfolio Return      | 52.56% (2 months) |
| Annualized Volatility | 23.51%            |
| Sharpe Ratio          | 2.41              |
| Alpha                 | 6.91%             |

>  Context: Exceptional return partly due to increased volatility post-Trump inauguration, enabling high long/short gains.

---

## Conclusion

This project highlights the power of quantitative strategies in portfolio management. By combining **Sharpe-based selection**, **Monte Carlo optimization**, and **rebalancing**, we demonstrate the construction of a high-performance portfolio tuned to short-term market conditions.

---

## Repository Structure

```
├── data/               # Raw and cleaned stock data
├── notebooks/          # Jupyter notebooks for analysis
├── src/                # Python scripts for metrics and simulations
├── results/            # Final weights, returns, plots
├── README.md           # Project overview and documentation
```

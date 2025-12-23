# Monte Carlo GBM Analysis & Statistical Validation

## Overview

This project investigates whether equity prices can be adequately described by a **Geometric Brownian Motion (GBM)**.
Using historical price data, several GBM specifications are simulated and **formally tested against real market data**.

The analysis goes beyond simple visual comparisons and implements **statistical hypothesis tests** to assess whether observed prices behave like a stochastic process or are distinguishable from pure randomness.

---

## Objectives

The main goals of this project are:

* Model asset price dynamics using **Geometric Brownian Motion**
* Compare different GBM calibration methods
* Test whether real market prices are compatible with GBM assumptions
* Determine whether prices behave as a **random stochastic process**

---

## Data

* **Asset**: Apple Inc. (AAPL)
* **Year analyzed**: 2024
* **Source**: Yahoo Finance (`yfinance`)
* **Frequency**: Daily closing prices

---

## Methodology

### 1. Log-Return Analysis

Daily log-returns are computed as:

[r_t = \log\left(\frac{S_t}{S_{t-1}}\right)]

Descriptive statistics are reported:

* Mean
* Volatility
* Skewness
* Excess kurtosis

The empirical distribution of returns is visualized and compared to a Gaussian density.

---

### 2. GBM Simulations

Three GBM specifications are implemented:

#### **GBM – Historical Calibration**

* Drift (μ) and volatility (σ) estimated from the previous year
* Constant parameters over the simulation horizon

#### **GBM – Random Parameters**

* μ and σ drawn randomly from predefined ranges
* Illustrates sensitivity to model assumptions

#### **GBM – Rolling Calibration**

* μ and σ estimated on a rolling window (21 trading days)
* Captures short-term dynamics but may introduce instability

Each model generates multiple Monte Carlo price paths, which are plotted against the historical price.

---

### 3. Statistical Validation Tests

To formally assess model validity, **three statistical tests** are applied to both real and simulated returns:

#### **Jarque–Bera Test**

* Tests normality of log-returns
* GBM assumption: returns should be Gaussian

#### **Ljung–Box Test**

* Tests for autocorrelation (independence)
* GBM assumption: returns are i.i.d.

#### **Likelihood Ratio Test (GBM vs Random Walk)**

* Tests whether the drift component is statistically significant
* Null hypothesis: prices follow a driftless random walk

All tests are performed at the 5% significance level.

---

## Results Summary

The final results are summarized in a comparison table including:

* Normality decision
* Independence decision
* Drift significance

### Key findings:

* **Real market returns strongly reject normality**
* **No significant autocorrelation is detected**
* **The drift component is not statistically significant**
* Prices are statistically indistinguishable from a **random walk with non-Gaussian innovations**

Among simulated models:

* Historical GBM imposes an artificial drift
* Random-parameter GBM most closely resembles real data behavior
* Rolling calibration introduces instability and dependence (overfitting)

---

## Conclusions

This study shows that:

* Equity prices are **stochastic and largely driven by noise**
* The strict assumptions of the GBM (Gaussian returns, constant drift) do **not hold in practice**
* While GBM is useful for simulation and pricing, it should **not be interpreted as a predictive model**
* Market prices are best described as a **random process with non-Gaussian features**

---


## How to Run

1. Install dependencies:

```bash
pip install numpy pandas matplotlib seaborn yfinance scipy statsmodels
```

2. Run the Jupyter notebook:

```bash
jupyter notebook MonteCarlo.ipynb
```

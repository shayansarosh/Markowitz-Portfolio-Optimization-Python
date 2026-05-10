# 📈 Markowitz Portfolio Optimization — Python

A Python-based implementation of **Modern Portfolio Theory (MPT)** using real historical market data, Monte Carlo simulation, and the Efficient Frontier to find the optimal risk-adjusted portfolio.

> Built as part of my MSc in Financial Technology journey into Quant Finance and Risk Analytics.

---

## 🗂️ Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Project Walkthrough](#project-walkthrough)
- [Results](#results)
- [Key Concepts](#key-concepts)
- [How to Run](#how-to-run)

---

## Overview

This project applies **Harry Markowitz's Mean-Variance Optimization** framework to identify the portfolio allocation that maximises the **Sharpe Ratio** — the best possible return for a given level of risk.

Assets used: **PG (Procter & Gamble)** and **^GSPC (S&P 500 Index)**  
Data range: 2010-01-01 to present

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| `Python` | Core language |
| `yfinance` | Historical market data |
| `NumPy` | Matrix operations & simulation |
| `Pandas` | Data manipulation |
| `Matplotlib` | Visualisation |

---

## Project Walkthrough

### 1. 📥 Data Download & Inspection

Downloaded real historical closing prices for PG and ^GSPC using `yfinance`, pulling data from 2010 onwards.

<img width="1030" height="524" alt="image" src="https://github.com/user-attachments/assets/f0d32726-4b35-40bd-91ae-6ae3531c5393" />

---

### 2. 📊 Normalised Price Performance

Normalised both assets to a base of 100 to compare their relative growth over time on the same scale.
<img width="1333" height="651" alt="image" src="https://github.com/user-attachments/assets/638a6f85-bb86-4d83-a951-6b76cf4a8f67" />

---

### 3. 📐 Log Returns, Covariance & Correlation

Calculated **log returns** to capture daily price movements, then built the **annualised covariance matrix** (× 250 trading days) and **correlation matrix** to understand how the two assets move relative to each other.

<img width="883" height="292" alt="image" src="https://github.com/user-attachments/assets/6c193c16-c6c3-45c8-8335-0181c3003ad5" />

> 💡 The correlation of **0.50** between PG and ^GSPC confirms a partial diversification benefit — they don't move in lockstep, which reduces overall portfolio variance.

<img width="739" height="462" alt="image" src="https://github.com/user-attachments/assets/d2de04d2-ceb2-4666-a4e7-ed1e321f5a98" />


### 4. ⚖️ Portfolio Variance & Volatility

Used matrix dot products to compute portfolio variance and volatility for a given weight allocation — the mathematical core of Markowitz's framework.

<img width="1141" height="497" alt="image" src="https://github.com/user-attachments/assets/d59ee389-1780-4f2d-a34e-54e039d87c9b" />

---

### 5. 🎲 Monte Carlo Simulation — 1,000 Portfolios

Generated **1,000 random weight combinations** (summing to 1) and computed the expected return, volatility, and Sharpe ratio for each — effectively sampling the entire risk-return space.

<img width="1381" height="561" alt="image" src="https://github.com/user-attachments/assets/a22be22c-eb28-48f2-b553-30b1034da8f3" />
<img width="1648" height="470" alt="image" src="https://github.com/user-attachments/assets/949a1fb2-d7a7-4c5d-889d-dc394c906142" />


---

### 6. 🏆 Optimal Portfolio — Maximum Sharpe Ratio

Identified the portfolio with the highest Sharpe Ratio across all 1,000 simulations using `argmax()`.

<img width="1108" height="493" alt="image" src="https://github.com/user-attachments/assets/cc6cc552-a978-45d1-af14-e13524acc636" />


---

### 7. 🌐 Efficient Frontier

Plotted all 1,000 simulated portfolios to visualise the **Efficient Frontier**. The ⭐ marks the optimal portfolio — the point where risk-adjusted return is maximised.

<img width="1186" height="637" alt="image" src="https://github.com/user-attachments/assets/81d8a2f0-e55b-4b54-a561-c324143db677" />


---

## Results

| Metric | Value |
|--------|-------|
| ✅ Expected Return | **10.6%** |
| 📉 Volatility / Risk | **15.51%** |
| ⚡ Sharpe Ratio | **0.683** |
| 🏦 PG Weight | **25.6%** |
| 📊 ^GSPC Weight | **74.4%** |

---

## Key Concepts

**Diversification** — Combining assets with a correlation below 1.0 reduces overall portfolio variance. The covariance matrix quantifies this mathematically.

**Risk-Return Tradeoff** — Higher expected returns come with higher volatility. The Efficient Frontier maps every portfolio that maximises return for a given level of risk.

**Sharpe Ratio** — Measures return earned per unit of risk. A higher Sharpe Ratio means better risk-adjusted performance.

**Efficient Frontier** — The upper boundary of all possible portfolios. Any portfolio below the frontier is suboptimal — you're taking on unnecessary risk for the same return.

---




# EUA Futures vs. Spot Basis Analysis (2023-2024)

###  Project Overview
**Quantifying arbitrage opportunities and liquidity premiums in the European Union Emissions Trading System (EU ETS).**

This project performs a statistical analysis of the spread (basis) between **European Union Allowance (EUA) Spot prices** (primary auctions at EEX) and **EUA Futures contracts** (traded on ICE). The goal was to identify structural mispricings that could be exploited by institutional hedgers or high-frequency arbitrage strategies.

---

### The Commercial Context
In the transition to Net Zero, Carbon Allowances have become a volatile asset class.
* **The Problem:** Theoretically, the Futures price should equal the Spot price. However, liquidity fragmentation between EEX and ICE often creates temporary inefficiencies.
* **The Opportunity:** By analyzing the Basis (Futures - Spot), we can detect when the market is overpaying for liquidity or hedging, offering a signal for statistical arbitrage.

---

###  Technical Implementation
**Tech Stack:** Python, Pandas, NumPy, Matplotlib, Statsmodels

The analysis pipeline was built to handle financial time-series data with the following key modules:
1.  **Data Ingestion & Cleaning:**
    * Aligned disparate timestamps between EEX (Auction data) and ICE (Continuous trading).
    * Handled missing data points during non-overlapping trading holidays.
2.  **Statistical Tests:**
    * Calculated the rolling correlation between Spot and Futures.
    * Performed **Stationarity tests (ADF Test)** on the Basis to confirm mean-reverting properties.
3.  **Visualization:**
    * Plotted the "Basis Structure" over time to visualize contango/backwardation shifts during the 2023 energy crisis aftershocks.

---

###  Challenges & Solutions (Self-Reflection)
* **Data Granularity:** The EEX auctions happen once daily, while ICE futures trade continuously.
    * *Solution:* I resampled the futures data to match the specific auction windows to ensure a fair price comparison, avoiding look-ahead bias.
* **Stationarity:** Initial tests showed the prices themselves were non-stationary (random walk).
    * *Solution:* I shifted the focus to the spread (difference), which proved to be stationary, validating the use of mean-reversion statistical models.

---

###  Contact
* **Author:** Marvin Kinuthia Mwenyura
* **Role:** MSc FinTech Candidate, University of Essex
* **Focus:** Quantitative Finance, Algorithmic Trading, DeFi

### Here is a 'live' version of the project:
https://kinuthia39.github.io/EUA-Futures-Basis-Arbitrage/  

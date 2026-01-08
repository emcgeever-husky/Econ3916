# Global Purchasing Power Parity Analysis via the Big Mac Index

## 📊 Project Overview

**Objective:** This project empirically tests the **Law of One Price** using The Economist's Big Mac Index as a proxy for evaluating global purchasing power parity (PPP) and identifying currency misalignments relative to the US Dollar.

## 🎯 Methodology

- **Data Construction**: Manually constructed a structured dataset from The Economist's 2015 Big Mac Index data using Python dictionaries, capturing local Big Mac prices and nominal exchange rates across multiple countries
- **PPP Calculation**: Computed the **implied PPP exchange rate** for each currency by comparing local Big Mac prices to the US benchmark price
- **Valuation Analysis**: Calculated the percentage over/undervaluation of each currency against the USD by comparing implied PPP rates to actual market exchange rates
- **Economic Interpretation**: Assessed whether currencies exhibited arbitrage opportunities based on deviation from purchasing power parity

## 💡 Economic Rationale

The **Law of One Price** posits that identical goods should cost the same across countries when expressed in a common currency, absent transaction costs and trade barriers. The Big Mac Index exploits this principle by using a globally standardized product (McDonald's Big Mac) as a benchmark for cross-country price comparisons. Deviations from parity suggest either:
- **Currency overvaluation** (local prices exceed PPP predictions)
- **Currency undervaluation** (local prices fall below PPP predictions)

This "Burgernomics" approach offers an intuitive, real-world application of purchasing power parity theory.

## 🔍 Key Findings

The analysis revealed significant currency misalignments across the 19-country sample:

**Most Overvalued Currency:**
- The **Norwegian Krone (NOK)** was overvalued by approximately **31.5%**, suggesting Big Macs were relatively expensive in Norway compared to the US

**Significantly Undervalued Currencies:**
- The **Russian Ruble (RUB)** exhibited the greatest undervaluation at **-71.6%**, indicating substantial purchasing power advantages
- **South African Rand (ZAR)**: -53.7% undervalued
- **Indonesian Rupiah (IDR)**: -53.2% undervalued
- **Egyptian Pound (EGP)**: -52.0% undervalued
- **Hong Kong Dollar (HKD)**: -49.3% undervalued
- **Chinese Yuan (CNY)**: -42.2% undervalued

**Currencies Closely Aligned with PPP:**
- **United States Dollar (USD)**: Baseline (0% by definition)
- **British Pound (GBP)**: -8.6% (relatively close to parity)
- **Euro (EUR)**: -10.7% (within reasonable deviation)
- **Australian Dollar (AUD)**: -10.0% (near equilibrium)

These findings highlight the presence of **cross-border arbitrage opportunities** and demonstrate how transportation costs, local market conditions, trade barriers, and currency dynamics create persistent deviations from theoretical parity. The substantial undervaluation in emerging markets (Russia, South Africa, Indonesia, China) suggests lower relative price levels, while Norway's overvaluation reflects its high-cost economy.

## 🛠️ Technical Implementation

- **Language**: Python
- **Libraries**: Pandas for data manipulation and exchange rate calculations
- **Approach**: Manual data ingestion to build foundational data wrangling skills
- **Visualization**: Seaborn horizontal bar chart displaying currency valuations

---

*This lab demonstrates the application of economic theory to real-world data, bridging conceptual understanding of PPP with hands-on quantitative analysis.*ta, bridging conceptual understanding of PPP with hands-on quantitative analysis.*

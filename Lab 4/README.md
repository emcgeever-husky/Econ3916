# LAB 4 — Descriptive Statistics & Anomaly Detection

## Comparative Forensics Report: Core Market vs. The Tail

---

## Context & Purpose

This README documents the analytical workflow implemented in **LAB_4_Descriptive_Statistics_&_Anomaly_Detection.ipynb**. The lab focuses on using **descriptive statistics and anomaly detection** to understand how extreme observations (outliers) reshape distributions, distort averages, and signal structural inequality in socioeconomic data.

Rather than treating anomalies as noise, this analysis treats them as **forensic evidence** — revealing tail risk, concentration effects, and Pareto-style dynamics that standard summary statistics often conceal.

---

## Dataset & Variables

The notebook operates on a Pandas DataFrame `df` containing at minimum:

* `outlier_iso` — Boolean indicator produced by an isolation-based anomaly detection method

  * `False` → Normal (core market)
  * `True` → Outlier (tail observations)
* `MedInc` — Median household income
* `MedHouseVal` — Median house value

These variables allow direct comparison between the economic “center of mass” and the statistical tail.

---

## Step 1: Data Segmentation

The first operation splits the dataset into two conditional populations:

* **df_normal** — All observations classified as non-outliers
* **df_outlier** — All observations flagged as anomalous

This separation is foundational. Every statistic computed downstream is conditional on group membership, ensuring that tail behavior does not contaminate core-market estimates.

---

## Step 2: Central Tendency (Mean vs. Median)

For both groups, the notebook computes:

* Mean and Median of `MedInc`
* Mean and Median of `MedHouseVal`

### Why both?

* **Mean** captures aggregate magnitude but is highly sensitive to extremes
* **Median** captures the typical observation and is robust to outliers

A divergence between these two values is the first quantitative signal of skewness, concentration, and inequality.

---

## Step 3: Volatility & Dispersion (STD vs. MAD)

To diagnose instability and tail influence, two dispersion metrics are compared:

* **Standard Deviation (STD)** — Sensitive to extreme values
* **Median Absolute Deviation (MAD)** — Robust, median-centered volatility

MAD is calculated as:

```
MAD = median(|x − median(x)|)
```

### Interpretation Logic

* STD ≫ MAD → volatility is driven by a small number of extreme observations
* STD ≈ MAD → dispersion is broadly distributed across the population

This comparison is central to anomaly detection and forensic robustness.

---

## Step 4: Inequality Wedge (Outliers Only)

For the outlier group, the analysis computes an **Inequality Wedge**:

```
Inequality Wedge = Mean − Median
```

This is calculated separately for:

* Median Income (`MedInc`)
* Median House Value (`MedHouseVal`)

### Why isolate outliers?

Outliers define the tail of the distribution. A large positive wedge indicates:

* Right-skewed distributions
* Wealth/value concentration
* Pareto-style dynamics where averages misrepresent lived reality

This table functions as the **forensic core output** of the lab.

---

## Step 5: Visualization — The Pareto World

The notebook concludes with a diagnostic visualization:

### Structure

* **1×2 subplot layout**

**Left Panel — Core Market**

* Histogram of `MedInc` for normal observations
* Represents the bulk of the population

**Right Panel — The Tail**

* Histogram of `MedInc` for outlier observations
* Reveals sparsity, skewness, and extreme values

### Global Title

> **“The Pareto World: Core Market vs. The Tail”**

This visual separation provides immediate intuition for why tail-aware statistics matter.

---

## Key Analytical Takeaways

* Outliers substantially inflate means and standard deviations
* Median-based statistics remain stable and interpretable
* Inequality wedges quantify distortion caused by tail observations
* Visual diagnostics confirm heavy-tailed structure

Together, these results demonstrate why **robust statistics are essential** in economic and housing market analysis.

---

## Methodological Framing

This lab aligns with best practices in:

* Exploratory Data Analysis (EDA)
* Anomaly detection and isolation methods
* Robust statistics
* Distributional forensics

The approach generalizes to finance, labor economics, housing markets, and any domain where **tails matter more than averages**.

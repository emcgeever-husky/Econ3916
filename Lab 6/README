# Lab 5: The Architecture of Bias

## Overview
This lab investigates how **bias enters machine learning systems before any model is trained**, focusing on the **Data Generating Process (DGP)** and sampling mechanisms. The project demonstrates how flawed data collection, allocation, and filtering decisions can invalidate downstream statistical inference and model performance.

Rather than treating bias as a modeling issue, this lab frames it as an **engineering and data integrity problem**.

---

## Objectives
- Analyze how different sampling strategies affect variance, representativeness, and inference
- Demonstrate how improper randomization leads to misleading conclusions
- Perform forensic checks to detect hidden data integrity failures in experiments

---

## Tech Stack
- **Python**
- **pandas, numpy**
- **scipy.stats** (Chi-Square tests)
- **scikit-learn** (sampling utilities)

---

## Methodology

### 1. Simple Random Sampling (SRS)
Manually simulated Simple Random Sampling on the Titanic dataset to illustrate how:
- Small or naive random samples can introduce **high variance**
- Class proportions fluctuate due to **sampling error**
- “Random” does not guarantee “representative,” especially under limited sample sizes

This step highlighted how instability in the sample itself can distort conclusions before modeling begins.

---

### 2. Stratified Sampling
Implemented **Stratified Sampling** using `sklearn` to control for key covariates (e.g., class labels).

Results:
- Preserved class distributions across samples
- Eliminated **covariate shift** introduced by SRS
- Reduced variance and improved statistical reliability

This demonstrated how sampling design can directly correct bias without changing the model.

---

### 3. Sample Ratio Mismatch (SRM) Forensic Audit
Conducted an **SRM audit** using Chi-Square tests to verify experimental integrity in A/B testing scenarios.

- Compared observed vs. expected group allocations
- Used Chi-Square statistics to detect deviations from planned randomization
- Flagged statistically significant mismatches as **engineering failures**, not randomness

This step reframed A/B testing as a **systems reliability problem**, where broken assignment logic invalidates causal claims.

---

## Key Takeaways
- Bias often originates in **data collection and allocation**, not algorithms
- Randomization must be **validated**, not assumed
- Statistical tests can be used as **forensic tools** to detect silent failures
- Sampling strategy is a first-class design decision in ML systems

---

## Theory: Survivorship Bias & Ghost Data

### Why analyzing only successful Unicorn startups leads to Survivorship Bias
Analyzing only Unicorn startups featured on platforms like TechCrunch introduces **Survivorship Bias** because the dataset is conditioned on success.

What’s missing:
- Startups that failed
- Startups that never received media attention
- Startups that exited quietly or shut down early

By observing only companies that *survived and succeeded*, we systematically overestimate:
- The effectiveness of certain strategies
- The probability of success
- The causal impact of visible traits (e.g., funding rounds, founders, geography)

This leads to false conclusions such as:
> “These traits cause success”

when, in reality, they may simply correlate with **being observed**.

---

### What Ghost Data is needed to fix this (Heckman Correction)
To correct for this bias using a **Heckman Selection Model**, we need **selection ghost data** — information about the **unobserved or excluded cases**.

Specifically:
- Data on **failed startups**
- Startups that never reached public visibility
- Variables that affect *selection into the observed dataset* (e.g., likelihood of media coverage, investor access)

This ghost data is used in the **selection equation** to model:
> *“What determines whether a startup appears in TechCrunch at all?”*

By explicitly modeling the selection mechanism, the Heckman Correction separates:
- The process of **being observed**
- From the process of **outcome generation (success)**

Without this ghost data, estimates are biased because the dataset is **non-randomly truncated**.

---

## Conclusion
This lab demonstrates that bias is often **architectural**, not accidental.  
Understanding and correcting for bias requires:
- Examining how data is generated
- Validating randomness
- Accounting for missing and unobserved populations

In short: **no amount of model tuning can fix broken data assumptions.**

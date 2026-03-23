# AI Capex Diagnostic Modeling

**Objective:** Identified and corrected structural failures in an OLS regression framework predicting AI software revenue from NVIDIA's 2026 capital expenditure and deployment data, applying heteroscedasticity-robust estimation to restore valid inference.

## Methodology

- Specified a baseline OLS model regressing AI software revenue on hardware capex, data center power consumption, and cloud GPU deployments using `statsmodels`
- Conducted visual residual forensics (residuals vs. fitted plots) to detect variance patterns inconsistent with homoscedasticity assumptions
- Formalized the diagnosis with a White Test, confirming statistically significant heteroscedasticity concentrated at high capex tiers
- Computed Variance Inflation Factors (VIF) across all regressors to screen for multicollinearity in the design matrix
- Re-estimated the model using HC3 heteroscedasticity-consistent standard errors to produce asymptotically valid coefficient inference

## Key Findings

The naive OLS model produced artificially narrow standard errors at high capital expenditure levels, inflating t-statistics and generating false confidence in the significance of deployment regressors. White Test results rejected homoscedasticity at conventional significance thresholds. HC3 correction appropriately widened standard errors, revealing that statistical significance for cloud GPU deployment metrics was overstated in the uncorrected specification — a consequential distinction for any policy or investment inference drawn from the model.

## Stack

Python · pandas · statsmodels · matplotlib · seaborn

## NY Fed Yield Curve Recession Model Replication

**Objective:** Replicated the Federal Reserve Bank of New York's yield curve recession forecasting model by fitting a logistic regression on FRED macroeconomic data to predict NBER-dated recessions 12 months ahead.

**Methodology:**
- Retrieved the 10-Year minus 3-Month Treasury yield spread (T10Y3M) and NBER recession indicator (USREC) from the FRED API; resampled the daily spread to monthly frequency and applied a 12-month forward lag to align predictors with recession outcomes
- Benchmarked a Linear Probability Model (OLS) against logistic regression to expose the structural failure of LPM on binary outcomes — out-of-bounds predicted probabilities below 0 and above 1 on real data
- Fitted a logistic regression via scikit-learn and re-estimated with statsmodels `Logit` to obtain heteroskedasticity-robust standard errors and 95% confidence intervals on the odds ratio
- Generated a monthly recession probability time series analogous to the NY Fed's published output; validated model performance using `TimeSeriesSplit` cross-validation to prevent look-ahead bias

**Key Findings:**
The LPM produced logically incoherent predicted probabilities on historical FRED data, confirming that logistic regression is the correct specification for binary economic outcomes. The fitted logistic S-curve captured the nonlinear relationship between the yield spread and recession risk. The extracted odds ratio with 95% CI quantified the marginal effect of spread inversion in probability terms. The reconstructed time series closely tracked the NY Fed's published forecasts, including the contested 2022–2024 inversion episode — a period in which the model signaled persistently elevated recession risk that ultimately did not materialize as an NBER-dated recession, illustrating the model's known limitations under structural shifts in the term premium.

**Stack:** Python · pandas · NumPy · scikit-learn · statsmodels · fredapi · matplotlib

# Causal ML — Double Machine Learning for 401(k) Policy Evaluation

## Objective
Apply Double Machine Learning to estimate the causal effect of 401(k) eligibility on net financial assets, correcting for selection bias introduced by income and demographic confounders.

## Methodology
- Demonstrated regularization bias: naive LASSO applied to a simulated DGP (TRUE ATE = 5.0) shrank the treatment coefficient as collateral damage from uniform penalization
- Constructed a DoubleMLData object separating outcome (`net_tfa`), treatment (`e401`), and 12 demographic/financial covariates
- Fit a Partially Linear Regression (PLR) model using Random Forest nuisance learners for both the outcome and propensity models with 5-fold cross-fitting
- Estimated the Average Treatment Effect (ATE) of 401(k) eligibility on net financial assets across 9,915 observations
- Conducted CATE analysis by income quartile to test for treatment effect heterogeneity
- Visualized subgroup ATEs with 95% confidence intervals

## Key Findings
- The overall ATE of 401(k) eligibility on net financial assets was -$867 (95% CI: [-$1,810, $76], p=0.072), statistically insignificant at the 5% level — suggesting eligibility alone does not reliably drive asset accumulation once confounders are controlled
- CATE estimates across all four income quartiles also failed to reach statistical significance, with confidence intervals crossing zero in every subgroup
- The null result highlights the importance of causal inference methods: naive comparisons overstate the 401(k) effect due to selection bias, while DML reveals a much weaker relationship after controlling for income and demographics

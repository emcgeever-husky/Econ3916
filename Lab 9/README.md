# Recovering Experimental Truths via Propensity Score Matching

## Objective
Correct for systematic selection bias in non-experimental data by applying Propensity Score Matching (PSM) to recover a treatment effect estimate consistent with randomized experimental benchmarks.

## Methodology
- **Selection bias modeling:** Characterized and quantified the structural differences between treated and control units in the observational Lalonde dataset, establishing that naive comparisons yield severely distorted estimates.
- **Propensity score estimation:** Fit a logistic regression model to estimate each unit's conditional probability of treatment assignment given pre-treatment covariates, producing calibrated propensity scores for all observations.
- **Nearest-neighbor matching:** Matched each treated unit to its closest control counterpart in propensity score space, constructing a balanced quasi-experimental comparison group that mimics the covariate distribution of a randomized trial.

## Key Findings
The unmatched, naive ATT estimate produced a treatment effect of **−$15,204** — a figure directionally wrong and economically implausible, driven entirely by pre-treatment differences between groups. Following PSM, the matched estimate recovered a treatment effect of approximately **+$1,800**, closely aligning with the known experimental benchmark from the Lalonde (1986) randomized study. This represents a correction of over $17,000 in estimated effect magnitude, demonstrating that selection bias, left unaddressed, can not only attenuate but fully invert causal conclusions.

## Stack
Python · Pandas · Scikit-Learn

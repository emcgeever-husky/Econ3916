# Hypothesis Testing & Causal Evidence Architecture

## The Epistemology of Falsification: Hypothesis Testing on the LaLonde Dataset

---

## Objective

Most applied work stops at estimation — fitting a model, reading a coefficient, moving on. This project takes a different stance: shifting the epistemological burden from *"what is the effect?"* to *"can we falsify the claim that there is no effect?"*

Using the LaLonde (1986) dataset, this analysis operationalizes the scientific method to adjudicate between competing causal narratives. Rather than treating a difference in means as self-evident, every estimated effect is subjected to formal falsification — stress-tested against distributional assumptions before any conclusion is drawn.

---

## Technical Approach

- **Parametric Testing — Welch's T-Test (SciPy):** Estimated the Average Treatment Effect (ATE) in real 1978 earnings between treatment and control groups. The signal-to-noise ratio (T-statistic) was computed using Welch's formulation rather than Student's T, correcting for unequal group variances — a common and consequential violation in observational wage data.

- **Non-Parametric Validation — Permutation Test, 10,000 resamples (SciPy):** Earnings distributions are characteristically right-skewed and non-normal. A permutation test was run to empirically construct the null distribution without relying on parametric assumptions, providing a model-free cross-check on the T-test result.

- **Type I Error Control:** A significance threshold of α = 0.05 was pre-specified before any testing was conducted. Both methods were held to this threshold rather than retrofitted to results — the distinction between confirmatory inference and p-hacking.

**Key Results:**

| Metric | Value |
|---|---|
| Treatment Effect (ATE) | -$635.03 |
| T-Statistic | -0.9377 |
| T-Test P-Value | 0.3491 |
| Permutation P-Value | 0.3370 |
| Decision (α = 0.05) | Fail to Reject Null Hypothesis |

Both methods converge on the same conclusion: the observed earnings differential between treated and control groups is not statistically significant. The tight agreement between parametric and non-parametric p-values (0.3491 vs. 0.3370) confirms the result is stable across methodological assumptions.

---

## Business Insight: Hypothesis Testing as the Safety Valve of the Algorithmic Economy

At scale, the danger isn't that models are wrong — it's that they're *convincingly wrong*. With enough features, enough slices of the data, and enough compute, a sufficiently motivated analyst can surface a statistically impressive result for almost any hypothesis. This is data dredging, and in production environments it's endemic.

Rigorous hypothesis testing is the institutional check against this failure mode. Pre-registered thresholds, distributional validation, and non-parametric cross-checks enforce a hard separation between exploration and confirmation. This project illustrates the point directly: a raw comparison of group means might invite a narrative, but putting that narrative through formal falsification changes the conclusion entirely.

A non-finding reported honestly is more defensible — and more valuable — than a spurious positive. In environments where model outputs inform hiring, credit, or resource allocation decisions, that distinction isn't academic. It's an operational and regulatory liability. Falsification-first methodology is how you build systems that hold up under scrutiny.

---

## Stack

`Python` · `SciPy` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn`

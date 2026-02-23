# Hypothesis Testing & Causal Evidence Architecture

## The Epistemology of Falsification: Hypothesis Testing on the LaLonde Dataset

---

## Objective

Most applied work stops at estimation — fitting a model, reading a coefficient, moving on. This project takes a different stance: shifting the epistemological burden from *"what is the effect?"* to *"can we falsify the claim that there is no effect?"*

Using the LaLonde (1986) dataset — a canonical benchmark in causal inference built from a randomized job training intervention — this analysis operationalizes the scientific method to adjudicate between competing causal narratives. The goal is not merely to produce an estimate of the Average Treatment Effect (ATE), but to stress-test that estimate against distributional assumptions and establish evidentiary rigor.

---

## Technical Approach

- **Parametric Testing (Welch's T-Test via SciPy):** Computed the ATE in real earnings between treatment and control groups. Welch's formulation was chosen over Student's T to account for unequal variances across groups — a common and consequential violation in observational economic data.

- **Non-Parametric Validation (Permutation Test, 10,000 resamples via SciPy):** To guard against conclusions inflated by distributional assumptions — earnings data is characteristically right-skewed and non-normal — a permutation test was run to empirically construct the null distribution. This provides a model-free confirmation of the parametric result.

- **Type I Error Discipline:** A pre-specified significance threshold (α = 0.05) was set prior to testing. Both methods were evaluated against this threshold, not retrofitted to it — a meaningful distinction that separates rigorous inference from p-hacking.

**Key Result:** Both methods converge on a statistically significant lift in real earnings of approximately **$1,795**, rejecting the null hypothesis of zero treatment effect.

---

## Business Insight: Hypothesis Testing as the Safety Valve of the Algorithmic Economy

At scale, the danger isn't that models are wrong — it's that they're *convincingly wrong*. With enough features, enough cuts of the data, and enough computational horsepower, a sufficiently motivated analyst can surface a statistically impressive result for almost any hypothesis. This is data dredging, and it's endemic.

Rigorous hypothesis testing — with pre-registered thresholds, distributional validation, and non-parametric cross-checks — is the institutional check against this failure mode. It enforces a separation between exploration and confirmation, and it's what makes the difference between a model that *fits the past* and one that *generalizes to the future*.

In production environments, where model outputs drive hiring decisions, credit allocations, or resource interventions, a spurious correlation isn't just an academic error. It's an operational liability. Falsification-first methodology is how you build systems that hold up under scrutiny — from regulators, from stakeholders, and from reality.

---

## Stack

`Python` · `SciPy` · `Pandas` · `NumPy`

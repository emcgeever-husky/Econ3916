# Audit 02: Deconstructing Statistical Lies

A hands-on audit of how standard statistical tools can mislead — and how to catch it.

---

## 1. Latency Skew — Robust Statistics

Simulated 1,000 server latency logs: 980 normal requests (20–50ms) and 20 traffic spikes (1,000–5,000ms).

| Metric | Value |
|--------|-------|
| Mean | ~128ms |
| Median | ~34ms |
| SD | ~489ms |
| MAD | ~7ms |

The mean and SD are pulled hard by the 20 spikes. The median and MAD barely move. When your data has outliers, SD doesn't measure spread — it measures how badly you're being fooled.

---

## 2. False Positives — The Base Rate Problem

Tested a plagiarism detector claiming 98% accuracy (sensitivity = specificity = 98%) across three environments.

| Scenario | Base Rate | P(Cheater \| Flagged) |
|----------|-----------|----------------------|
| Bootcamp | 50% | 98.0% |
| Econ Class | 5% | 72.1% |
| Honors Seminar | 0.1% | 4.7% |

In the Honors Seminar, a flagged student has only a 4.7% chance of actually cheating. The detector is technically accurate — it's just mostly finding innocent people because cheating is so rare. Accuracy without base rate context is meaningless.

---

## 3. Survivorship Bias — Crypto Token Launches

Simulated 10,000 token launches using a Pareto distribution (power law), mirroring real platforms like Pump.fun where 98%+ of tokens fail.

| Group | Mean Market Cap |
|-------|----------------|
| All 10,000 tokens | ~$2,741 |
| Top 1% survivors | ~$44,634 |

The survivor mean is **16x higher** than reality. Anyone studying only successful tokens is studying a fantasy. The graveyard is the data.

---

## Key Takeaway

Standard metrics (mean, SD, accuracy) are not lies by themselves — but they become lies when applied without context. Ask what's being excluded before trusting any summary statistic.

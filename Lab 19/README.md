# Tree-Based Models — Random Forests

**Course:** ECON 3916: Data Science for Economists
**Dataset:** California Housing (sklearn) — 20,640 observations, 8 features

---

## Objective

Evaluate the predictive performance of ensemble tree-based methods against linear and single-tree baselines on a canonical housing dataset, with emphasis on hyperparameter sensitivity and feature attribution.

---

## Methodology

- Benchmarked three model classes — Decision Tree, Ridge Regression, and Random Forest — on the California Housing dataset using RMSE and R² across train/test splits
- Tuned Random Forest hyperparameters (`n_estimators`, `max_depth`, `max_features`) via 5-fold GridSearchCV, evaluating 27 parameter combinations scored on negative MSE
- Extracted and compared two feature importance methods: MDI (mean decrease in impurity, training-based) and permutation importance (test-based), analyzing where and why they diverge
- Framed a binary classification task — predicting above-median home prices — and benchmarked a Random Forest classifier against Logistic Regression using ROC-AUC
- Built an interactive three-panel Plotly dashboard with ipywidgets sliders for `n_estimators` and `max_features`, visualizing model comparison, MDI importance, and train/test learning curves in real time

---

## Key Findings

- Random Forest (Test R² = **[YOUR VALUE]**) substantially outperformed Ridge Regression (Test R² = **[YOUR VALUE]**), indicating meaningful non-linearity in the feature-price relationship that a linear model cannot capture
- `MedInc` ranked as the dominant predictor under both importance methods; geographic coordinates (`Latitude`, `Longitude`) were inflated by MDI relative to permutation importance, consistent with high-cardinality bias in impurity-based metrics
- The RF classifier achieved materially higher AUC than Logistic Regression, reinforcing that the expensive/cheap decision boundary is non-linear in feature space
- Hyperparameter tuning via GridSearchCV produced modest gains over default settings, suggesting RF is robust to initialization but sensitive to `max_depth` constraints

---

## Tools & Libraries

`scikit-learn` · `plotly` · `ipywidgets` · `numpy` · `pandas`

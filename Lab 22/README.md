# Clustering World Economies with K-Means & PCA

**Objective:** Applied unsupervised machine learning to classify ~160 economies across 10 World Bank development indicators, evaluating how algorithmically derived clusters compare to official income group classifications.

**Methodology:**
- Pulled 10 WDI indicators (GDP per capita, life expectancy, infant mortality, etc.) via `wbgapi`
- Standardized all features with `StandardScaler` to ensure equal contribution to Euclidean distance
- Fit K-Means (K=4) and projected results to 2D using PCA for visualization
- Evaluated K=2 through K=10 using the elbow method (WCSS) and silhouette analysis
- Cross-tabulated algorithmic clusters against World Bank income group labels to assess alignment

**Key Findings:** K=4 was the optimal cluster count, confirmed by both diagnostics and consistent with the World Bank's four income tiers. Clusters separated cleanly at the extremes — high-income countries averaged $91K GDP/capita and 3.3 infant deaths per 1,000 versus $8K and 40.3 in the lowest cluster — but middle-tier countries overlapped, reflecting that GNI per capita alone does not fully capture multidimensional development. The same pipeline applied to California Housing census tracts identified four economically meaningful tract types, including a small outlier group of institutional housing with anomalous occupancy figures.

# FedSpeak Analysis — NLP on FOMC Minutes

## Objective
Quantify shifts in Federal Reserve communication style and sentiment across 240 FOMC meeting minutes (2000–2026) using natural language processing techniques.

## Methodology
- Loaded FOMC meeting minutes via HuggingFace (`vtasca/fomc-statements-minutes`)
- Preprocessed text through lowercasing, tokenization, stop word removal, and lemmatization
- Built a TF-IDF document-term matrix (5,000 features, unigrams + bigrams) with frequency thresholds to filter noise
- Scored each document using the Loughran-McDonald financial sentiment dictionary (net sentiment + uncertainty)
- Visualized sentiment time series with rolling averages and annotated key macro events (Lehman, Taper Tantrum, COVID, 2022 tightening)
- Reduced TF-IDF to 50 dimensions via TruncatedSVD, then clustered documents with K-Means (K=3)
- Compared pre- vs post-COVID sentiment distributions using overlaid histograms

## Key Findings
- K-Means clustering identified a clear structural break around the 2008 financial crisis: a pre-GFC language regime (2000–2008) and a distinct post-GFC regime (2008–present), with a smaller cluster capturing outlier meetings across both eras
- Post-COVID FOMC minutes show a meaningful decline in net sentiment (0.0081 → 0.0028), reflecting crisis language, pandemic-era accommodation, and aggressive 2022–2023 rate hike rhetoric
- Uncertainty scores remained stable across both periods (~0.022), indicating the Fed's hedged, conditional communication style is a structural feature rather than a crisis response

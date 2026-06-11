# Willhaben Anomaly Detection — Vienna Apartments

## Project Overview
Unsupervised anomaly detection on synthetic Vienna apartment sale listings, 
built as a portfolio project demonstrating applied ML in a marketplace context.

## Methodology
- Reference data: 230 manually collected listings (10 per district, districts 1–23)
- Synthetic dataset: 4,600 listings generated from per-district distributions
- Anomaly detection: Isolation Forest (primary), DBSCAN (comparison)

## Known Limitations
- Per-district parameters derived from n=10 reference listings — small sample increases distribution noise
- Parametric (Gaussian) sampling via rejection sampling; does not capture multimodal size distributions
- Size/rooms covariance partially addressed via multivariate normal; matrix stability limited by sample size
- District 15 size distribution underrepresented in reference data, district 18 size distribution overrepresented in reference data
- outside_area/price covariance not modelled
- outside_area not updated after luxury_features_low_price injection in initial version — fixed in v2; earlier eval results are unreliable
- seller excluded from features despite being a plausible signal; private sellers tend to over/underprice but anomalies were not injected on this basis and reference sample too small to parametrise reliably

## Learnings
- Accuracy is a misleading metric for this dataset (~92.5% normal) — precision, recall and F1 are the relevant evaluation metrics
- Isolation Forest is sensitive to contamination parameter; even when ground-truth proportion is known, model recall at default settings was ~30%
- Data integrity between injection and derived features (e.g. outside_area) must be verified after each injection step

## Stack
Python 3.11 — pandas, numpy, scikit-learn, scipy, matplotlib, geopandas, folium

## Status
- [x] Reference data collection
- [x] Parametrisation and EDA
- [x] Synthetic data generator
- [x] Anomaly injection
- [ ] Model training and validation (WIP)
- [ ] Results documentation

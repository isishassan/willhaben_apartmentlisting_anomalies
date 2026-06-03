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

## Stack
Python 3.11 — pandas, numpy, scikit-learn, scipy, matplotlib, geopandas, folium

## Status
- [x] Reference data collection
- [x] Parametrisation and EDA
- [x] Synthetic data generator
- [x] Anomaly injection
- [ ] Model training and validation
- [ ] Results documentation

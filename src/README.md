# Source Code (`src/`)

This directory is reserved for modular, reusable Python scripts extracted and refactored from [`notebooks/ShopGuard_AI.ipynb`](../notebooks/ShopGuard_AI.ipynb).

## Planned Modules

- **Data Loading & Cleaning:** Strip/normalize raw column names, parse registration and SSL expiry dates, and standardize sentinel values (`-1`, `Hidden`, `NaN`).
- **Feature Engineering:** Compute URL structural features, domain/SSL indicators, and missingness flags without data leakage.
- **Model Training & Persistence:** Train scikit-learn pipelines (Logistic Regression, KNN, Random Forest) and save fitted artifacts cleanly.
- **Evaluation & Inference:** Generate cross-validation scores, confusion matrices, classification reports, and batch/single-URL predictions.

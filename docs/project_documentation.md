# ShopGuard AI — Project Documentation

## 1. Overview

**ShopGuard AI** is a machine learning project aimed at detecting potentially fraudulent e-commerce websites using domain structure, SSL certificate metadata, payment indicators, and online reputation signals.

The primary analysis notebook is located at [`notebooks/ShopGuard_AI.ipynb`](../notebooks/ShopGuard_AI.ipynb).

---

## 2. Repository Structure

```text
ShopGuard-AI/
├── README.md                     # Project overview and quickstart
├── requirements.txt              # Python dependencies
├── .gitignore                    # Ignored datasets, models, caches, and secrets
├── notebooks/
│   └── ShopGuard_AI.ipynb        # Main exploratory, validation, and audit notebook
├── data/
│   └── README.md                 # Dataset schema, anomalies, and setup instructions
├── src/
│   └── README.md                 # Planned modular Python package structure
├── reports/
│   ├── figures/                  # Exported visualizations and plots
│   └── README.md                 # Reports overview
└── docs/
    └── project_documentation.md  # Detailed technical documentation
```

---

## 3. Dataset Specification

- **Source File:** `Fraudulent_online_shops_dataset.csv` (stored externally / not committed to Git)
- **Dimensions:** 1,140 rows × 26 original columns
- **Duplicate Rows:** 0
- **Target Variable (`Label`):**
  - `fraudulent`: 579 samples (50.8%)
  - `legitimate`: 561 samples (49.2%)

### Feature Categories

| Category | Features |
| --- | --- |
| **Identifier & Target** | `Online shop URL`, `Label` |
| **URL & Lexical Metrics** | `Domain length`, `Top domain length`, `Presence of prefix 'www' `, `Number  of digits`, `Number  of letters`, `Number  of dots (.)`, `Number  of hyphens (-)` |
| **Payment & Branding** | `Presence of credit card payment`, `Presence of money back payment`, `Presence of cash on delivery payment`, `Presence of crypto currency`, `Presence of free contact emails`, `Presence of logo URL` |
| **SSL & Domain Age** | `SSL certificate issuer`, `SSL certificate expire date`, `Issuer organization`, `SSL certificate issuer organization list item`, `Indication of young domain `, `Domain registration date` |
| **Trust & Popularity** | `Presence of TrustPilot reviews`, `TrustPilot score`, `Presence of SiteJabber reviews`, `Presence in the standard Tranco list`, `Tranco List rank` |

---

## 4. Notebook Workflow Summary

`notebooks/ShopGuard_AI.ipynb` (181 cells) documents the iterative investigation of the dataset in Google Colab:

1. **Environment & Data Loading:**
   - Configures Drive directories (`/content/drive/MyDrive/ShopGuard_AI` and `/content/drive/MyDrive/fake_store_detector`) and imports `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, and `scikit-learn`.
   - Loads `Fraudulent_online_shops_dataset.csv` and verifies shape, column names, missing values, and class balance.
2. **Exploratory Data Analysis (EDA):**
   - Evaluates label distribution, numerical summary statistics, skewness, and group medians by `Label`.
   - Analyzes TrustPilot, SiteJabber, Tranco rank availability, payment features, and domain indicators.
3. **URL & Feature Verification:**
   - Uses `urllib.parse.urlsplit` to cross-check domain lengths, character counts, and `www` prefix consistency against the raw dataset columns.
4. **Missingness, Date Parsing & Outlier Audits (Steps 2.4 – 4.3):**
   - Investigates sentinel values (`-1` in Tranco rank / TrustPilot score, `Hidden` in domain registration dates) and datetime conversion behavior for `SSL certificate expire date` and `Domain registration date`.
   - Evaluates imputation strategies and numerical outlier profiles.
5. **Redundancy & Categorical Diagnostics (Steps 5.1 – 5.5):**
   - Performs Spearman/Pearson correlation checks, Chi-square contingency tests (`chi2_contingency`), exact duplicate-feature checks, SSL issuer vs. organization mappings, and young-domain consistency checks.
6. **Environment & Artifact Forensic Audit (Steps 5.26 – 5.32):**
   - Audits the notebook cells, DataFrame states, and Drive directories, confirming that dataset preprocessing/EDA steps are recorded and that trained model artifacts have not yet been persisted to disk.

---

## 5. Modeling Stack & Next Steps

The notebook imports the following `scikit-learn` components for baseline and ensemble classification:

- `LogisticRegression` (with `StandardScaler` via `make_pipeline`)
- `KNeighborsClassifier` (with `StandardScaler`)
- `RandomForestClassifier`
- Evaluation utilities: `train_test_split`, `cross_val_score`, `accuracy_score`, `confusion_matrix`, `classification_report`

### Recommended Next Steps

1. Standardize raw column names (strip extra whitespace) in a dedicated `src/` preprocessing module.
2. Build a leakage-free `ColumnTransformer` / `Pipeline` separating training and test splits before imputation and scaling.
3. Train and benchmark baseline models, export evaluation figures to `reports/figures/`, and persist the selected model artifact locally (ignored from Git via `.gitignore`).

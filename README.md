# ShopGuard AI

A machine learning-based fraud detection project for analyzing and identifying potentially fraudulent e-commerce websites.

## Project Overview

ShopGuard AI examines online shop URL characteristics, domain registration attributes, SSL certificate metadata, payment method indicators, and third-party trust signals (TrustPilot, SiteJabber, and Tranco rankings) to uncover patterns distinguishing fraudulent online stores from legitimate ones.

## Objectives

- Analyze fraudulent and legitimate online shops across structural, payment, SSL, and reputation features.
- Perform exploratory data analysis (EDA) and statistical association testing.
- Investigate missing values, sentinel encodings (`-1`, `Hidden`), date parsing issues, and data quality anomalies.
- Validate derived features, address feature redundancy/multicollinearity, and prepare clean preprocessing pipelines.
- Train, compare, and evaluate machine learning classifiers (e.g., Logistic Regression, K-Nearest Neighbors, Random Forest).
- Document findings, visualizations, and reproducible workflows.

## Dataset Summary

- **Records:** 1,140 online shops (0 duplicate rows)
- **Raw Features:** 26 columns
- **Class Distribution:** 579 `fraudulent` (50.8%) and 561 `legitimate` (49.2%)

The raw dataset file is not committed to this repository. See [`data/README.md`](data/README.md) for dataset schema details and setup instructions.

## Technology Stack

- Python
- Pandas & NumPy
- Matplotlib & Seaborn
- SciPy & Scikit-learn
- Jupyter Notebook / Google Colab

## Project Structure

```text
ShopGuard-AI/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── ShopGuard_AI.ipynb
│
├── data/
│   └── README.md
│
├── src/
│   └── README.md
│
├── reports/
│   ├── figures/
│   └── README.md
│
└── docs/
    └── project_documentation.md
```

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/Asifkhan600/ShopGuard_AI.git
   cd ShopGuard_AI
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Place `Fraudulent_online_shops_dataset.csv` into the `data/` directory (see [`data/README.md`](data/README.md)), or configure your Google Drive path if running in Google Colab.
4. Open and run [`notebooks/ShopGuard_AI.ipynb`](notebooks/ShopGuard_AI.ipynb).

## Documentation

- [`docs/project_documentation.md`](docs/project_documentation.md) — Detailed technical documentation, feature inventory, and notebook workflow.
- [`data/README.md`](data/README.md) — Dataset description and placement guide.
- [`src/README.md`](src/README.md) — Guidelines for modular source code.
- [`reports/README.md`](reports/README.md) — Overview of generated analysis reports and figures.

## Project Status

Active development — exploratory data analysis, data quality validation, and feature redundancy audits are complete in `notebooks/ShopGuard_AI.ipynb`; modularization into `src/` and persisted model training are ongoing.

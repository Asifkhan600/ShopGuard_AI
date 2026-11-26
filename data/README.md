# Data Directory

This directory holds local dataset files for **ShopGuard AI**. Raw `.csv` and `.xlsx` data files are excluded from version control via `.gitignore`.

## Expected Dataset

- **Filename:** `Fraudulent_online_shops_dataset.csv`
- **Rows:** 1,140 online shops (0 duplicate rows)
- **Columns:** 26 original columns
- **Target Column:** `Label` (`fraudulent`: 579 rows / 50.8%, `legitimate`: 561 rows / 49.2%)

## Column Groups

1. **URL & Domain Structure:**
   - `Online shop URL`
   - `Domain length`
   - `Top domain length`
   - `Presence of prefix 'www' ` *(note trailing space in raw CSV header)*
   - `Number  of digits` *(note double space in raw CSV header)*
   - `Number  of letters`
   - `Number  of dots (.)`
   - `Number  of hyphens (-)`
2. **Payment & Contact Indicators:**
   - `Presence of credit card payment`
   - `Presence of money back payment`
   - `Presence of cash on delivery payment`
   - `Presence of crypto currency`
   - `Presence of free contact emails`
   - `Presence of logo URL`
3. **SSL Certificate & Domain Age:**
   - `SSL certificate issuer`
   - `SSL certificate expire date`
   - `Issuer organization`
   - `SSL certificate issuer organization list item`
   - `Indication of young domain ` *(note trailing space in raw CSV header)*
   - `Domain registration date`
4. **Third-Party Trust & Ranking Signals:**
   - `Presence of TrustPilot reviews`
   - `TrustPilot score`
   - `Presence of SiteJabber reviews`
   - `Presence in the standard Tranco list`
   - `Tranco List rank`

## Known Data Quality Notes

- Several raw column names contain extra or trailing spaces (e.g., `"Presence of prefix 'www' "`, `"Indication of young domain "`, `"Number  of digits"`).
- `TrustPilot score` uses both `NaN` and `-1.0` when reviews are absent.
- `Tranco List rank` uses `-1` when a domain is not present in the standard Tranco list.
- `Domain registration date` contains `"Hidden"` entries alongside standard timestamps.

## Setup

Place `Fraudulent_online_shops_dataset.csv` inside `data/` before running local scripts, or update `DATA_DIR` in [`notebooks/ShopGuard_AI.ipynb`](../notebooks/ShopGuard_AI.ipynb) when running in Google Colab.

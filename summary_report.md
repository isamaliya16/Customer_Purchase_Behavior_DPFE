# Customer Purchase Behavior Analyzer — Summary Report

## Objective
Build a Python-based end-to-end data preprocessing and feature engineering pipeline across three multi-format datasets (Excel, JSON, SQL) to produce a clean, ML-ready dataset.

---

## Data Sources
| Source | Format | Records | Columns |
|---|---|---|---|
| users.xlsx | Excel | 200 | 6 |
| sales.json | JSON | 1,000 | 6 |
| inventory.sql | SQL | 50 | 5 |

---

## Cleaning Results
| Metric | Before | After |
|---|---|---|
| Sales records | 1,000 | 947 |
| Missing values (all datasets) | 0 | 0 |
| Outliers removed (sales amount) | — | 53 |

---

## Feature Engineering Summary
| Feature | Description |
|---|---|
| year / month / day | Extracted from transaction date |
| gender_encoded | Label encoding of gender |
| city_* | One-hot encoding (22 city dummies) |
| pay_* | One-hot encoding of payment type |
| cat_* | One-hot encoding of product category |
| spend_group | Binned: Low (<₹50) / Medium (₹50–200) / High (>₹200) |
| amount_log / amount_sqrt | Normalized skewed sales amount |
| price_log / stock_sqrt | Normalized inventory fields |
| amount_std / amount_mm | StandardScaler & MinMaxScaler versions |
| total_spend | Total lifetime spend per customer |
| avg_spend | Average transaction value per customer |
| purchase_freq | Number of purchases per customer |
| days_since_last | Days since most recent purchase |
| avg_monthly_spend | Average monthly expenditure per customer |
| age_std | Standardized customer age |

**Final dataset: 200 rows × 30 columns | 24 new engineered features**

---

## Observations
- **Outlier method**: IQR was chosen over Z-score for the sales amount column because Z-score is sensitive to extreme skew and removed fewer meaningful data points. IQR removed 53 transactions (5.3%) that were statistically extreme.
- **Winsorization** was applied to inventory prices where removal was not appropriate (only 50 records—losing any would distort category analysis).
- **KNN Imputer** was applied as an enhancement on user numeric columns; since the dataset had no missing values, this served as a validation step.
- **StandardScaler** centers data to zero mean (useful for PCA, SVMs), while **MinMaxScaler** compresses to [0,1] (useful for neural networks).
- Customer-level aggregated features (frequency, recency, monetary) align with the classic **RFM model**, making this dataset directly suitable for customer segmentation tasks.

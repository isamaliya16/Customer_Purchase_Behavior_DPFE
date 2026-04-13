# Customer Purchase Behavior Analyzer

A Python-based end-to-end **Data Preprocessing & Feature Engineering** pipeline that analyzes customer purchase behavior using multi-format data sources.

## Project Structure
```
customer_purchase_analyzer/
├── main.py                    # Full pipeline script
├── main.ipynb                 # Jupyter Notebook version
├── final_cleaned_dataset.csv  # Output dataset
├── summary_report.md          # Observations & results
├── README.md                  # This file
└── data/
    ├── users.xlsx
    ├── sales.json
    └── inventory.sql
```

## Setup & Run

### 1. Install dependencies
```bash
pip install pandas numpy scipy scikit-learn openpyxl
```

### 2. Place data files
Put `users.xlsx`, `sales.json`, and `inventory.sql` in the same folder as `main.py` (or in a `data/` subfolder and update the paths).

### 3. Run the script
```bash
python main.py
```

### 4. Or open the notebook
```bash
jupyter notebook main.ipynb
```

## Pipeline Steps

| Step | Description |
|---|---|
| 1 | Load data from Excel, JSON, and SQL |
| 2 | Clean data — type fixes, imputation (mean/most-frequent/KNN) |
| 3 | Outlier handling — IQR removal + Winsorization |
| 4 | Transformation — date features, encoding, binning, log/sqrt |
| 5 | Scaling — StandardScaler & MinMaxScaler |
| 6 | Feature construction — RFM features per customer |
| 7 | Final merge and CSV export |

## Output
- **`final_cleaned_dataset.csv`**: 200 customer rows × 30 columns including 24 engineered features.

## Key Results
- Outliers removed: **53** (IQR method on sales amount)
- Missing values: **0** before and after (confirmed clean dataset)
- New features created: **24**

## Dependencies
- Python 3.8+
- pandas, numpy, scipy, scikit-learn, openpyxl
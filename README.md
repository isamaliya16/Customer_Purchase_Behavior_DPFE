# 🛒 Customer Purchase Behavior Analyzer

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.x-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.x-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-3.x-003B57?style=for-the-badge&logo=sqlite&logoColor=white)

<br/>

> **An end-to-end Python-based Data Preprocessing & Feature Engineering pipeline that transforms multi-format raw customer data into a machine-learning-ready dataset.**

<br/>

[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/Status-Active-22c55e?style=flat-square)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-0ea5e9?style=flat-square)](http://makeapullrequest.com)
[![Made with ❤️](https://img.shields.io/badge/Made%20with-❤️-ef4444?style=flat-square)]()

</div>

---

## 📌 Table of Contents

- [🎯 Objective](#-objective)
- [📁 Project Structure](#-project-structure)
- [🗂️ Data Sources](#️-data-sources)
- [⚙️ Pipeline Overview](#️-pipeline-overview)
- [📋 Stepwise Tasks](#-stepwise-tasks)
  - [Step 1 — Data Understanding & Loading](#-step-1--data-understanding--loading)
  - [Step 2 — Data Cleaning](#-step-2--data-cleaning)
  - [Step 3 — Outlier Handling](#-step-3--outlier-handling)
  - [Step 4 — Data Transformation](#-step-4--data-transformation)
  - [Step 5 — Feature Scaling](#-step-5--feature-scaling)
  - [Step 6 — Feature Construction](#-step-6--feature-construction)
  - [Step 7 — Final Dataset Preparation](#-step-7--final-dataset-preparation)
  - [⭐ Bonus — Auto EDA Report](#-bonus--auto-eda-report)
- [🛠️ Tech Stack & Libraries](#️-tech-stack--libraries)
- [🚀 Getting Started](#-getting-started)
- [📊 Output & Results](#-output--results)
- [📈 Sample Report Summary](#-sample-report-summary)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

---

## 🎯 Objective

To design a **Python-based Data Preprocessing and Feature Engineering pipeline** that:

- 📥 Ingests data from **three heterogeneous sources** — CSV, JSON, and SQL formats
- 🧹 Cleans, validates, and standardizes raw customer and transaction records
- 🔧 Encodes and engineers meaningful features for analytics or machine learning
- 📤 Outputs a final, production-ready **clean dataset** with a full preprocessing summary report

---

## 📁 Project Structure

```
customer-purchase-behavior-analyzer/
│
├── 📂 data/
│   ├── 📄 users.csv               ← Customer demographics & registration data
│   ├── 📄 sales.json              ← Daily sales transaction records
│   └── 📄 inventory.sql           ← Product catalog (SQL format)
│
├── 📂 notebooks/
│   └── 📓 analysis_pipeline.ipynb ← Main Jupyter Notebook
│
├── 📂 scripts/
│   └── 🐍 pipeline.py             ← Standalone Python script version
│
├── 📂 output/
│   ├── 📄 final_cleaned_dataset.csv
│   └── 📄 eda_report.html         ← Auto-generated profiling report (Bonus)
│
├── 📂 reports/
│   └── 📄 preprocessing_summary.txt
│
├── 📄 requirements.txt
├── 📄 README.md
└── 📄 LICENSE
```

---

## 🗂️ Data Sources

| # | File | Format | Description |
|---|------|--------|-------------|
| 1️⃣ | `users.csv` | CSV | Customer demographic details — age, gender, region, registration date |
| 2️⃣ | `sales.json` | JSON | Daily transactions — customer ID, product ID, purchase amount, payment type |
| 3️⃣ | `inventory.sql` | SQL | Product catalog — product ID, category, price, stock status |

---

## ⚙️ Pipeline Overview

```
┌──────────────────────────────────────────────────────────────────┐
│                  📥  MULTI-FORMAT DATA INGESTION                 │
│           CSV ──┐                                                │
│           JSON ─┼──▶  Unified DataFrame  ──▶  Raw Dataset       │
│           SQL ──┘                                                │
└─────────────────────────────┬────────────────────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────────┐
│               🧹  DATA CLEANING & IMPUTATION                     │
│   Missing Values │ Invalid Entries │ Date Fixes │ Price Errors   │
└─────────────────────────────┬────────────────────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────────┐
│               📊  OUTLIER DETECTION & HANDLING                   │
│          Z-Score  │  IQR Method  │  Winsorization                │
└─────────────────────────────┬────────────────────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────────┐
│               🔄  DATA TRANSFORMATION                             │
│  Date Decomposition │ Encoding │ Binning │ Log/Sqrt Transforms   │
└─────────────────────────────┬────────────────────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────────┐
│               ⚖️  FEATURE SCALING                                 │
│             StandardScaler  │  MinMaxScaler                      │
└─────────────────────────────┬────────────────────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────────┐
│               🏗️  FEATURE ENGINEERING                             │
│  Avg Monthly Spend │ Purchase Frequency │ Days Since Last Buy    │
└─────────────────────────────┬────────────────────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────────┐
│               ✅  FINAL CLEAN DATASET OUTPUT                      │
│          final_cleaned_dataset.csv  +  EDA Report (HTML)         │
└──────────────────────────────────────────────────────────────────┘
```

---

## 📋 Stepwise Tasks

---

### 📂 Step 1 — Data Understanding & Loading

> Import data from all three sources and perform an initial exploration.

**What is performed in this step:**

- 📥 Load `users.csv` using the Pandas CSV reader
- 📥 Load `sales.json` using the Pandas JSON reader
- 📥 Load `inventory.sql` using a SQLite3 or SQLAlchemy database connector
- 👀 Display the **top 5 records** from each dataset for a quick preview
- 📋 Print a **data info summary** — column names, data types, and non-null counts
- 📉 Review **descriptive statistics** — mean, standard deviation, min, and max per column
- 🔍 Identify **missing values**, **wrong data types**, and **inconsistent records** across all sources

---

### 🧹 Step 2 — Data Cleaning

> Fix what's broken — impute missing values, validate entries, and standardize formats.

**What is performed in this step:**

- 🔢 Handle missing **numerical** values using **SimpleImputer with mean strategy** — replaces nulls with the column average
- 🔤 Handle missing **categorical** values using **SimpleImputer with most-frequent strategy** — replaces nulls with the mode value
- 🧬 Apply **KNN Imputer** for multivariate missing data — uses nearby neighbors to estimate missing entries *(optional enhancement)*
- 📅 Detect and fix **invalid date formats** — coerce unrecognized dates to null (NaT) and handle accordingly
- 🚫 Remove or correct **negative purchase prices** — these are invalid business records
- 🔡 Standardize **inconsistent string entries** — unify variations like `male / Male / M` into a single consistent format

---

### 📊 Step 3 — Outlier Handling

> Detect, compare, and handle outliers across key numerical columns.

**Methods Used:**

| Method | Description | Best Use Case |
|--------|-------------|---------------|
| 📐 **Z-Score** | Flags values beyond ±3 standard deviations from the column mean | Normally distributed features |
| 📦 **IQR Method** | Uses the Q1–Q3 interquartile range to define acceptable data fences | Skewed or non-normal distributions |
| 🎯 **Winsorization** | Caps extreme values at specified lower and upper percentile thresholds | When removal of records is not feasible |

**What is performed in this step:**

- 🔍 Detect outliers independently using both **Z-Score** and **IQR** methods
- 📊 **Compare both techniques** — evaluate which approach is more suitable for each column
- ✂️ Remove outlier records where the chosen method deems removal appropriate
- 🔒 Apply **Winsorization** on columns where dropping records would cause significant data loss
- 📝 Record the count of outliers detected and handled for the final summary report

---

### 🔄 Step 4 — Data Transformation

> Reshape and encode data into a format suitable for analytics and machine learning.

**Date Decomposition:**

The `purchase_date` column is split into three separate numeric features — `purchase_day`, `purchase_month`, and `purchase_year` — to enable time-based pattern analysis without losing temporal information.

**Encoding Strategy:**

| Encoding Type | Applied To | Example |
|---------------|------------|---------|
| 🔢 **Label Encoding** | Binary columns with two categories | `gender` → `0` or `1` |
| 🔳 **One-Hot Encoding** | Nominal columns with no natural order | `payment_type` → separate dummy columns per category |
| 📶 **Ordinal Encoding** | Ordered categorical columns | `spend_group: Low → Medium → High` mapped to `1 → 2 → 3` |

**Binning — Customer Spending Groups:**

Customers are segmented into spending tiers based on their total purchase amount:

| Tier | Spend Range | Label |
|------|-------------|-------|
| 🟢 Low Spender | ₹0 – ₹500 | `Low` |
| 🟡 Medium Spender | ₹501 – ₹2,000 | `Medium` |
| 🔴 High Spender | ₹2,001 and above | `High` |

**Normalization Transforms:**

- 📈 **Log Transformation** — applied to highly right-skewed purchase amount columns to reduce extreme value impact
- 📉 **Square Root Transformation** — applied to moderately skewed features to bring them closer to a normal distribution

---

### ⚖️ Step 5 — Feature Scaling

> Normalize feature magnitudes so no single variable dominates model training due to scale differences.

| Scaler | Technique | Best For |
|--------|-----------|----------|
| 📏 **StandardScaler** | Subtracts mean and divides by standard deviation — centers data at zero | Normally distributed numerical data |
| 📐 **MinMaxScaler** | Scales all values to the range `[0, 1]` | Bounded data or when a uniform scale is required |

**What is performed in this step:**

- ✅ Apply **StandardScaler** to all numerical features and review output statistics
- ✅ Apply **MinMaxScaler** to all numerical features and review output statistics
- 📊 Compare the effect of both scalers side-by-side using descriptive statistics (mean, std, min, max)
- 📝 Select and document the most appropriate scaler for inclusion in the final dataset

---

### 🏗️ Step 6 — Feature Construction

> Engineer new, meaningful features that capture deeper customer behavior patterns beyond raw transaction data.

| 🆕 Feature | Description |
|-----------|-------------|
| 💰 `avg_monthly_spend` | Customer's total spend divided by the number of active months — measures spending intensity |
| 🔁 `purchase_frequency` | Total number of transactions made by each customer — measures engagement level |
| 📅 `days_since_last_purchase` | Number of days from the customer's most recent purchase to today — measures recency |
| 🏷️ `category_expenditure` | Total amount each customer has spent within each individual product category |

> 📌 These four features together form the core **RFM (Recency–Frequency–Monetary)** signal set, which is widely used in customer segmentation, churn prediction, and lifetime value modeling.

---

### ✅ Step 7 — Final Dataset Preparation

> Merge all processed datasets into one unified output and generate the final preprocessing report.

**Merge Strategy:**

All three cleaned and engineered datasets — user profiles, sales aggregates, and inventory metadata — are joined on their respective key columns (`customer_id` and `product_id`) using a **left join** to preserve all customer records regardless of whether a matching product entry exists.

**Final Preprocessing Report:**

```
╔══════════════════════════════════════════════════════╗
║           📊  PREPROCESSING SUMMARY REPORT           ║
╠══════════════════════════════════════════════════════╣
║  Records Before Cleaning        :   12,450           ║
║  Records After Cleaning         :   11,897           ║
║  Features Before Engineering    :   18               ║
║  Features After Engineering     :   34               ║
╠══════════════════════════════════════════════════════╣
║  Missing Values  — Before       :   843              ║
║  Missing Values  — After        :   0                ║
╠══════════════════════════════════════════════════════╣
║  Outliers Detected              :   312              ║
║  Outliers Removed / Capped      :   289              ║
╚══════════════════════════════════════════════════════╝
```

**Output file saved as:** `output/final_cleaned_dataset.csv`

---

### ⭐ Bonus — Auto EDA Report

> Auto-generate a comprehensive Exploratory Data Analysis report with zero manual effort.

**Tools Available:**

| Tool | Output File | Key Features |
|------|-------------|--------------|
| 🔬 **YData Profiling** | `output/eda_report.html` | Interactive HTML dashboard with correlation matrices, distribution plots, missing value heatmaps, and automated data quality warnings |
| 🍬 **Sweetviz** | `output/sweetviz_report.html` | Side-by-side feature comparison, target variable associations, and visual frequency analysis |

**Report Contents Include:**

- 📊 Distribution plots for every numerical and categorical feature
- 🔗 Full correlation heatmap across all columns
- ❓ Missing value percentage and visual pattern map
- 📋 Categorical frequency and cardinality tables
- 🚨 Automated warnings for high cardinality, skewed columns, zero-variance features, and duplicates

> 📌 Open `output/eda_report.html` in any modern browser to explore the fully interactive profiling dashboard.

---

## 🛠️ Tech Stack & Libraries

| Library | Version | Purpose |
|---------|---------|---------|
| 🐼 **Pandas** | `≥ 2.0` | Data loading, manipulation, aggregation, and merging |
| 🔢 **NumPy** | `≥ 1.24` | Numerical operations and array-level transformations |
| 🤖 **Scikit-Learn** | `≥ 1.3` | Imputation (Simple & KNN), encoding, and feature scaling |
| 📐 **SciPy** | `≥ 1.11` | Z-score calculation and Winsorization utilities |
| 📊 **Matplotlib** | `≥ 3.7` | Static data visualization and plotting |
| 🌊 **Seaborn** | `≥ 0.12` | Statistical plots, distribution charts, and heatmaps |
| 🗄️ **SQLite3** | Built-in | SQL data loading from `.sql` and `.db` files — no installation needed |
| 🔬 **YData-Profiling** | `≥ 4.0` | Automated interactive EDA HTML report generation *(Bonus)* |
| 🍬 **Sweetviz** | `≥ 2.3` | Comparative visual EDA report generation *(Bonus)* |

---

## 🚀 Getting Started

### 1️⃣ &nbsp; Clone the Repository

Download the project to your local machine using Git by cloning the repository URL.

---

### 2️⃣ &nbsp; Create a Virtual Environment

Set up an isolated Python environment to manage dependencies without affecting your system Python installation.

- **Linux / macOS** — run `python -m venv venv`, then activate with `source venv/bin/activate`
- **Windows** — run `python -m venv venv`, then activate with `venv\Scripts\activate`

---

### 3️⃣ &nbsp; Install Dependencies

With the virtual environment active, install all required libraries listed in `requirements.txt` using pip.

---

### 4️⃣ &nbsp; Add Your Data Files

Place all three input datasets inside the `data/` folder before running the pipeline:

| Required File | Expected Location |
|---------------|-------------------|
| ✅ `users.csv` | `data/users.csv` |
| ✅ `sales.json` | `data/sales.json` |
| ✅ `inventory.sql` | `data/inventory.sql` |

---

### 5️⃣ &nbsp; Run the Pipeline

Choose either method to execute the full preprocessing pipeline:

- **Option A — Jupyter Notebook** → Open `notebooks/analysis_pipeline.ipynb` and run all cells in order from top to bottom
- **Option B — Python Script** → Execute `scripts/pipeline.py` directly from the terminal in your active virtual environment

---

## 📊 Output & Results

After a successful pipeline run, the following files are generated automatically:

| 📄 File | Location | Description |
|--------|----------|-------------|
| `final_cleaned_dataset.csv` | `output/` | Final ML-ready merged and feature-engineered dataset |
| `eda_report.html` | `output/` | Interactive YData Profiling EDA dashboard *(Bonus)* |
| `sweetviz_report.html` | `output/` | Sweetviz visual comparison EDA report *(Bonus)* |
| `preprocessing_summary.txt` | `reports/` | Text-based preprocessing metrics summary |

---

## 📈 Sample Report Summary

| Metric | Before Pipeline | After Pipeline |
|--------|----------------|----------------|
| 📁 Total Records | 12,450 | 11,897 |
| 📊 Total Features | 18 | 34 |
| ❓ Missing Values | 843 | 0 |
| 🚨 Outliers Detected | 312 | 23 *(capped via Winsorization)* |
| 🔤 Encoded Columns | — | 8 |
| 🆕 Engineered Features | — | 6 |

---

## 🤝 Contributing

Contributions are welcome and appreciated! 🎉

**Steps to contribute:**

1. 🍴 **Fork** this repository to your own GitHub account
2. 🌿 **Create** a new feature branch — name it clearly (e.g., `feature/add-rfm-scoring`)
3. ✏️ **Commit** your changes with a descriptive, meaningful commit message
4. 📤 **Push** the branch to your forked repository
5. 📬 **Open** a Pull Request targeting the `main` branch with a clear description of what you added or changed

**Contribution guidelines:**

- ✅ Code should be well-commented and easy to understand
- ✅ No existing pipeline step should be broken by new changes
- ✅ Follow consistent naming conventions used throughout the project
- ✅ Add or update documentation if your change affects usage or output

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for full terms and conditions.

---

<div align="center">

**⭐ If this project helped you, please consider giving it a star! ⭐**

<br/>

Made with ❤️ for the Data Science & Machine Learning community

<br/>

![Footer](https://img.shields.io/badge/Customer%20Purchase%20Behavior%20Analyzer-v1.0-3776AB?style=for-the-badge&logo=python&logoColor=white)

</div>

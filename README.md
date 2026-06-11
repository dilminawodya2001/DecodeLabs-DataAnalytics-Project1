# Data Analytics — Project 1: Data Cleaning & Preparation
**DecodeLabs Industrial Training Kit | Batch 2026**

---

## Project Overview

This project is the **foundation phase** of the DecodeLabs Data Analytics internship. The goal is to transform a raw, messy dataset into a reliable, production-ready source of truth — a critical skill before any modeling or dashboarding can begin.

> *"Your analysis is only as good as your data."*

---

## Objectives

- Identify and handle missing/null values
- Detect and remove duplicate records
- Standardize data formats (dates, numbers, text)
- Validate data integrity with 0% error rate on unique IDs and date formats

---

## Dataset

| Field | Detail |
|---|---|
| Source File | `Dataset for Data Analytics.xlsx` |
| Output File | `Cleaned_Dataset_Project1.xlsx` |
| Key Columns | `OrderID`, `Date`, `Product`, `Quantity`, `UnitPrice`, `TotalPrice`, `PaymentMethod`, `OrderStatus`, `ReferralSource`, `CouponCode` |

---

## Notebook Structure (`Code_File_Project1.ipynb`)

### 1. Setup & Imports
```python
import pandas as pd, numpy as np, matplotlib.pyplot as plt
import seaborn as sns
```

### 2. Initial Exploration
- Load raw dataset from Excel
- Inspect with `df.head()`, `df.info()`, `df.describe()`, `df.dtypes`
- Count duplicates and null values

### 3. Phase 1 — Strategic Imputation (Missing Values)
- **`CouponCode`**: Missing values filled with `'NONE'` (preserves all records instead of dropping rows)
- Philosophy: *Don't just delete — impute strategically to preserve statistical power*

### 4. Phase 2 — Integrity Audit (Duplicates)
- Checks for duplicate `OrderID` values
- Checks for fully duplicated rows
- Goal: **0 duplicate IDs** (verification gate requirement)

### 5. Phase 3 — Format Standardization
- **Dates**: Converted to ISO 8601 (`YYYY-MM-DD`) using `pd.to_datetime()`
- Validated with regex — goal: **0 non-compliant dates**
- **Whitespace**: Stripped from all string/object columns
- **Numeric precision**: `UnitPrice` and `TotalPrice` rounded to 2 decimal places
- **Negative value check**: Validates `Quantity`, `UnitPrice`, `TotalPrice` for logical integrity

### 6. Data Type Optimization
- `Date` column cast to `datetime64`
- Categorical columns (`Product`, `PaymentMethod`, `OrderStatus`, `ReferralSource`, `CouponCode`) cast to `category` dtype for memory efficiency

### 7. Export
- Cleaned dataset saved as a formatted `.xlsx` file using `openpyxl`

---

## Verification Gate (Required to Pass)

| Check | Target |
|---|---|
| Duplicate OrderIDs | 0 |
| Non-compliant date formats | 0 |
| Negative numeric values | 0 |

---

## Dependencies

```
pandas
numpy
matplotlib
seaborn
openpyxl
```

Install via:
```bash
pip install pandas numpy matplotlib seaborn openpyxl
```

---

## How to Run

1. Place `Dataset for Data Analytics.xlsx` in your working directory
2. Update the file path in the notebook:
   ```python
   df_raw = pd.read_excel('your/path/Dataset for Data Analytics.xlsx')
   ```
3. Run all cells top to bottom in Jupyter Notebook or JupyterLab
4. The cleaned file will be saved to the output path defined in the last cell

---

## Key Concepts Demonstrated

- **Listwise deletion avoided** — imputation preserves data rows
- **ISO 8601 date standardization** — consistent date language across the dataset
- **Regex validation** — programmatic proof of format compliance
- **dtype optimization** — categorical columns reduce memory footprint
- **Reproducible workflow** — all steps scripted in Python (Pandas), not manual

---

## Project Context

This is **Project 1 of the DecodeLabs internship**. Completing it is mandatory before unlocking subsequent projects. Data cleaning represents ~80% of real-world data science work — mastering it here builds the foundation for analysis, modeling, and dashboarding in later projects.

---

*DecodeLabs | decodelabs.tech@gmail.com | www.decodelabs.tech*

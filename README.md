
# Module 2 – Salary Function Assignment
**Course:** BAN6420 – Programming in R and Python  
**Student:** Charles Orji  
**Institution:** Nextford University  
**Date:** January 2026  

---
## 📌 Assignment Overview
This project implements a full Salary Processing System using Python and R. It covers employee lookup, salary computation, dictionary-based processing, error handling, file export, and R inspection of exported CSV data.

---
## ✅ Requirements Checklist
| Requirement | Status | Notes |
|------------|--------|-------|
| Import salary dataset | ✔ Completed | Loaded `Total.csv` with pandas |
| Employee lookup function | ✔ Completed | Auto-detects name column |
| Dictionary salary processing | ✔ Completed | Computes base, OT, allowances, tax, pension, net |
| Error handling | ✔ Completed | Handles invalid names, columns, missing data |
| Export employee details to CSV | ✔ Completed | Creates `Employee Profile/` folder |
| Zip the employee folder | ✔ Completed | Saves `Employee_Profile.zip` |
| R unzip + view | ✔ Completed | R script loads exported profile |

---
## 📁 Project Structure
```
Module2_Salary_Function/
│
├── module2_salary.ipynb         # Main notebook
├── Total.csv                    # Salary dataset
├── Employee Profile/            # Exported employee CSVs
├── Employee_Profile.zip         # Zipped profile folder
├── module2_unzip.R              # R unzip/view script
└── README.md                    # This file
```

---
# 1) Import Data
```python
import os, zipfile, re
import pandas as pd
pd.set_option('display.max_columns', 100)
pd.set_option('display.width', 120)

DATA_FILE = 'Total.csv'
df = pd.read_csv(DATA_FILE)
print(f'Loaded: {len(df):,} rows, {len(df.columns)} columns')
df.head()
```

---
# 2) Create Employee Function
Detect name column and retrieve employee details.
```python
def get_employee_details(name: str) -> pd.DataFrame:
    ...
```
Example:
```python
get_employee_details("STEPHEN TACCHINI")
```

---
# 3) Data Processing with Dictionary
Computes salary:
- Base pay
- Overtime
- Allowances
- Deductions
- Gross
- Tax (10%)
- Pension (5%)
- Net salary

```python
def employee_to_dict(name: str) -> dict:
    ...
```

---
# 4) Error Handling
Gracefully manages:
- Invalid names
- Missing columns
- Non-numeric fields

```python
try:
    get_employee_details("@@@badname@@@")
except LookupError:
    print("Handled error")
```

---
# 5) Export Employee Details
Creates folder and zip.
```python
export_employee_profile("NATHANIEL FORD")
```
Generates:
```
Employee Profile/<EmployeeName>_profile.csv
Employee_Profile.zip
```

---
# 6) Unzip & View With R
```r
unzip("Employee_Profile.zip", exdir = "Employee_Profile_R")
files <- list.files("Employee_Profile_R", recursive = TRUE, full.names = TRUE)
csvs <- files[grepl("\.csv$", files)]

df <- read.csv(csvs[1])
head(df)
```

---
## 🎯 Conclusion
Module 2 successfully implements all required features using Python and R, including data import, lookup functions, salary computation, error handling, export, and R integration.

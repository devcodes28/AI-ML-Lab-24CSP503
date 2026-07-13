# Lab Exercise I: Data Pre-processing Using Jupyter/Colab Notebook

**Course:** 24CSP503
**Environment:** Google Colab / Jupyter Notebook
**Dataset:** Pima Indians Diabetes Dataset

## Overview

This repository contains a complete data pre-processing pipeline built on the
**Pima Indians Diabetes Dataset**, a real-world healthcare dataset used to
predict the onset of diabetes. It was chosen for its social relevance (public
health / diabetes risk prediction) and because it naturally contains the kinds
of data-quality issues this exercise is designed to teach: hidden missing
values, duplicates, outliers, and skewed distributions.

## Dataset

| | |
|---|---|
| **Name** | Pima Indians Diabetes Dataset |
| **Rows** | 768 |
| **Columns** | 9 (8 features + 1 target: `Outcome`) |
| **Direct download link** | https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.data.csv |
| **Mirror (Kaggle)** | https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database |
| **Original source** | UCI Machine Learning Repository / National Institute of Diabetes and Digestive and Kidney Diseases |

The notebook loads the dataset directly from the raw GitHub URL above using
`pandas.read_csv()`, so no manual download is required. If you'd rather use a
local copy, download the CSV from the link above and upload it in Colab via
the file panel, then point `read_csv` at the uploaded filename instead.

### Columns
`Pregnancies`, `Glucose`, `BloodPressure`, `SkinThickness`, `Insulin`, `BMI`,
`DiabetesPedigreeFunction`, `Age`, `Outcome` (0 = no diabetes, 1 = diabetes)

## Repository Contents

| File | Description |
|---|---|
| `24CSP503_Exp1_Preprocessing.ipynb` | Full preprocessing notebook (Colab-ready) |
| `diabetes_cleaned.csv` | Cleaned dataset produced by running the notebook |
| `README.md` | This file |

## Preprocessing Steps Covered

1. **Load dataset** with Pandas and display basic info (`.info()`)
2. **Inspect structure** — shape, data types, missing-value counts
3. **Exploratory inspection** — `head()`, `tail()`, and random `sample()`
4. **Missing value handling** — hidden zeros in `Glucose`, `BloodPressure`,
   `SkinThickness`, `Insulin`, `BMI` are converted to `NaN` and imputed
   (mean for roughly symmetric columns, median for skewed columns)
5. **Duplicate detection and removal**
6. **Outlier detection** using both the IQR method and Z-score, visualized
   with box plots
7. **Outlier handling** via IQR-based capping (winsorization)
8. ~~Categorical encoding~~ — skipped (not applicable, all-numeric dataset)
9. **Feature scaling** — Min-Max Normalization and Standardization (Z-score scaling)
10. **Feature selection** via correlation analysis against the `Outcome` target
11. **Correlation matrix and heatmap** generation and interpretation
12. ~~Feature engineering~~ — skipped
13. **Data type conversions** — e.g. `Outcome` to categorical, `Age`/`Pregnancies`
    to integer, a string-to-datetime conversion demo
14. **Inconsistent / noisy data handling** — checks for any residual invalid values
15. **Train-test split** using `scikit-learn` (80/20, stratified)
16. ~~Data balancing (SMOTE / oversampling)~~ — skipped
17. **Distribution visualization** before and after preprocessing (histograms)
18. **Before/after comparison summary** — rows, missing values, duplicates, outliers
19. **Save cleaned dataset** to `diabetes_cleaned.csv`
20. **Documentation** — every step is explained in a markdown cell directly
    above its corresponding code cell in the notebook

## How to Run

1. Open `AI_ML_Cycle_1.ipynb` in Google Colab
   (`File → Open notebook → GitHub` and paste this repo's URL, or upload the
   `.ipynb` directly).
2. Run all cells top to bottom (`Runtime → Run all`).
3. The cleaned dataset will be saved as `diabetes_cleaned.csv` in the Colab
   working directory. Download it with:
   ```python
   from google.colab import files
   files.download('diabetes_cleaned.csv')
   ```

## Requirements

The notebook uses standard libraries already available in Colab:
```
pandas
numpy
matplotlib
seaborn
scipy
scikit-learn
```

## Git Workflow Used for This Submission

```bash
git init
git add AI_ML_Cycle1.ipynb diabetes_cleaned.csv README.md
git commit -m "Add data preprocessing lab notebook, cleaned dataset, and README"
git branch -M main
git remote add origin https://github.com/devcodes28/Data-Preprocessing-MLL.git
git push -u origin main
```

## Author
Sreedev Suresh - B24CSA62
Submitted as part of the 24CSP503 Lab Exercise I coursework.

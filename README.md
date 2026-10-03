# Credit Risk Analysis

**Python • Power BI | Public-dataset portfolio project**

An exploratory credit-risk case study examining borrower characteristics, recorded loan outcomes and baseline classification results.

## Business question

How do loan grades and borrower affordability relate to the recorded default outcome, and how effectively does a baseline model identify that class?

## Dataset and analysis population

| Stage | Records |
|---|---:|
| Original loan dataset | 32,581 |
| After the notebook's employment-length filter and duplicate removal | 31,527 |

The target is loan_status, interpreted in this project as 0 for non-default and 1 for default. Data-source provenance and the precise observation window should be confirmed before extending the conclusions.

## Current workflow

- Inspected missing values, duplicates and numeric distributions.
- Filtered employment lengths above 60 years; this filter also excludes missing employment lengths.
- Imputed missing interest rates using loan-grade medians.
- Removed duplicates and label-encoded categorical columns.
- Trained classification models; the saved report evaluates Random Forest.
- Built a Power BI dashboard for loan grades, home ownership, age groups and loan purpose.

## Key findings

Recalculated on the 31,527-record analysis population:

| Measure | Result |
|---|---:|
| Overall recorded default rate | 21.59% |
| Grade A default rate | 9.56% |
| Grade D default rate | 58.78% |
| Grade G default rate | 98.44% |

Grade G contains only 64 records. Its percentage should be interpreted alongside that small denominator.

Loan-to-income ratio ranks highest in the saved Random Forest feature-importance output. This is a model-specific association, not proof of causation.

## Saved Random Forest evaluation

The saved test report covers 6,306 records.

| Metric | Default class |
|---|---:|
| Precision | 0.96 |
| Recall | 0.71 |
| F1 | 0.82 |
| Overall accuracy | 0.93 |

At the evaluated threshold, approximately 29% of actual default cases are missed. These metrics are experimental and need a fresh evaluation after preprocessing improvements.

## Business recommendation

Investigate affordability measures alongside loan grades when reviewing higher-risk segments. Compare the cost of missed defaults with false alerts before choosing a model threshold.

The project does not demonstrate reduced defaults, approved lending decisions or production deployment.

## How to inspect the work

1. Review the notebook and included raw and analysis CSV files.
2. Open the PBIX in Power BI Desktop and update data-source paths if needed.
3. For the notebook, install pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost and Jupyter.
4. Replace the Colab-specific data path with the included Dataset path before running.

## Technical limitations and next steps

- Split the data before fitting imputation and other learned preprocessing.
- Preserve missing employment-length values for explicit handling instead of excluding them accidentally.
- Review encoding of nominal categories and fix the Logistic Regression convergence warning.
- Use reproducible model seeds and an imbalance-aware evaluation split.
- A balanced Random Forest comparison is not demonstrated in the uploaded notebook.
- The separately created Loan_Income_Ratio column is added after X is defined; the model importance refers to the existing loan_percent_income feature.

These notes describe the current uploaded implementation. They are not claims that the improvements have already been completed.

## Dashboard preview

![Dashboard 1](Dashboard%20Image/Dashboard%201.jpg)

![Dashboard 2](Dashboard%20Image/Dashboard%202.jpg)

## Repository files

- [Credit Risk Analysis- Dashboard.pbix](Credit%20Risk%20Analysis-%20Dashboard.pbix)
- [Credit_Risk_Project.ipynb](Credit_Risk_Project.ipynb)
- [Dataset/credit_risk_analysis.csv](Dataset/credit_risk_analysis.csv)
- [Dataset/credit_risk_dataset.csv](Dataset/credit_risk_dataset.csv)

## Author

**Manish Kumar** — banking professional transitioning into Data Analytics.

[LinkedIn](https://www.linkedin.com/in/manish071096/) · [GitHub](https://github.com/manish-kr0722)

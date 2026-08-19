## Credit Risk Analysis
An end-to-end data analytics project that analyzes loan applicant data to identify patterns in credit risk and default behavior, combining Python-based data cleaning and machine learning with an interactive Power BI dashboard.

# Overview
This project analyzes 32,581 loan applicant records to answer two questions:

# What factors most strongly predict loan default?
Can we build a model that reliably flags high-risk applicants?

The workflow covers data cleaning, exploratory data analysis, classification modeling, and a business-facing Power BI dashboard for exploring the results interactively.
Dataset
# Attribute	Detail
Records	32,581 loan applicants
Columns	12
Target variable	loan_status (0 = no default, 1 = default)

# Data Cleaning
Duplicates removed before imputation, to avoid skewing fill values.
Missing values handled via median imputation:
person_emp_length — ~2.7% missing
loan_int_rate — ~9.6% missing

# Categorical encoding:
loan_grade — ordinal mapping (A=0 ... G=6), preserving its natural risk order
cb_person_default_on_file — label encoded (binary)
person_home_ownership, loan_intent — one-hot encoded (nominal, no inherent order)
Modeling

# A Random Forest Classifier was trained to predict loan_status.

Class weighting was tested (class_weight='balanced') to address the ~4:1 class imbalance between non-default and default cases. It did not meaningfully improve minority-class recall for this model, so the baseline (unweighted) Random Forest was kept as the final model. Threshold tuning is noted as a possible next step for future iterations.

The model is highly precise when it predicts default (96%) but misses about 29% of actual defaulters (recall 0.71) — an expected effect of class imbalance, and the main limitation to note when interpreting results.

Key finding: loan-to-income ratio was the single strongest predictor of default — outweighing even the lender-assigned loan grade — suggesting affordability metrics carry more predictive signal than categorical risk grades alone.

## Power BI Dashboard ##

An interactive dashboard was built to explore the same findings visually, with slicers for Loan Grade, Home Ownership, Loan Intent, and Loan Status.

# KPI cards:

Total Applicants: 32K
Total Loan Amount: $304.68M
Avg Interest Rate: 11.05%
Default Rate %: 21.59%

# Visuals:

Default Rate % by Loan Grade — shows a near-linear increase from Grade A (9.56%) to Grade G (98.44%)
Default Rate % by Home Ownership — Other and Rent categories show the highest default rates (~31%)
Total Loan Amount by Loan Purpose
Default Rate % by Age Group — a dip through mid-age brackets, rising sharply again at 50+

# Key Insights (from dashboard):

Default risk increases significantly from Grade A to Grade G
Grade D–G show considerably higher default rates than Grade A–C
The 50+ age group has the highest default rate
Others and Rent home ownership categories show the highest default rates

# Tools Used
Python: Pandas, NumPy, scikit-learn, Matplotlib, Seaborn
Power BI: Power Query, DAX, Interactive Dashboards

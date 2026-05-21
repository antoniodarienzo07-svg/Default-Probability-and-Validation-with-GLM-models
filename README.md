# Credit Risk Modeling & Default Probability Estimation

## Overview
This repository contains the final project for the **Risk Management and Capital Requirements** course. The primary objective is to estimate the **Probability of Default (PD)** for mortgage borrowers using Generalized Linear Models (logit/probit). The project implements advanced banking regulatory frameworks, evaluating risk within the **Vasicek model** and comparing **Point-in-Time (PIT)** and **Through-the-Cycle (TTC)** methodologies.

## Dataset
The analysis leverages the "Loan Approval Prediction" dataset from Kaggle, based on Dream Housing Finance. Originally designed for automated loan eligibility, the data has been adapted for a credit risk modeling framework focused on residential home loans. 

**Key Features Include:**
- **Borrower Demographics:** Gender, Marital Status, Dependents, Education, Self-Employment.
- **Loan Details:** Loan Amount, Loan Term, Property Area.
- **Financial & Macroeconomic Metrics:** Applicant/Co-applicant Income, Credit History, Eurozone Inflation Rate, and GDP Growth.

## Methodology
### 1. Data Preprocessing & Aggregation
- **Feature Engineering:** Consolidated applicant and co-applicant incomes into a `TotalIncome` variable, and mapped the loan status to binary default flags (1 = Default, 0 = No Default).
- **Time-Series Smoothing:** Aggregated daily observations into monthly cohorts to resolve numerical instability and stabilize the empirical default rate.
- **Data Splitting:** Performed a stratified 80/20 train-test split based on default status to ensure a balanced evaluation.

### 2. Predictive Modeling (GLM)
- **Logit & Probit Models:** Developed Generalized Linear Models (GLMs) using the binomial family and Logit/Probit link functions to estimate PD.
- **Feature Selection:** Identified statistically significant predictors using p-value evaluation, selecting features such as Credit History, Marital Status, and Property Area.
- **Interaction Effects:** Explored interaction terms (e.g., `LoanAmount * Credit_History`) to capture nuanced risk dynamics, demonstrating how loan amount risk varies based on prior credit history.

### 3. Capital Requirements & Vasicek Framework
- **Point-in-Time (PIT):** Formulated estimates that are cyclical and highly responsive to current macroeconomic conditions.
- **Through-the-Cycle (TTC):** Built a stable, long-term assessment of borrower creditworthiness by excluding time-varying features, as preferred by regulators for capital adequacy.
- **Validation:** Assessed model fit and calibration using validation test statistics across the monthly aggregated time horizon.

## Technologies Used
- **Python 3**
- **Statistical Modeling:** `statsmodels` (GLM, formula API), `scipy`
- **Data Manipulation & ML:** `pandas`, `numpy`, `scikit-learn`
- **Visualization:** `matplotlib`

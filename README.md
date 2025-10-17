# DA5401 A6 — Imputation via Regression

### Course
**DA5401: Data Analysis and Computation Techniques**

### Assignment Title
**Imputation via Regression (Handling Missing Data)**

### Dataset
**UCI Credit Card Default Clients Dataset**  
File used: `UCI_Credit_Card_revised.csv`

---

## 📘 Overview

This assignment demonstrates how to **detect, simulate, and handle missing data** using multiple **imputation strategies**.  
The focus is on comparing regression-based imputations (Linear and KNN) against simpler or naïve approaches.

We introduce **MAR (Missing At Random)** values in a few numeric columns, apply different imputation methods, and evaluate their downstream impact on a **classification model** predicting **default payment next month**.

---

## 🎯 Objectives

1. Load and explore the UCI Credit Card dataset.  
2. Artificially introduce MAR (Missing At Random) values in selected numeric columns.  
3. Apply and compare multiple imputation strategies:
   - **Model A:** Median Imputation (Baseline)
   - **Model B:** Linear Regression Imputation
   - **Model C:** KNN Regression Imputation
   - **Model D:** Listwise Deletion  
4. Train a **Logistic Regression classifier** on each imputed dataset.  
5. Compare model performance using **Accuracy**, **Precision**, **Recall**, and **F1-score**.  
6. Provide a plausible story and interpretation of findings.

---

## 🧩 Methodology Summary

| Step | Description |
|------|--------------|
| **1. Load Data** | The revised UCI Credit Card dataset is loaded into a pandas DataFrame. |
| **2. Identify Target** | Automatically detect the dependent variable (`default payment next month` or similar variants). |
| **3. Inject MAR Missingness** | Randomly introduce 6–10% missing values in 2–3 numeric columns. Missingness depends on an observed driver column (e.g., `PAY_0` or `LIMIT_BAL`). |
| **4. Imputation Strategies** | Perform Median, Linear Regression, and KNN Regression imputations. Also test listwise deletion for comparison. |
| **5. Train/Test Split** | 75% train / 25% test split, stratified on the target. |
| **6. Classification Model** | Logistic Regression (standardized inputs). |
| **7. Evaluation Metrics** | Compare accuracy and F1-scores (macro, weighted). |
| **8. Visualization** | Plot Weighted F1 by strategy to illustrate performance differences. |

---

## 📊 Key Findings

- **Median Imputation** serves as a strong, quick baseline.  
- **Linear Regression Imputation** works well when relationships between predictors and the imputed column are approximately linear.  
- **KNN Imputation** can outperform Linear Regression when local or non-linear dependencies exist.  
- **Listwise Deletion** often reduces sample size and biases estimates when data are MAR.  

**Conclusion:**  
Regression-based imputations (Linear or KNN) generally preserve data structure better than deletion or static fillers. The *best method* depends on the nature of the relationship between predictors and the missing variable.

---

## 🧠 Conceptual Takeaways

- MAR (Missing At Random) means that the probability of missingness depends on other observed variables, not on the missing value itself.  
- Deletion methods are simple but risky under MAR.  
- Regression imputations **borrow information** from correlated predictors to fill missing data more realistically.  
- Always assess model stability post-imputation — the impact is often non-trivial.

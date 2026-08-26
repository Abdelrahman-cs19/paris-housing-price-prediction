# 📊 Customer Churn Prediction App

An end-to-end Machine Learning web application designed to identify customers at high risk of churning. Built with **scikit-learn**, **pandas**, and **Streamlit**, this project processes customer demographic, financial, and service usage data to deliver real-time risk scoring, actionable feature importance, and interactive user predictions.

---

## 📌 Overview

Customer retention is critical for subscription-based businesses. This repository contains the complete pipeline for data preprocessing, outlier detection, model training, hyperparameter optimization, and cloud deployment. 

The interactive front-end allows business users to input individual customer attributes or upload batch datasets to get immediate churn probabilities and key driving risk factors.

---

## 🛠️ Tech Stack & Key Features

* **Data Handling & Preprocessing:** Pandas, NumPy, Scikit-Learn (ColumnTransformer, OneHotEncoder, StandardScaler, SimpleImputer)
* **Outlier Detection & Imbalance Handling:** Isolation Forest, SMOTE / Class Weighting
* **Machine Learning Algorithms:** Random Forest, XGBoost, LightGBM, Logistic Regression
* **Deployment & Web Framework:** Streamlit, Streamlit Community Cloud
* **Serialization & Versioning:** Joblib, Git LFS

---

## 🏎️ Model Performance & Comparisons

Multiple algorithms were evaluated using 5-fold cross-validation on the test split. Because predicting potential churners (false negatives) is more costly than sending retention offers to loyal customers (false positives), **Recall** and **ROC-AUC** were chosen as primary optimization metrics alongside **F1-Score**.

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **XGBoost Classifier (Tuned)** 🏆 | **0.842** | **0.781** | **0.814** | **0.797** | **0.891** |
| LightGBM Classifier | 0.835 | 0.768 | 0.802 | 0.785 | 0.884 |
| Random Forest (Tuned) | 0.828 | 0.755 | 0.789 | 0.771 | 0.876 |
| Logistic Regression (Baseline) | 0.791 | 0.694 | 0.732 | 0.712 | 0.815 |

### 🎯 Key Drivers of Churn (Feature Importance)
1. **Contract Type** (Month-to-month contracts strongly correlate with higher churn)
2. **Tenure** (Newer customers show significantly higher attrition)
3. **Total / Monthly Charges** (Higher bill amounts increase churn probability)
4. **Internet Service Type** (Fiber optic users exhibit distinct churn patterns)

---

## 🚀 Quick Start & Local Setup

### 1. Prerequisites
Ensure you have Python 3.9+ installed.

### 2. Clone the Repository
```bash
git clone [https://github.com/your-username/customer-churn-prediction.git](https://github.com/your-username/customer-churn-prediction.git)
cd customer-churn-prediction

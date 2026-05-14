# 💳 Credit Card Default Prediction — Machine Learning in Python

A machine learning pipeline built in Python to predict credit card payment defaults, developed as part of BUSA3020 Advanced Analytics at Macquarie University. The project covers the full data science workflow from data cleaning and feature engineering through to model training and evaluation.

---

## 📋 Project Overview

Using a dataset of 10,000 credit card customer records, this project preprocesses raw financial and demographic data and trains **Support Vector Classifier (SVC)** models to predict whether a customer will default on their next payment. Two approaches are compared — full-feature SVC and PCA-reduced SVC — to evaluate the trade-off between dimensionality and accuracy.

---

## 🔍 Workflow

**1. Data Loading & Exploration**
- Loaded 10,000 rows from an Excel dataset
- Classified all 24 features as numeric, ordinal, or nominal variables
- Identified and reported missing values across all columns

**2. Data Cleaning & Feature Engineering**
- Imputed missing values using **mean** for numeric features and **mode** for categorical features
- Applied one-hot encoding (`get_dummies`) to nominal variables: `SEX` → `SEX_FEMALE`, `MARRIAGE` → `MARRIAGE_MARRIED`, `MARRIAGE_SINGLE`, `MARRIAGE_OTHER`
- Consolidated undocumented values in `EDUCATION` (0, 5, 6) into a single "other" category

**3. Model Preparation**
- Split data into 75% train / 25% test with stratified sampling (`random_state=3`)
- Standardised all features to mean=0 and variance=1 using `StandardScaler`

**4. Model Training & Evaluation**

| Model | Train Accuracy | Test Accuracy |
|---|---|---|
| SVC (all features, RBF kernel) | 82.31% | 81.44% |
| SVC (2 PCA components, RBF kernel) | 80.12% | 80.37% |

The full-feature SVC outperforms the PCA-reduced model, with both showing consistent train/test accuracy, indicating no significant overfitting.

---

## 🛠️ Built With

- Python 3.11
- `pandas` — data loading, cleaning, feature engineering
- `scikit-learn` — imputation, train/test split, scaling, PCA, SVC, accuracy scoring
- `numpy` — array operations
- Jupyter Notebook

---

## 📁 Project Structure

```
BUSA3020_Assignment1.ipynb          # Full notebook with code and written analysis
assignment_data/
  └── credit_data.xlsx              # Working dataset (10,345 rows, 22.4% default rate)
  └── credit_card_defaults.xlsx     # Raw source dataset (30,000 rows, 22.1% default rate)
```

---

## 🧠 Concepts Demonstrated

- Exploratory data analysis (EDA)
- Variable type classification (numeric, ordinal, nominal)
- Missing value imputation strategies
- One-hot encoding and dummy variable creation
- Train/test splitting with stratification
- Feature standardisation
- Principal Component Analysis (PCA)
- Support Vector Classification (SVC) with RBF kernel
- Model comparison and performance analysis

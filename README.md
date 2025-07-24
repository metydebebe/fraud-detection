# Improved detection of fraud cases for e-commerce and bank transactions

# Task-1 Data Cleaning and Preprocessing

This task handles the initial data cleaning and preprocessing steps necessary for fraud detection. The goal is to prepare a clean, structured dataset for feature engineering and modeling.

## Tasks Completed

Loaded raw datasets

Mapped IP addresses to countries

Converted IP addresses to integer format

Used IP range lookup to identify country of origin

Cleaned data

Removed raw IP address and timestamp columns

One-hot encoded categorical columns: browser, source, sex

Handled class imbalance

Inspected class distribution

Used SMOTE (Synthetic Minority Oversampling Technique) on training set

Exported cleaned data

Saved the processed dataset to data/cleaned_fraud_data.csv

## How to Reproduce

git clone https://github.com/metydebebe/fraud-detection
cd fraud-detection
conda activate fraud-detection

## Output

data/cleaned_fraud_data.csv

# Task 2 - Model Building and Training

## Objective

To build and compare fraud detection models using two different machine learning algorithms on the preprocessed dataset from Task 1.

## Dataset Used

- `cleaned_fraud_df.csv` from Task 1 (based on `Fraud_Data.csv`)

## Steps Performed

### 1. Data Preparation

- Target column: `class`
- Features: All numeric features (categorical columns one-hot encoded)
- Train-test split: 80/20 with stratification to maintain class balance
- Feature scaling applied using `StandardScaler`

### 2. Model Training

Two models were trained on the prepared dataset:

- **Logistic Regression** (`class_weight='balanced'`)
- **Random Forest Classifier** (`n_estimators=100`, `class_weight='balanced'`)

### 3. Model Evaluation

Both models were evaluated using metrics suitable for imbalanced classification:

- **Confusion Matrix**
- **Classification Report**
- **F1 Score**
- **AUC-PR**

#### Results Summary:

| Metric   | Logistic Regression | Random Forest |
| -------- | ------------------- | ------------- |
| F1 Score | 0.6112              | 0.6907        |
| AUC-PR   | 0.4074              | 0.5718        |

> **Conclusion:** Random Forest performed better across all evaluation metrics, especially in handling the imbalanced nature of the dataset. It is selected for further interpretation in Task 3.

### 4. Outputs

- Scaled and labeled training/testing datasets:
  - `data/processed/X_train_task2.csv`
  - `data/processed/X_test_task2.csv`
- Trained model files:
  - `models/logistic_regression_model.pkl`
  - `models/random_forest_model.pkl`

# Task 3 – Model Explainability with SHAP

## Overview

This task focuses on interpreting the best-performing fraud detection model (Random Forest) using SHAP (Shapley Additive explanations). SHAP provides insight into the contribution of each feature to individual predictions and overall model behavior.

## Key Steps

Loaded the trained Random Forest model from Task 2.

Selected a representative sample of test data for explanation.

Computed SHAP values using the TreeExplainer to quantify feature importance for the fraud class.

Generated visualizations:

Local Force Plot: Explains individual prediction contributions for specific instances.

Bar Plot: Highlights average feature importance specifically for the fraud class.

## Files

task3_model_explainability.ipynb – Jupyter notebook with all code and plots.

outputs/force_plot_instance5.html – Saved interactive force plot for a sample transaction.

## How to Run

Ensure the Random Forest model file (random_forest_model.pkl) from Task 2 is in the models/ folder.

Run task3_model_explainability.ipynb to reproduce all SHAP computations and plots.

Visualize saved plots in the outputs/ directory if desired.

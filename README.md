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

# Money Laundering Detection using IBM Transactions Dataset

## Overview

This project aims to detect money laundering activities within financial transactions using machine learning techniques. Utilizing the IBM Transactions for Anti Money Laundering (AML) dataset, we explore patterns and develop classification models to identify suspicious transactions effectively.

## Dataset

The dataset is sourced from [Kaggle](https://www.kaggle.com/datasets/ealtman2019/ibm-transactions-for-anti-money-laundering-aml) and contains detailed transaction records, including indicators of money laundering activities. 

- **HI-Small_Trans.csv**: Higher illicit ratio, small transactions


### Data Dictionary

| Attribute          | Description                                                       |
|--------------------|-------------------------------------------------------------------|
| Timestamp          | The date and time when the transaction occurred                   |
| From Bank          | An identifier for the bank from which the transaction originated  |
| Account            | The account number from which the transaction originated          |
| To Bank            | An identifier for the bank to which the transaction was sent      |
| Account.1          | The account number to which the transaction was sent              |
| Amount Received    | The amount of money received in the transaction                   |
| Receiving Currency | The currency in which the amount was received                     |
| Amount Paid        | The amount of money paid in the transaction                       |
| Payment Currency   | The currency in which the amount was paid                         |
| Payment Format     | The format or type of payment made in the transaction (e.g., Reinvestment) |
| Is Laundering      | Indicator of whether the transaction is identified as money laundering (0 = No, 1 = Yes) |

## Exploratory Data Analysis (EDA)

The EDA aims to uncover patterns, relationships, and anomalies within the dataset. Key steps include:

1. **Data Overview**: Check for missing values and summary statistics.
2. **Data Shape, Type & Structure**: Identify data types and structure.
3. **Data Distribution & Pattern**: Analyze distributions using KDE plots, histograms, bar plots, and box plots.
4. **Correlation Analysis**: Use heatmaps to identify correlations between variables.
5. **Scatter Plots**: Examine the distribution of laundering vs non-laundering transactions over time and amounts.

### Key Findings

- **Currency**: USD and Euro are the most common currencies.
- **Payment Channels**: Credit cards and cheques are popular for legitimate transactions, while ACH is common for laundering.
- **Outliers**: High-value transactions appear in both laundering and non-laundering activities.
- **Weak Correlations**: Laundering indicator has weak correlations with other variables.

## Machine Learning Models

Several classification models were tested to detect money laundering:

1. **Logistic Regression**
2. **Decision Tree**
3. **LightGBM**

### Results Summary

- **Logistic Regression with SMOTE** performed the best, balancing recall and F1-score for the minority class (Class 1). 
- **Decision Tree** and **LightGBM** showed lower performance in comparison.

| Model                             | Precision (Class 1) | Recall (Class 1) | F1-Score (Class 1) | Accuracy |
|-----------------------------------|---------------------|------------------|--------------------|----------|
| Logistic Regression               | 0.70                | 0.09             | 0.16               | 1.00     |
| Logistic Regression with SMOTE    | 0.15                | 0.43             | 0.23               | 1.00     |
| Logistic Regression with Tuning   | 0.17                | 0.41             | 0.24               | 1.00     |
| Decision Tree                     | 0.29                | 0.25             | 0.27               | 1.00     |
| Decision Tree with SMOTE          | 0.15                | 0.33             | 0.20               | 1.00     |
| Decision Tree with Tuning         | 0.01                | 0.57             | 0.02               | 0.95     |
| LightGBM                          | 0.47                | 0.20             | 0.28               | 1.00     |
| LightGBM with SMOTE               | 0.15                | 0.33             | 0.20               | 1.00     |
| LightGBM with Tuning              | 0.09                | 0.28             | 0.14               | 1.00     |


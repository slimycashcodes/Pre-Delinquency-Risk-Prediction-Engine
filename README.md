# Pre-Delinquency-Risk-Prediction-Engine

## 📝 Description

The Pre-Delinquency Risk Prediction Engine is a sophisticated, proactive analytics platform designed to safeguard financial institutions from credit losses. By continuously monitoring and analyzing customer financial behavior, the engine identifies subtle early stress signals that often precede a default. This early-warning system empowers banks to transition from reactive recovery to proactive intervention, allowing them to engage with at-risk clients and implement mitigation strategies well before delinquency occurs. Through data-driven insights, the engine enhances portfolio stability and optimizes risk management processes.


## 🧠 Project Overview

This engine **creates synthetic financial datasets** to model customer behavior for use in pre-delinquency analysis.  
It simulates three primary data sources:

1. **Customer Profiles**
2. **Loan Records**
3. **Credit Card + Transactions History** :contentReference[oaicite:1]{index=1}

---

## 📊 Data Generation Logic

### 1. Customer Profiles
- Simulate `NUM_CUSTOMERS` customers
- Each has:
  - Unique ID
  - Age
  - Monthly income
  - Base risk score (derived from income & age randomness)
- Purpose: baseline risk attribute for downstream behavior modeling. :contentReference[oaicite:2]{index=2}

### 2. Loan Data
- Loan amount computed using monthly income.
- Loan approval based on risk score criteria.
- Default flag derived from a combination of:
  - Base risk score
  - Random noise (adds variability for realism) :contentReference[oaicite:3]{index=3}

### 3. Credit Card & Transactions
- For each customer:
  - Assign credit limit as multiple of income.
  - Random utilization rate (0–1).
  - Classification of next-month credit default if utilization is very high and risk score is poor.
  - Daily transaction simulation over a fixed period:
    - Monthly salary credits
    - Random spend debits
    - Balance tracking
- Transactions include both **credit** and **debit** events with running balances per customer. :contentReference[oaicite:4]{index=4}

---

## 📁 Output Datasets

The script generates these CSV files:

- `customers.csv` — profile + base risk score
- `loan_data.csv` — loan details + default label
- `credit_card_data.csv` — credit limits, utilization, next-month default
- `transactions_data.csv` — per-day transaction logs

These datasets support training ML models for **predicting early signs of financial stress**. :contentReference[oaicite:5]{index=5}

---

## 🛠️ Technologies

- Python 🐍
- pandas, numpy
- Data simulation logic

---

## 📌 Ideal Use Cases

- Generate training data for credit risk models
- Test early delinquency prediction pipelines
- Analyze behavior signals before default

---

Made by Rahul Suresh (and cup of coffee ☕ 😅)

# 🏦 End-to-End Bank Fraud Detection Lakehouse

![Databricks](https://shields.io)
![PySpark](https://shields.io)
![Delta Lake](https://shields.io)
![Python](https://shields.io)
![Scikit-Learn](https://shields.io)

## 📌 Project Overview
This project implements an **End-to-End Data Engineering & Machine Learning pipeline** designed to detect fraudulent banking transactions. Built on **Databricks** following the **Medallion Lakehouse Architecture (Bronze, Silver, Gold)**, the pipeline ingests raw transaction logs, enforces automated **Data Quality** rules, extracts behavioral indicators via **Spark SQL**, and trains a class-balanced **Random Forest** model using **SMOTE**.

> **Status:** *Active Development (Finalizing Gold SQL Aggregations & ML Evaluation)*

---

## 🏗️ Lakehouse Architecture

```text
[ Raw Transactions CSV ] 
          │
          ▼  (1. Ingestion - Unity Catalog Volumes)
[ 🥉 BRONZE LAYER ]  ──► Raw Delta Lake Table (Schema Enforcement & ACID)
          │
          ▼  (2. Cleaning & Data Quality - PySpark Lazy Evaluation)
[ 🥈 SILVER LAYER ]  ──► Deduplicated, Null-Handled & Validated Transactions
          │
          ▼  (3. Feature Engineering - Spark SQL & Window Functions)
[ 🥇 GOLD LAYER ]    ──► Aggregated Behavioral & Risk Indicators
          │
          ▼  (4. Predictive Modeling - Scikit-Learn & Imbalanced-Learn)
[ 🤖 ML PIPELINE ]   ──► Train/Test Split -> SMOTE (Train Only) -> Random Forest
```

---

## 🚀 Key Technical Highlights

### 1. Data Engineering (Medallion Architecture)
* **Bronze Layer (`01_bronze_ingestion`):** Ingests raw banking transaction data from Databricks Unity Catalog Volumes and persists it into **Delta Lake** format for reliability and versioning.
* **Silver Layer (`02_silver_cleaning_dq`):** Cleans records (deduplication, missing value imputation) and applies automated **Data Quality Checks** (ensuring non-negative amounts and valid target labels), leveraging Spark's **Lazy Evaluation** for optimized query execution.
* **Gold Layer (`03_gold_sql_transformations`):** Uses **Spark SQL** (*Window Functions*, rolling averages, and transaction frequency metrics) to build high-value features for downstream analytics and AI.

### 2. Machine Learning & Imbalanced Data (`04_ml_fraud_detection`)
* **Class Imbalance Resolution:** Addresses severe fraud class rarity (~1.5%) by applying **SMOTE** (*Synthetic Minority Over-sampling Technique*) strictly on the training set to prevent data leakage.
* **Model Training & Tuning:** Trains and tunes a **Random Forest Classifier**, optimizing for **Recall** and **F1-Score** to minimize undetected fraudulent transactions.

---

## 📂 Repository Structure

```text
fraud-detection-pipeline/
├── notebooks/
│   ├── 01_bronze_ingestion.py          # Raw CSV to Delta Lake ingestion
│   ├── 02_silver_cleaning_dq.py        # PySpark cleaning & Data Quality rules
│   ├── 03_gold_sql_transformations.sql # Spark SQL feature engineering
│   └── 04_ml_fraud_detection.py        # SMOTE resampling & Random Forest model
├── images/
│   └── architecture_diagram.png        # End-to-End Lakehouse schema
└── README.md
```

---

## 🛠️ Tech Stack
* **Platform & Storage:** Databricks (Free Edition), Unity Catalog Volumes, Delta Lake
* **Big Data Processing:** Apache Spark (PySpark, Spark SQL)
* **Machine Learning:** Python, Pandas, NumPy, Scikit-learn, Imbalanced-learn (SMOTE)
* **Version Control:** Git, GitHub

---

## 👤 Author
**Hasna Ouafegha**  
*Master of Excellence in Data Analytics & Artificial Intelligence*  
🔗 [GitHub](https://github.com) | 📧 hasnaouafegha08@gmail.com

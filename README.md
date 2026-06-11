# DataScience_MachineLearning----End-To-End_ModelBuilding----Predict-Credit-Card-Consumption_project
# Bank Credit Card Consumption Predictive Modeling Case Study

This repository contains an advanced predictive data science case study focused on predicting **Credit Card Consumption (`cc_cons`)** for a banking institution's customer base. By integrating diverse consumer streams (demographics, debit/credit interaction frequencies, transaction histories, and active asset lines), this project builds and optimizes high-performance regressor models to forecast future credit card expenditures.

---

## 📂 Multi-Source Dataset Architecture

The project processes user profiles distributed across **3 separate relational data files** mapped uniformly by a common primary identifier (`ID`).

### Dataset Overview

| File Name | Domain Matrix | Key Captured Features | Dimensions |
| :--- | :--- | :--- | :--- |
| `CustomerDemographics.xlsx - CustomerDemographics.csv` | Personal & Institutional Attributes | `account_type`, `gender`, `age`, `Income`, `Emp_Tenure_Years`, `Tenure_with_Bank`, `NetBanking_Flag` | Customer Static States |
| `CustomerBehaviorData.xlsx - Train.csv` | Monthly Transaction Footprints | Monthly Credit/Debit limits, spending behaviors across Apr/May/Jun (`cc_cons_apr`, `dc_cons_may`), dynamic transaction counters, investments, active loans | Behavioral Time-slice |
| `CreditConsumptionData.xlsx - Train.csv` | Model Target Repository | Unique `ID` and corresponding actual Credit Card Consumption target value (`cc_cons`) | Ground Truth Target Labels |

---

## ⚙️ Core Data Engineering & Cleaning Pipelines

The pipeline steps configured inside `Capstone_Case_Study.ipynb` include:
1. **Dynamic Dataset Merging:** Combining Demographics, Financial Behavior, and Target features seamlessly on the relational key (`ID`).
2. **Whitespace Stripping:** Automatically fixing column header naming issues by cleaning unexpected hidden blanks or strings:
   ```python
   df.columns = df.columns.str.strip()

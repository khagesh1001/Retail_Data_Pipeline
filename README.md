# Retail_Data_Pipeline
## Project Overview
This project implements an end-to-end retail data pipeline using Databricks, PySpark, SQL, and Power BI/Databricks dashboards.  
It follows the Medallion Architecture (Bronze, Silver, Gold) for batch (and stream processing: currently in development) of retail transactional data.  

The pipeline enables data cleaning, transformation, aggregation, and business analytics, as well as predictive modeling for key business metrics.

---

## Dataset: The project uses the "Online Retail II dataset" from [UCI Machine Learning Repository / Kaggle](https://www.kaggle.com/datasets/mashlyn/online-retail-ii).

## Project Structure

| Notebook |  Purpose |
|----------|---------|
| `01_bronze_ingestion.ipynb` | Read raw transactional data into Bronze layer |
| `02_silver_layer.ipynb` | Clean, format, and transform data to Silver layer |
| `03_gold_layer.ipynb` | Aggregate data to Gold layer for business metrics |
| `04_Analytics.ipynb` | Predict order value, quantity, and monthly revenue using PySpark ML |
| `05_Regression_Analysis.ipynb` | Build Databricks dashboards for KPIs, customer, product, and revenue insights |

Other folders:
- `data/` → sample dataset  
- `images/` → related screenshots 

---

## Approach

## 1. Data Ingestion (Bronze Layer)
- Read raw CSV/Excel from Kaggle
- Store in Delta tables for batch processing
- Retain original schema for auditing

## 2. Data Cleaning & Transformation (Silver Layer)
- Remove nulls and invalid records
- Standardize text (trim, uppercase, remove special characters)
- Create derived fields:
  - `order_value = quantity * price`
  - `year`, `month` from `InvoiceDate`

## 3. Aggregation (Gold Layer)
- Customer metrics:
  - Total spend, total orders, average order value
- Product metrics:
  - Total revenue, total quantity sold
- Monthly revenue trends

## 4. Predictive Modeling
- Regression models in PySpark:
  - Predict **order value** per transaction
  - Predict **quantity purchased** (demand)
  - Predict **monthly revenue** (trend forecasting)

## 5. Analytics & Dashboard
- Power BI / Databricks dashboards
---


## How to Run
1. Upload notebooks to **Databricks** workspace
2. Set up Delta tables for Bronze, Silver, Gold layers
3. Run notebooks sequentially:
   1. `01_bronze_ingestion.ipynb`
   2. `02_silver_layer.ipynb`
   3. `03_gold_layer.ipynb`
   4. `04_Analytics.ipynb`
   5. `05_Regression_Analysis.ipynb`
4. View dashboards in Databricks or connect Power BI

---
## Tools & Technologies
- **Databricks** (PySpark, SQL)
- **Delta Lake** (Bronze, Silver, Gold layers)
- **PySpark ML** (Regression)
- **Power BI / Databricks dashboards**

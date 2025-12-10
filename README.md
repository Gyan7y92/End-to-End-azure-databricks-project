# End-to-End Retail Data Pipeline Using Azure Data Factory, ADLS, Databricks & Power BI

**Project Overview**

This project demonstrates how to build a complete end-to-end data engineering pipeline for a retail client using Azure cloud services.
The solution integrates multiple data sources, performs ETL/ELT, applies the Medallion Architecture (Bronze → Silver → Gold), and exposes analytics through Power BI.

**Business Requirements**

Build an end-to-end scalable data pipeline for retail analytics.
Ingest data from multiple data sources into Azure Data Lake Store (ADLS).
Transaction data is stored in Azure SQL Database.
Product and Store data is also stored in Azure SQL Database.
Customer data is received from an External REST API (JSON).
Transform and cleanse data using Azure Databricks (PySpark).
Load curated business-level data into Gold Layer for reporting.
Build dashboards in Power BI for business decision-making.

**Solution Architecture (Step-by-Step)**
1. Data Sources
Azure SQL DB
Transaction Table
Product Table
Store Table

REST API (JSON)
Customer Data
3. Ingestion Layer – Azure Data Factory (ADF)
ADF is used to orchestrate ingestion using:
Copy Activity
REST API Linked Service
Azure SQL linked services
Pipelines scheduled via triggers
ADF loads raw data into ADLS Bronze Layer.

4. Storage Layer – Azure Data Lake Storage (ADLS Gen2)

Data is stored in hierarchical structure:

/raw/transaction/  
/raw/product/  
/raw/store/  
/raw/customer/  

All records are stored as-is for audit and reprocessing.

4. Processing Layer – Azure Databricks

**Databricks performs:**

Incremental ingestion

Data cleaning

Null handling

Schema enforcement

Joins across customer, store, and product

Creation of Silver and Gold curated tables

**Medallion Architecture**

Bronze Layer: Raw ingested data (ADLS).

Silver Layer: Cleaned, validated, conformed data.

Gold Layer: Business-ready aggregated data for reporting.

5. Transformation Logic 
Data cleaning & validation
Convert JSON API payload into tabular format
Create unified customer dimension
Create fact table with transaction-product-store mapping
Optimize PySpark jobs using partitioning and caching

6. Reporting Layer – Power BI

Power BI connects to Gold Layer to build dashboards such as:

Sales Analysis
Store Performance
Product Performance
Customer Segmentation

Dataflows and scheduled refresh are configured for automation.

# Folder structure

├── data_ingestion  
│   ├── adf_pipelines  
│   ├── linked_services  
│   ├── datasets  
│
├── databricks_notebooks  
│   ├── bronze_ingestion  
│   ├── silver_transformation  
│   ├── gold_aggregation  
│
├── powerbi_reports  
│   ├── dashboards.pbix  
│
├── docs  
│   ├── architecture.png  
│   ├── ERD.png  
│
└── README.md

**Outcome**
A fully automated, scalable, production-ready retail data pipeline enabling fast and reliable analytics for business decision-making.
# Author

**Gyan Singh**
Azure Data Engineer | Data Engineering | ADF | Databricks | PySpark | Azure SQL



# AdventureWorks_Analysis-Azure-Data-Engineering
Data Engineering Project - Analyze Microsoft's Adventures Work data from End to End

## Table of Contents
1. [Project Overview](#project-overview)
2. [Project Architecture](#project-architecture)
3. [Resources Used](#resources-used)
4. [Data Storage Strategy](#data-storage-strategy)
5. [Data Ingestion](#data-ingestion)
6. [Data Transformation](#data-transformation)
7. [Data Analytics](#data-analytics)
8. [Data Visualization](#data-visualization)
9. [Security & Authentication](#security--authentication)
10. [Conclusion](#conclusion)

---
## Project Overview
This project demonstrates an end-to-end data pipeline implementation using Microsoft Azure services with AdventureWorks data. The primary objectives include:
- Ingesting on-premise data to Azure Data Lake Storage (ADLS)
- Implementing a medallion architecture for data organization
- Performing data transformations using Azure Data Factory (ADF) and Azure Databricks
- Conducting analytics using Azure Synapse Analytics
- Visualizing insights using Power BI

### Image 1: On-Premise Data
- Shows the original data stored in on-premise storage.
- **Image 1.1:** Displays the contents of the on-premise data.

---
## Project Architecture

### Image 2: Resource Group
- The necessary resources are created under the Resource Group: **"harsha-Data_Engineering-Project"**.
- This includes:
  - Azure Data Factory (ADF)
  - Azure Databricks
  - Azure Data Lake Storage (ADLS)
  - Azure Key Vault
  - Azure Synapse Analytics

### Image 3: SHIR to On-Premise Connection
- **Image 3.1:** Shows the steps to connect Self-Hosted Integration Runtime (SHIR) with on-premise data.

---
## Data Storage Strategy

### Image 4: Storage Medallion
- ADLS follows a **Medallion Architecture**:
  - **Bronze Layer:** Stores raw source data (CSV format)
  - **Silver Layer:** Stores cleansed and structured data (Parquet format)
  - **Gold Layer:** Stores analytics-ready, aggregated data (Parquet format)

---
## Data Ingestion

### Image 5: Data Ingestion from On-Prem to ADF
- AdventureWorks data is imported into the **bronze container** in ADLS using ADF after configuring SHIR.

### Image 6: Data Ingested to ADLS in Bronze Container
- **Image 6.1:** Shows the ingested CSV files stored in the bronze container.

---
## Data Transformation

### Image 7: Data Transformation from Bronze to Silver
- **Image 7.1:** Shows the transformation of data from bronze (CSV) to silver (Parquet) using Azure Databricks.

### Image 8: Data Transformation from Silver to Gold
- **Image 8.1:** Shows the transformation of data from silver (Parquet) to gold (Parquet), optimizing it for analytics.

### Image 9: Transformation Pipeline
- A pipeline named **"Transformation Pipeline"** automates the process of moving and transforming data between these layers.

---
## Data Analytics

### Image 10: Synapse Analytics Pipeline
- A **"Synapse Analytics Pipeline"** is created to analyze the transformed data in the gold layer.
- **Image 10.1:** Shows the SQL script used to create views of all tables in the **GoldDB**.

---
## Data Visualization

### Image 11: Data Imported to Power BI
- The processed data from **GoldDB** is imported into Power BI for reporting.

### Image 12: Power BI Report Generated
- Power BI dashboards are created using the cleaned and aggregated data from Azure Synapse Analytics.

---
## Security & Authentication
- All sensitive information, including authentication keys, is securely stored in **Azure Key Vault** to manage access and credentials.

---
## Conclusion
This project successfully demonstrates an end-to-end data engineering workflow in Azure. It covers data ingestion, transformation, storage, analytics, and visualization, leveraging Azure's robust cloud capabilities. By following a structured medallion architecture and integrating Azure services efficiently, this project provides a scalable and secure data pipeline for enterprise use cases.


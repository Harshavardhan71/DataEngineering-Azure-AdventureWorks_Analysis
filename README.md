# Azure End-to-End Data Engineering Project using AdventureWorks Data
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

The project starts with the on-premise data, as shown in `on premise data`, where the dataset exists in local storage. The contents of the dataset can be seen in `contents of the on premise data`.
[on premise data](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/1.on%20premise%20data.jpg)  
[contents of the on premise data](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/1.1.contents%20of%20on%20premise%20data.jpg)  

---
## Project Architecture
[Project Architecture](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/architectur.png)  
The necessary resources are created under the Resource Group: **"harsha-Data_Engineering-Project"**. This includes:
  - Azure Data Factory (ADF)
  - Azure Databricks
  - Azure Data Lake Storage (ADLS)
  - Azure Key Vault
  - Azure Synapse Analytics

The setup of these resources is illustrated in `resource group`.

[resource group](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/2.resource%20group.jpg)  
A Self-Hosted Integration Runtime (SHIR) is used to establish a connection between the on-premise data source and Azure services. The connection process is detailed in `SHIR to on Premise`, which includes steps depicted in `contains 3 images`.

[SHIR to on Premise](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/3.SHIR%20to%20on%20premise.jpg)  
[SHIR to on Premise_1](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/3.1.SHIR%20to%20on%20premise.jpg)  
[SHIR to on Premise_2](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/3.2.SHIR%20to%20on%20premise.jpg)  

---
## Data Storage Strategy

ADLS follows a **Medallion Architecture**, as depicted in `Storage Medallion`. This architecture consists of three storage layers:
  - **Bronze Layer:** Stores raw source data (CSV format)
  - **Silver Layer:** Stores cleansed and structured data (Parquet format)
  - **Gold Layer:** Stores analytics-ready, aggregated data (Parquet format)

[Storage Medallion](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/4.storage%20medalion.jpg)  

---
## Data Ingestion

AdventureWorks data is imported into the **bronze container** in ADLS using ADF after configuring SHIR. The ingestion process is demonstrated in `data ingestion from on prem to adf`.

[data ingestion from on prem to adf](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/5.data%20ingestion%20from%20on%20prem%20to%20adf.jpg) 
[data ingestion pipeline from on prem to adf](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/5.data%20ingestion%20pipeline%20from%20on%20prem%20to%20adf.jpg)  
Once ingested, the data resides in ADLS under the bronze container, as seen in `data ingested to adls in bronze container`, with further details in `contains 2 images`.

[data ingested to adls in bronze container](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/6.data%20ingested%20to%20adls%20in%20broze%20container.jpg) 
[data ingested to adls in bronze container](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/6.1.data%20ingested%20to%20adls%20in%20broze%20container.jpg)  

---
## Data Transformation

The data is transformed from bronze (CSV) to silver (Parquet) using Azure Databricks, as shown in `data transformation from bronze to silver`. The transformation steps are depicted in `contains 2 images`.

[data transformation from bronze to silver](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/7.data%20transformation%20from%20bronze%20to%20silver.jpg)  
[data transformation from bronze to silver](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/7.1.data%20transformation%20from%20bronze%20to%20silver.jpg)  
Further transformation occurs from silver (Parquet) to gold (Parquet) to optimize it for analytics, as detailed in `data transformation from silver to gold`, with additional visuals in `contains 2 images`.

[data transformation from silver to gold](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/8.data%20transformation%20from%20silver%20to%20%20gold.jpg)  
[data transformation from silver to gold](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/8.1.data%20transformation%20from%20silver%20to%20%20gold.jpg)  
To automate this entire process, a dedicated **Transformation Pipeline** is created in ADF, as shown in `transformation pipeline`.

[transformation pipeline](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/9.transformation%20pipeline.jpg)  

---
## Data Analytics

A **Synapse Analytics Pipeline** is built to perform analytics on the transformed data stored in the gold layer. The implementation of this pipeline is detailed in `synapse analytics pipeline`. The SQL script used to create views of all tables for **GoldDB** is captured in `Script to create view of all tables for goldDB`.

[synapse analytics pipeline](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/10.synapse%20analytics%20pipeline.jpg)  
[Script to create view of all tables for goldDB](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/10.1.script%20to%20create%20view%20of%20all%20tables%20for%20gold_DB.jpg)  

---
## Data Visualization

The processed data from **GoldDB** is imported into Power BI for reporting, as shown in `data imported to powerbi`.

[data imported to powerbi](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/11.data%20imported%20to%20powerbi.jpg)  
Power BI dashboards are then generated using the cleaned and aggregated data from Azure Synapse Analytics, as illustrated in `power bi report generated`.

[power bi report generated](https://github.com/Harshavardhan71/AdventureWorks_Analysis-Azure-Data-Engineering/blob/main/ss%20of%20project/12.powerbi%20report%20genrated.jpg)  

---
## Security & Authentication
All sensitive information, including authentication keys, is securely stored in **Azure Key Vault** to manage access and credentials.

---
## Conclusion
This project successfully demonstrates an end-to-end data engineering workflow in Azure. It covers data ingestion, transformation, storage, analytics, and visualization, leveraging Azure's robust cloud capabilities. By following a structured medallion architecture and integrating Azure services efficiently, this project provides a scalable and secure data pipeline for enterprise use cases.

# Azure End-to-End Data Engineering Real-Time Project
This project is a data engineering pipeline solution to a made-up business problem, created to aid in my learning and understanding of data pipelining.

## Project Overview
This project addresses a critical business need by building a comprehensive data pipeline on Azure. The goal is to extract Flight data from Flight Radar, for 787-X airliners to on-premises SQL database, transform it in the cloud, and generate actionable insights through a Power BI dashboard. The dashboard will highlight key performance indicators (KPIs) related to flight hours and cycles, allowing stakeholders to retrieve this information in streamline mode.

![399150923-bdadd2e0-89be-4683-b53b-fe331be6f6bf](https://github.com/user-attachments/assets/1312d397-be03-46f8-af20-1be2919b12a3)

## Business Requirements
The business has identified a gap in missing information of Airliners flight hours, specifically from Boeing 787-X airliners, since this model is currently being manufactured and delivery to customers and not necessarily partnership with customer is made to retrieve this data from official’s channels, and how it influences product purchases. The key requirements include:

1. Flight data for 787-X airliners aircraft: A dashboard showing summarize data for the total hours, cycles, Airline ICAO code and last location by tail number.
2. Data Filtering: Ability to filter the data by product Airline, Tail Number, and date.
3. User-Friendly Interface: Stakeholders should have access to an easy-to-use interface for retrieving data.

## Solution Overview
To meet these requirements, the solution is broken down into the following components:

1. Data Ingestion:
  - Extract aircraft data from an on-premises SQL database.
  - Load the data into Azure Data Lake Storage (ADLS) using Azure Data Factory (ADF).

2. Data Transformation:

  - Use Azure Databricks to clean and transform the data.
  - Organize the data into Bronze, Silver, and Gold layers for raw, cleansed, and aggregated data respectively.

3. Data Loading and Reporting:
   
- Load the transformed data into Azure Synapse Analytics.
- Build a Power BI dashboard to visualize the data, allowing stakeholders to explore metrics.

## Automation:

Schedule the pipeline to run daily, ensuring that the data and reports are always up-to-date.
Technology Stack
- Azure Data Factory (ADF): For orchestrating data movement and transformation.
- Azure Data Lake Storage (ADLS): For storing raw and processed data.
- Azure Databricks: For data transformation and processing.
- Azure Synapse Analytics: For data warehousing and SQL-based analytics.
- Power BI: For data visualization and reporting.
- Azure Key Vault: For securely managing credentials and secrets.
- SQL Server (On-Premises): Source of flight data.

## Setup Instructions
### Prerequisites
- An Azure account with sufficient credits.
- Access to an on-premises SQL Server database.
  
Step 1: Azure Environment Setup

1. Create Resource Group: Set up a new resource group in Azure.
   
3. Provision Services:
   - Create an Azure Data Factory instance.
   - Set up Azure Data Lake Storage with `bronze`, `silver`, and `gold` containers.
   - Set up an Azure Databricks workspace and Synapse Analytics workspace.
   - Configure Azure Key Vault for secret management.
     
Step 2: Data Ingestion

  1. Set up SQL Server: Install SQL Server and SQL Server Management Studio (SSMS). Restore the AdventureWorks database.
   
  3. Ingest Data with ADF: Create pipelines in ADF to copy data from SQL Server to the `bronze` layer in ADLS.
   
Step 3: Data Transformation

  1. Mount Data Lake in Databricks: Configure Databricks to access ADLS.
   
  3. Transform Data: Use Databricks notebooks to clean and aggregate the data, moving it from `bronze` to `silver` and then to `gold`.
   
Step 4: Data Loading and Reporting

  1. Load Data into Synapse: Set up a Synapse SQL pool and load the `gold` data for analysis.
   
  3. Create Power BI Dashboard: Connect Power BI to Synapse and create visualizations based on business requirements.
   
Step 5: Automation and Monitoring

  1. Schedule Pipelines: Use ADF to schedule the data pipelines to run daily.
     
  3. Monitor Pipeline Runs: Use the monitoring tools in ADF and Synapse to ensure successful pipeline execution.
     
Step 6: Security and Governance

  1. Manage Access: Set up role-based access control (RBAC) using Azure Entra ID (formerly Active Directory).
Step 7: End-to-End Testing

  2. Trigger and Test Pipelines: Insert new records into the SQL database and verify that the entire pipeline runs successfully, updating the Power BI dashboard.

## Dashboard

![dashboard](https://github.com/user-attachments/assets/82a5107e-6739-4346-9210-ad8319e896ee)

## Conclusion

This project provides a robust end-to-end solution for understanding aircraft utilization. The automated data pipeline ensures that stakeholders always have access to the most current and actionable insights.

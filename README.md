
# 2024 Paris Olympic Analysis | Azure End-To-End Data Engineering Project

This project provides a data engineering and analytical journey on the Paris Olympic dataset. Starting with a CSV on GitHub, the data is ingested into the Azure ecosystem via Azure Data Factory. It's initially stored in Azure Data Lake Storage Gen2, then transformed in Azure Databricks. The enriched data, once again housed in ADLS Gen2, undergoes advanced analytics in Azure Synapse. The insights are finally visualized in Azure Synapse or Power BI, offering a comprehensive view of the dataset.


## Datasets Utilized

This dataset contains the details of the participating Athletes, Coaches, and team, Entries by gender. It contains their names, countries represented, discipline, gender of competitors, name of the coaches.

This dataset contains the details of over 10,500 athletes, with 48 disciplines, along with 206 Teams taking part in the 2024 Paris Olympics. 
## Structure
The process begins with the ingestion of raw data from a CSV file stored on GitHub, using Azure Data Factory to bring it into the Azure ecosystem. The data is initially stored in Azure Data Lake Storage Gen2 before being transformed and enriched in Azure Databricks. After processing, the enhanced data is stored back in ADLS Gen2, where advanced analytics are performed in Azure Synapse Analytics. Finally, the insights derived from these analyses are visualized in Azure Synapse or Power BI, providing a comprehensive and actionable view of the dataset.



![App Screenshot](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Images/Structure.png)


## Azure Services Used

1. Azure Data Factory: For data ingestion from GitHub.
2. Azure Data Lake Storage Gen2: As the primary data storage     solution.
3. Azure Databricks: For data transformation tasks.
4. Azure Synapse Analytics: To perform in-depth data analytics.
## Initial Setup
1. created Azure Free Subscription account
2. created a Resource Group 'Paris-Olympic' to house and manage all the Azure resources associated with this project.
3. Within the created resource group, set up a storage account. This is specifically configured to leverage Azure Data Lake Storage(ADLS) Gen2 capabilities.
4. Created a Container 'paris-olympic-data-2024' inside this storage account to hold the project's data. Two directories 'raw-data' and 'transformed-data' are created to store raw data and transformed data.

![App Screenshot](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Images/azure_storage_account.png)
## Data Ingestion

1. Begin by creating an Azure Data Factory workspace within the previously established resource group.
2. After setting up the workspace, launch the Azure Data Factory Studio.
3. Upload the Paris Olympics dataset from Kaggle to GitHub.
Within the studio, initialize a new data integration pipeline.
4. Now use the task Copy Data to move data efficiently between various supported sources and destinations.
5. Configuring the Data Source with an HTTP template as we are using HTTP requests to get the data from the GitHub repo.
6. Establishing the Linked Service for source.
7. Configuring the File Format for and setting up the Linked Service Sink.
8. Repeat the above steps to load all the datasets.
9. You can connect all the copy data activity and run them all at once.
10. After the pipeline completes its execution, navigate to your Azure Data Lake Storage Gen2. Dive into the "raw_data" folder and validate that the files, like "athletes.csv", "medals.csv", etc., are present and populated with the expected data.

![App Screenshot](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Images/Pipeline.png)

![App Screenshot](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Images/ADLS_raw_data.png)

Please refer to the notebook below for transformations and code mounting ADLS Gen2 to Databricks. 
[Paris-Olympic-Data-Transformation](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Paris-Olympic-Data-Transformation.ipynb)
## Data Transformation using Azure Databricks

1. Navigate to Azure Databricks within the Azure portal and create a workspace within the previously established resource group and launch it.
2. Configuring Compute in Databricks.
3. Create a new notebook within Databricks and rename it appropriately, reflecting its purpose or the dataset it pertains to.
4. Establishing a Connection to Azure Data Lake Storage (ADLS)
5. Using the credentials (Client ID, Tenant ID, Secret), write the appropriate code in the Databricks notebook to mount ADLS.
6. Writing Data Transformations mount ADLS Gen2 to Databricks.
7. Writing Transformed Data to ADLS Gen2.

![App Screenshot](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Images/storage_transformed_data.png)
![App Screenshot](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Images/transformed_data_content.png)

Refer to the information below for the transformations and code used to mount ADLS Gen2 to Databricks. [Paris-Olympic-Data-Transformation](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Paris-Olympic-Data-Transformation.ipynb)


## Setting Up and Using Azure Synapse Analytics

1. Creating a Synapse Analytics Workspace.
2. Within Workspace navigate to the "Data" section, choose "Lake Database" and created a Database called "ParisOlympicDB"
3. Create a Table from the Data Lake from the Transformed Data folder within your ADLS Gen2 storage.

![App Screenshot](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Images/Synapse_database.png)
## Performing Data Analysis on the Data

![App Screenshot](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Images/Synapse_reports.png)

Refer to the SQL scripts used for data analysis [Paris OlympicSQL script](https://github.com/SonuRepo/paris_olympic_azure_project/blob/main/Paris%20OlympicSQL%20script.sql)

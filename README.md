# SalesAssignment

The flow execution is automated using event triggers and pipelines. When the source system pushes a file to the SFTP server, and the SFTP server transfers it to the ADLS raw container, an event trigger (TRG_PROCESS_DATA) is fired, which calls the pipeline (RETAIL_PROCESS). The pipeline includes a Databricks notebook task responsible for:
- Validating the data
- Performing quality checks
- Refining and cleansing master data for products, customers, and regions
- Creating a report for inconsistent data that will not be processed
- Writing the cleansed master data to the harmonized layer

Azure Synapse is used as the data warehouse, and it is responsible for creating data marts. Once the data marts are populated, analysis can be performed on them and used in Power BI to generate dashboards.

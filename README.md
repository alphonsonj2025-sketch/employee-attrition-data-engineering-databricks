# Employee Attrition Data Engineering Project (Databricks Medallion Architecture)

## 📌 Project Overview
This project demonstrates an end-to-end Data Engineering pipeline using the Medallion Architecture (Bronze, Silver, Gold) in Databricks.
The goal is to analyze employee attrition data and generate business insights using scalable data processing techniques.

Technologies used:
- Databricks  (with unity catalog for data governance)
- PySpark     (data processing)
- Delta Lake  (storage layer)
- SQL         (analytic and transformations)

- ## 📂 Unity Catalog Implementation

This project uses Unity Catalog to manage data governance, organization, and access control in Databricks.

### Structure Used:
- **Catalog**: `catalog_emp_attrition`
- **Schema**: `schema_emp_att`
- **Volume**: `empattvol`

### Purpose:
- Centralized data management across layers (Bronze, Silver, Gold)
- Secure and governed data access
- Organized storage for structured data pipelines

### Data Storage Path:
/Volumes/catalog_emp_attrition/schema_empatt/empattvol/

### Layers:
- Bronze → Raw data ingestion
- Silver → Cleaned and transformed data
- Gold → Business-ready aggregated data
- ![Workspace Setup](images/001_workspace_setup.png)

- **Catalog & Schema Setup (Unity Catalog)**

This screenshot shows the successful creation of the project’s data structure in Databricks using Unity Catalog.
A catalog named catalog_emp_attrition was created to group all project-related data assets
A schema named schema_emp_att was created within the catalog to organize datasets
This setup establishes a clear and scalable foundation for managing data across the Medallion Architecture (Bronze, Silver, Gold).
![Catalog Setup](images/002_catalog_creation.png)

# Data Upload to Volume

This step confirms the successful upload of the raw dataset into the Unity Catalog volume.
The dataset Employee-Attrition.csv was uploaded into the volume
The file is stored within the schema under the volume (displayed as “files” in the Databricks UI)
![Data Uploaded](images/003_data_uploaded.png)


**📂Bronze Layer – Raw Data Ingestion**

The raw employee attrition dataset is successfully ingested into the Bronze layer, serving as the foundation of the Medallion Architecture.
This layer preserves data in its original format, ensuring traceability and enabling downstream transformations.
Highlights:
Ingestion into Unity Catalog Volume
Organized storage structure for scalability
Supports batch processing workflows
![Bronze Upload](images/004_bronze_upload.png)

##**Step 1: Create Medallion Folders Using PySpark**##
🔧 **Code**##

To implement the Medallion Architecture, directories were created inside the Unity Catalog Volume using PySpark utilities.
🔧**Code**
dbutils.fs.mkdirs("/Volumes/catalog_emp_attrition/schema_emp_att/emp_bronze")
dbutils.fs.mkdirs("/Volumes/catalog_emp_attrition/schema_emp_att/emp_silver")
dbutils.fs.mkdirs("/Volumes/catalog_emp_attrition/schema_emp_att/emp_gold")
![Folder Creation](images/005-bronze_ingestion_emp_attrition.png)

This step creates three layers for structured data processing:
Bronze Layer (emp_bronze) → Stores raw, unprocessed data
Silver Layer (emp_silver) → Stores cleaned and transformed data
Gold Layer (emp_gold) → Stores aggregated, business-ready data

📌 **Step 2: Verify Folder Structure in Unity Catalog**

![Unity Catalog Structure](images/006_unity_catalog_volume_structure.png)

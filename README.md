# SAP-to-Cloud-Migration
Migrated 500 TB of SAP data from HDFS to Azure for OLAP reporting. Using ExpressRoute, Azure Data Factory, and Self-hosted Integration Runtime, data was ingested into Azure Data Lake. Transformation was done with Databricks and PySpark. Processed data was stored in SSMS and linked to Power BI dashboards.

## 📄 Project Overview

This project showcases the successful migration of approximately **500 TB** of SAP data stored in **HDFS** (in formats such as Parquet, JSON, and CSV) from an on-premise environment to **Azure Cloud**. The primary goal was to enable analytical (OLAP) workloads by transforming and storing structured data in a Snowflake-schema-based **SQL Data Warehouse** integrated with **Power BI** for reporting.

---

## 🧱 Architecture Overview

**Main Components:**

- **Source:** On-Premise SAP (via HDFS – Parquet, JSON, CSV)
- **Connectivity:** Azure ExpressRoute
- **Orchestration:** Azure Data Factory (ADF)
- **Transformation Engine:** Azure Databricks (ADB) using PySpark
- **Sink:** SQL Server Data Warehouse (Snowflake Schema)
- **Reporting Layer:** Power BI

> ADF was also used for small datasets (≤ 2GB) and CSV files via Data Flows. Larger and complex JSON/Parquet files were handled by ADB with performance-optimized PySpark jobs.

---

## 🔁 Workflow

1. **Data Extraction:**  
   Data is pulled from HDFS via Azure Integration Runtime (IR) using ExpressRoute.

2. **Conditional Processing Logic:**
   - CSV or small files (≤ 2GB) → processed using **ADF Data Flows**.
   - JSON and large Parquet files → processed using **Azure Databricks**.

3. **Data Transformation:**
   - PySpark with **lazy evaluation** and **salting** techniques.
   - Standardized DataFrames handled business logic.

4. **Data Loading:**  
   Final transformed data is loaded to **SQL Server Data Warehouse** with a **Snowflake Schema** (Fact and Dimension tables).

5. **Reporting:**  
   Power BI dashboards connected to warehouse for real-time analytics.

---

## 🔧 Technologies Used

| Service            | Purpose                                |
|--------------------|----------------------------------------|
| Azure Data Factory | Orchestration and data ingestion       |
| Azure Databricks   | Data transformation (PySpark)          |
| SQL Server DW      | Structured OLAP storage (Snowflake)    |
| Power BI           | Visualization and Reporting            |
| ExpressRoute       | Secure high-speed data transfer        |

---

## 📈 Schema Design

- **Snowflake Schema**
  - Central **Fact Tables** connected to multiple **Dimension Tables**
  - Dimension tables further linked to **Sub-Dimensions** where needed
  - Highly normalized for performance and storage efficiency

---

## 📊 Diagram

Architecture and flow diagram is available in the `/docs` folder or can be viewed [here](./docs/SAP_to_Azure_Migration_Architecture.png)

---

## 🧠 Key Learnings

- Leveraged cloud-native tools for large-scale migration
- Demonstrated cost and compute efficiency by dynamically choosing processing engines
- Implemented PySpark best practices and advanced transformation logic

---

## 📁 Folder Structure

/SAP-Azure-Migration/
│
├── notebooks/ # PySpark Notebooks (cleansed, no data)
├── pipelines/ # ADF pipeline JSONs or visual diagrams
├── docs/
│ └── SAP_to_Azure_Migration_Architecture.png
│ └── SAP_to_Azure_Migration_Documentation.docx
├── README.md


---

## 🔐 Note

All code and logic provided here is generalized and **contains no confidential or client-specific data**.

---

## 📬 Contact

If you're interested in similar solutions or freelance work, feel free to reach out!


# 📊 Economic & Demographic Analysis of Indian States using AWS (S3, Glue, Redshift)

A scalable **ETL (Extract, Transform, Load)** pipeline built on **AWS Cloud** to perform insightful analysis on India’s economic and demographic indicators using publicly available datasets. The project focuses on **Per Capita Income** and **Sex Ratio**, helping uncover trends across Indian states.

---

## 📌 Project Overview

This project demonstrates how cloud-based data engineering can be used to drive **economic and social insights** from raw datasets. We used:

- **Amazon S3** for data storage  
- **AWS Glue** (ETL Jobs & Crawlers) for schema inference and data transformation  
- **Amazon Redshift** for querying and analysis

We analyzed data from:
- **India Census** (Demographics like population, sex ratio, literacy)
- **State-wise State Domestic Product (SDP)** (Income indicators and economic performance)

---

## 📊 Datasets

### 1. India Census Dataset
- **Attributes:** State, Population, Sex Ratio, Literacy Rate, etc.

### 2. State-wise SDP Dataset
- **Attributes:** State, Net State Domestic Product, Per Capita Income, Sector-wise Contribution, etc.

### Key Indicators Analyzed
- **Economic Metrics:** Per Capita Income, Total SDP  
- **Demographic Metrics:** Sex Ratio, Population  
- **Derived Insights:** Correlation between economic prosperity and social indicators

---

## ⚙️ ETL Pipeline Overview

### Extraction

- Raw CSV files uploaded to **Amazon S3**, acting as the central data lake.
- **AWS Glue Crawlers** scan the S3 data and automatically create schema in **AWS Glue Data Catalog**.

### Transformation

A custom **AWS Glue Job** using **PySpark** performs the following transformations:

| Attribute        | Transformation Logic                              |
|------------------|----------------------------------------------------|
| Sex Ratio        | Converted to consistent numeric format             |
| Income Data      | Cleaned and scaled to uniform units               |
| Null Handling    | Handled missing/invalid records                    |
| Derived Columns  | Added fields like "Income Bracket" or "Density"   |

- **Output Format:** Parquet  
- **Storage Location:** Transformed data saved back to **Amazon S3**

### Load

- Cleaned and transformed data is imported into **Amazon Redshift**.
- Data is loaded using the Redshift `COPY` command for fast ingestion and optimized querying.

---

## ETL Flow Summary

1. **Extract**
   - Upload raw India Census and SDP datasets to **Amazon S3**

2. **Transform**
   - Use **AWS Glue Crawler** to infer schema
   - Apply cleaning and standardization logic via **AWS Glue Job**
   - Save the transformed data in **Parquet format** to S3

3. **Load**
   - Load cleaned datasets into **Amazon Redshift**
   - Run SQL queries to extract insights

---

## 💡 Sample Insights Extracted

- States with **higher Per Capita Income** generally exhibit **better literacy rates and sex ratios**
- Identified **economic disparities** between industrialized and agrarian states
- Clustered states into **high, medium, and low-income brackets**

---

## 💻 Technologies Used

- **Amazon S3** – Raw and transformed data storage  
- **AWS Glue Crawler** – Schema detection and Data Catalog creation  
- **AWS Glue** – PySpark-based transformation logic  
- **Amazon Redshift** – Cloud-based data warehouse for fast analytics  
- **Parquet Format** – Efficient storage for querying  
- **Python (PySpark)** – For data cleaning and transformations

---

## 🎯 Use Case

Governments, NGOs, and researchers can use this pipeline to:

- Monitor **state-wise development** across India  
- Identify **regions requiring policy interventions**  
- Explore **relationships between demographic and economic indicators**

---

## 🎥 Demo

▶️ [Click here to watch the project video explanation](https://drive.google.com/file/d/1L2MdG62RdISPUGNlKqMX10uQOZnlujfQ/view?usp=drive_link)


# TelcoSphere-Project_With_Databricks



## Project Overview

**TelcoSphere** is a mid-sized telecommunications company operating across **Africa, Europe, and North America**, offering:

* Mobile voice services
* Mobile data plans
* SMS services

The company serves **hundreds of thousands of customers**, producing large volumes of customer, subscription, and usage data daily.

This project focuses on **designing and implementing a modern, cloud-based analytics platform** that consolidates raw telecom data and transforms it into **trusted, analytics-ready datasets** for decision-making and customer churn analysis.

## Architecture Explanation

The solution follows **Azure Medallion Architecture** using **Azure Data Lake Storage Gen2** and **Databricks**.

### Architecture Flow

1. **Dta Source**

   * Synthetic telecom data generated using Python and Faker
   * Exported as CSV files

2. **Bronze Layer (Raw Data)**

   * CSV files ingested directly into **ADLS Gen2 (Bronze)**

3. **Silver Layer (Cleaned Data)**

   * **Databricks** reads data from the Bronze layer
   * Transformations applied:

     * Deduplication
     * Data type casting
     * Data standardisation
     * Business rule validation
   * Cleaned data written to **ADLS Gen2 (Silver)**

4. **Gold Layer (Modelled Data)**

   * Databricks performs final transformations
   * Data modelled into:

     * Dimension tables
     * Fact tables
   * Analytics-ready datasets written to **ADLS Gen2 (Gold)**
  
5. Data Model (EDW) D
   *Dimension Tables
     *customer_dim
     *subscription_dim
     *plan_dim
   date_dim
     *Fact Table
     *usage_fact 

7. **Analytics & Serving Layer**

   * **Azure Data Studio** used for querying and validating curated datasets
   * Gold-layer data serves as the analytical staging and serving layer

8. **Visualisation Layer**

   * **Power BI** connects to the Gold layer
   * Dashboards built for:

     * Customer growth
     * Usage patterns
     * Revenue trends
     * Churn analysis



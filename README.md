# SQL Data Warehouse & Analytics Project

![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=flat\&logo=microsoftsqlserver\&logoColor=white)
![T-SQL](https://img.shields.io/badge/T--SQL-CC2927?style=flat\&logo=microsoftsqlserver\&logoColor=white)
![Data Warehouse](https://img.shields.io/badge/Data%20Warehouse-2C3E50?style=flat)
![ETL](https://img.shields.io/badge/ETL-4B8BBE?style=flat)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat\&logo=github\&logoColor=white)

## Overview

An end-to-end **SQL Server Data Warehouse** project designed to consolidate, transform, and model data from ERP and CRM source systems into a structured, analytics-ready platform.

The solution follows a **Medallion Architecture** consisting of **Bronze, Silver, and Gold layers**, with SQL-based ETL pipelines, data quality validation, and dimensional modeling implemented using **T-SQL**.

The final Gold layer provides a business-oriented **Star Schema** that can serve as the foundation for analytical workloads and BI solutions.

---

## Architecture

```text
                    Source Systems
                  ┌───────────────┐
                  │   ERP / CRM   │
                  │   CSV Files   │
                  └───────┬───────┘
                          │
                          ▼
                ┌───────────────────┐
                │   Bronze Layer    │
                │                   │
                │ Raw / Historical  │
                │ Source Data       │
                └─────────┬─────────┘
                          │
                     ETL & Cleaning
                          │
                          ▼
                ┌───────────────────┐
                │   Silver Layer    │
                │                   │
                │ Cleaned &          │
                │ Standardized Data │
                └─────────┬─────────┘
                          │
                  Business Modeling
                          │
                          ▼
                ┌───────────────────┐
                │    Gold Layer     │
                │                   │
                │ Business-Ready    │
                │ Dimensional Model │
                └─────────┬─────────┘
                          │
                          ▼
                ┌───────────────────┐
                │ Analytics / BI    │
                │ Reporting & SQL   │
                └───────────────────┘
```

---

## Key Objectives

* Design and implement a scalable SQL Server data warehouse.
* Build a structured **Bronze → Silver → Gold** data pipeline.
* Integrate ERP and CRM source data into a centralized warehouse.
* Clean, standardize, and transform raw datasets.
* Implement reusable **T-SQL ETL stored procedures**.
* Develop a dimensional **Star Schema** for analytical workloads.
* Implement data quality and validation checks.
* Document the data model, naming conventions, and business entities.
* Prepare the warehouse for downstream BI and reporting solutions.

---

## Data Warehouse Layers

### Bronze Layer

The Bronze layer stores source data in its raw form with minimal transformation.

**Responsibilities:**

* Source data ingestion
* Raw data preservation
* Initial data loading
* Source-system separation

### Silver Layer

The Silver layer transforms raw data into clean and standardized datasets.

**Responsibilities:**

* Data cleansing
* Data type standardization
* Handling inconsistent values
* Data transformation
* Business-rule preparation

### Gold Layer

The Gold layer provides business-ready data optimized for analytical consumption.

**Core entities:**

* `dim_customers`
* `dim_products`
* `fact_sales`

The model follows a **Star Schema**, separating descriptive dimensions from transactional facts.

---

## Dimensional Model

```text
                 ┌──────────────────┐
                 │  dim_customers   │
                 ├──────────────────┤
                 │ customer_key     │
                 │ customer_id      │
                 │ customer_number  │
                 │ first_name       │
                 │ last_name        │
                 │ country          │
                 │ gender           │
                 │ birthdate        │
                 └────────┬─────────┘
                          │
                          │
                          ▼
                 ┌──────────────────┐
                 │    fact_sales    │
                 ├──────────────────┤
                 │ order_number     │
                 │ customer_key     │
                 │ product_key      │
                 │ order_date       │
                 │ shipping_date    │
                 │ due_date         │
                 │ sales_amount     │
                 │ quantity         │
                 │ price            │
                 └────────┬─────────┘
                          │
                          │
                          ▼
                 ┌──────────────────┐
                 │  dim_products    │
                 ├──────────────────┤
                 │ product_key      │
                 │ product_id       │
                 │ product_number   │
                 │ product_name     │
                 │ category         │
                 │ subcategory      │
                 │ product_line     │
                 │ cost             │
                 └──────────────────┘
```

---

## ETL Pipeline

The warehouse loading process is implemented using **T-SQL stored procedures**.

```text
Source Data
     │
     ▼
Bronze Load
     │
     ▼
Data Validation
     │
     ▼
Silver Transformation
     │
     ▼
Data Quality Checks
     │
     ▼
Gold Transformation
     │
     ▼
Analytics-Ready Data
```

The pipeline separates ingestion, transformation, validation, and analytical modeling to improve maintainability and data reliability.

---

## Data Quality

Dedicated SQL validation scripts are included to verify the integrity of the warehouse data.

Quality checks cover areas such as:

* Data completeness
* Duplicate records
* Referential integrity
* Invalid or inconsistent values
* Data consistency between layers
* Business-rule validation

```text
test/
├── quality_checks_silver.sql
└── quality_checks_gold.sql
```

---

## Repository Structure

```text
sql-data-warehouse-poject/
│
├── datasets/
│
├── docs/
│   ├── data_catalog.md
│   ├── data_model.png
│   └── naming_conventions.md
│
├── scripts/
│   ├── init_database.sql
│   │
│   ├── bronze/
│   │   ├── ddl.bronze.sql
│   │   └── proc_load_bronze/
│   │
│   ├── silver/
│   │   ├── ddl_silver.sql
│   │   └── proc_load_silver.sql
│   │
│   └── gold/
│       └── ddl_gold.sql
│
├── test/
│   ├── quality_checks_silver.sql
│   └── quality_checks_gold.sql
│
└── README.md
```

---

## Technology Stack

| Area            | Technology             |
| --------------- | ---------------------- |
| Database        | Microsoft SQL Server   |
| Language        | T-SQL                  |
| ETL             | SQL Stored Procedures  |
| Architecture    | Medallion Architecture |
| Data Modeling   | Star Schema            |
| Data Quality    | SQL Validation Scripts |
| Documentation   | Markdown               |
| Version Control | Git / GitHub           |

---

## Skills Demonstrated

**Data Engineering**

* Data Warehousing
* ETL Development
* Data Integration
* Data Transformation
* Data Quality
* Dimensional Modeling

**SQL**

* Advanced SQL
* T-SQL
* Stored Procedures
* DDL / DML
* Data Validation
* Analytical Queries

**Architecture**

* Medallion Architecture
* Star Schema
* Fact & Dimension Modeling
* Layered Data Architecture

---

## Getting Started

### Prerequisites

* Microsoft SQL Server
* SQL Server Management Studio (SSMS)
* Git

### Clone the Repository

```bash
git clone https://github.com/Moaaz-Elhaiys/sql-data-warehouse-poject.git

cd sql-data-warehouse-poject
```

### Initialize the Database

Execute:

```text
scripts/init_database.sql
```

This creates the required database and warehouse schemas.

> **Warning:** The initialization script recreates the warehouse database. Do not execute it against a database containing data you need to preserve.

### Execute the ETL Pipeline

Run the scripts in the following order:

```text
1. Bronze Layer
2. Silver Layer
3. Gold Layer
4. Data Quality Checks
```

---

## Documentation

Additional documentation is available in the [`docs`](./docs) directory.

* [Data Catalog](./docs/data_catalog.md)
* [Data Model](./docs/data_model.png)
* [Naming Conventions](./docs/naming_conventions.md)

---

## Future Enhancements

* Incremental data loading
* Slowly Changing Dimensions (SCD)
* ETL orchestration and scheduling
* Automated data-quality testing
* CI/CD integration
* Analytical SQL views
* Power BI integration
* Interactive business intelligence dashboard
* Containerized development environment

---

## Author

**Moaaz Elhaiys**

**Data Analytics Engineer | Data Engineering | SQL | Power BI**

[GitHub](https://github.com/Moaaz-Elhaiys)

---

## License

This project is licensed under the MIT License.

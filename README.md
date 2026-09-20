# 🏠 Airbnb End-to-End Data Engineering Project

> **End-to-end data engineering pipeline for Airbnb data using AWS S3, Snowflake and dbt, following a modern Medallion Architecture.**

## 📋 Overview

This project implements a complete **end-to-end data engineering pipeline** for Airbnb data.

The pipeline ingests raw CSV datasets into **AWS S3**, loads them into **Snowflake**, and transforms them with **dbt** through a **Bronze → Silver → Gold** architecture.

The project demonstrates key data engineering concepts including:

* Data ingestion and cloud storage
* Data warehousing with Snowflake
* SQL transformations with dbt
* Incremental models
* Slowly Changing Dimensions (SCD Type 2)
* Data quality testing
* Reusable dbt macros
* Analytics-ready data modeling

---

## 🏗️ Architecture

```text
                    ┌───────────────┐
                    │   Source CSV  │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │    AWS S3     │
                    │ Cloud Storage │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │   Snowflake   │
                    │    Staging    │
                    └───────┬───────┘
                            │
                            ▼
              ┌──────────────────────────┐
              │       dbt Pipeline       │
              └────────────┬─────────────┘
                           │
             ┌─────────────┼─────────────┐
             ▼             ▼             ▼
        🥉 Bronze      🥈 Silver      🥇 Gold
        Raw Data      Clean Data    Analytics
```

---

## 🛠️ Technology Stack

| Technology       | Purpose                            |
| ---------------- | ---------------------------------- |
| **Python 3.12+** | Project environment and automation |
| **AWS S3**       | Cloud object storage               |
| **Snowflake**    | Cloud data warehouse               |
| **dbt**          | Data transformation and modeling   |
| **SQL**          | Data transformation and analysis   |
| **Git / GitHub** | Version control                    |

### dbt Features

* Incremental models
* Snapshots / SCD Type 2
* Jinja templating
* Custom macros
* Data quality tests
* Source definitions
* Layered data modeling

---

## 📊 Data Model

The project follows a **Medallion Architecture**.

### 🥉 Bronze — Raw Data

The Bronze layer contains data loaded from Snowflake staging with minimal transformations.

```text
bronze_bookings
bronze_hosts
bronze_listings
```

### 🥈 Silver — Cleaned & Standardized Data

The Silver layer applies cleaning, standardization and business transformations.

```text
silver_bookings
silver_hosts
silver_listings
```

Examples include:

* Data validation
* Standardization
* Data quality improvements
* Price categorization
* Host profile enrichment

### 🥇 Gold — Analytics-Ready Data

The Gold layer contains datasets designed for analytics and reporting.

```text
fact
obt
```

Where:

* **fact** → dimensional-modeling fact table
* **obt** → One Big Table combining bookings, listings and hosts
* **ephemeral models** → intermediate transformations used by dbt

---

## 🔄 Slowly Changing Dimensions — SCD Type 2

The project uses **dbt snapshots** to preserve historical changes in key business entities.

```text
dim_bookings
dim_hosts
dim_listings
```

This allows historical versions of records to be maintained rather than simply overwriting previous values.

---

## 📁 Project Structure

```text
AWS_DBT_Snowflake/
│
├── README.md
├── pyproject.toml
├── main.py
│
├── SourceData/
│   ├── bookings.csv
│   ├── hosts.csv
│   └── listings.csv
│
├── DDL/
│   ├── ddl.sql
│   └── resources.sql
│
└── aws_dbt_snowflake_project/
    │
    ├── dbt_project.yml
    ├── ExampleProfiles.yml
    │
    ├── models/
    │   ├── sources/
    │   │   └── sources.yml
    │   │
    │   ├── bronze/
    │   │   ├── bronze_bookings.sql
    │   │   ├── bronze_hosts.sql
    │   │   └── bronze_listings.sql
    │   │
    │   ├── silver/
    │   │   ├── silver_bookings.sql
    │   │   ├── silver_hosts.sql
    │   │   └── silver_listings.sql
    │   │
    │   └── gold/
    │       ├── fact.sql
    │       ├── obt.sql
    │       └── ephemeral/
    │
    ├── macros/
    ├── analyses/
    ├── snapshots/
    ├── tests/
    └── seeds/
```

---

## 🚀 Getting Started

### Prerequisites

Before running the project, you need:

* **Python 3.12+**
* **Snowflake account**
* **AWS account**
* **AWS S3 bucket**
* **dbt**
* **Git**


### 1. Create a Python environment

Using `uv`:

```bash
uv venv
source .venv/bin/activate
```

Install dependencies:

```bash
uv pip install -r requirements.txt
```

### 3. Configure Snowflake

Configure your Snowflake credentials and connection profile.

> **Never commit credentials, passwords, API keys or private connection information to GitHub.**

### 4. Configure AWS S3

Upload the source datasets to your S3 bucket:

```text
s3://<your-bucket>/
    bookings.csv
    hosts.csv
    listings.csv
```

---

## 🎯 Project Objectives

This project demonstrates practical Data Engineering skills in:

* **Cloud data storage**
* **Cloud data warehousing**
* **ETL / ELT pipelines**
* **Dimensional data modeling**
* **Medallion Architecture**
* **dbt development**
* **Incremental processing**
* **SCD Type 2**
* **Data quality**
* **SQL transformation**
* **Version control**

---

## 🔮 Future Improvements


---

## 👨‍💻 Author

**Edgard Basso**

**AI Engineer | Data Engineer | Data & Risk Analytics**

`Python` · `SQL` · `Snowflake` · `dbt` · `AWS` · `Data Engineering` · `Machine Learning`

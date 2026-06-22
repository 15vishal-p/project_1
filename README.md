# PaySim Fraud Detection Data Pipeline

A scalable, production-style data pipeline that ingests, transforms, and analyzes 6M+ synthetic mobile money transactions to surface fraud patterns — built to mirror real-world data engineering workflows used in financial services.

## Overview
This project simulates an end-to-end data engineering workflow: raw transactional data is ingested, cleaned, modeled into staging/intermediate/mart layers using dbt, and processed at scale in Databricks. The goal is to produce reliable, tested, well-documented data models that could support downstream fraud analytics and reporting.

## Dataset
[PaySim1](https://www.kaggle.com/datasets/ealaxi/paysim1) — a synthetic dataset of mobile money transactions (~6.3M rows) including transaction type, amount, sender/receiver balances, and fraud labels.

## Architecture  

Raw CSV → Databricks (Delta Lake) → dbt (staging → intermediate → mart) → Analytics-ready tables

## Technologies Used
- **Databricks** — distributed data processing, Delta Lake storage
- **dbt** — data modeling, transformation, testing, and documentation
- **SQL** — transformation logic and data quality checks
- **Python** — initial data profiling and exploration
- **Git/GitHub** — version control

## Project Structure

├── models/
│   ├── staging/        # cleaned, typed source data
│   ├── intermediate/   # business logic (fraud flags, balance checks)
│   └── marts/          # final aggregated tables for analysis
├── tests/               # dbt data quality tests
├── notebooks/           # Databricks exploration notebooks
└── README.md

## Data Quality & Testing
- Schema tests: not-null, accepted values, uniqueness checks on key fields
- Custom test: validates balance consistency (`oldbalance - amount = newbalance`)
- dbt docs generated for full model lineage and documentation

## Key Findings
*(fill in once you run it — e.g. "Fraud is concentrated in TRANSFER and CASH_OUT transaction types, accounting for X% of flagged cases")*

## Setup Instructions
1. Clone the repo: `git clone <your-repo-url>`
2. Set up a Databricks Community Edition workspace and upload the dataset
3. Install dbt: `pip install dbt-core dbt-databricks`
4. Configure your `profiles.yml` with your Databricks connection details
5. Run `dbt run` to build models, `dbt test` to validate data quality

## What This Project Demonstrates
- Building modular, layered data models (staging → mart)
- Implementing data quality frameworks via dbt tests
- Working with cloud-based data platforms (Databricks)
- Git-based version control and reproducible project structure

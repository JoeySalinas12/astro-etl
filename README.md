# astro-etl

## Overview

This project builds an end-to-end data pipeline to process astrophysics data, focusing on exoplanets and stellar properties. It uses dbt, Airflow, Python, and Snowflake to ingest, transform, and analyze datasets from NASA's Exoplanet Archive and ESA's Gaia mission.

## Tech Stack

Data Ingestion: Python, Airflow

Storage: AWS S3 (optional), Snowflake

Processing: dbt (SQL transformations)

Orchestration: Apache Airflow (DAG scheduling)

Monitoring: Great Expectations (data validation)

Visualization: Tableau / Power BI

## Data Sources

- NASA Exoplanet Archive API - Provides information on confirmed exoplanets.

- ESA Gaia Data Release - Stellar properties like temperature, luminosity, and position.

## Pipeline Structure

```bash
          # Airflow DAGs for orchestration
│-- dags/                     # Airflow DAGs for orchestration
│   ├── ingest_exoplanets.py  # DAG for fetching exoplanet data
│   ├── ingest_gaia.py        # DAG for fetching stellar data
│
│-- dbt/
│   ├── models/
│   │   ├── staging/
│   │   │   ├── stg_exoplanets.sql  # Staging model for raw exoplanet data
│   │   │   ├── stg_gaia.sql        # Staging model for Gaia data
│   │   ├── marts/
│   │   │   ├── exoplanet_analysis.sql  # Processed dataset for analysis
│
│-- scripts/
│   ├── fetch_exoplanets.py  # Python script to fetch exoplanet data
│   ├── fetch_gaia.py        # Python script to process Gaia dataset
│
│-- great_expectations/      # Data quality checks
│-- config/
│   ├── airflow_connections.env  # Environment variables for Airflow
│   ├── dbt_profiles.yml         # dbt connection settings
│
│-- data/
│
│-- requirements.txt        # Python dependencies
│-- README.md               # Project documentation
```

## Pipeline Steps

**Ingestion**: Fetch exoplanet data via API and download Gaia dataset files.

**Staging**: Store raw data in Snowflake staging tables.

**Transformation**: Use dbt to clean, standardize, and join datasets.

**Orchestration**: Use Airflow DAGs to automate and schedule workflows.

**Monitoring**: Validate data quality with Great Expectations.

**Analytics**: Aggregate data for insights (e.g., habitable zone classification).

## Next Steps

1. Implement the Airflow DAG to fetch and load exoplanet data.

2. Set up dbt models for staging and transformation.

3. Build dashboards to visualize findings.

## Setup Instructions

1. Clone the repository:
   ```bash
   git clone <repo-url>
   ```

2. Set up a virtual environment:
    ```bash
    python -m venv venv
    source venv/bin/activate # Mac/Linux
    env\Scripts\activate # Windows
    ```

3. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```

4. Configure Snowflake credentials in config/snowflake.yml.

5. Deploy Airflow DAGs and dbt models.

6. Run the pipeline!

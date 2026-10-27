# Healthcare Analytics with Python and SQL Server

## Overview
This project demonstrates an end-to-end healthcare analytics workflow using Python, SQL Server, and a sample healthcare-style dataset. The scripts cover database setup, data generation/loading, clinical views, statistical analysis, survival analysis, time-series forecasting, and report generation.

> **Data note:** Treat the included CSVs as demonstration data and verify their provenance before sharing. Do not upload real patient or confidential health information.

## Tools
- Python: pandas, NumPy, scikit-learn, SciPy, statsmodels, Matplotlib, Faker, lifelines
- Microsoft SQL Server and ODBC Driver for SQL Server
- SQL: database schema, clinical views, and analytical queries

## Repository structure
```text
scripts/       Python and SQL scripts
 data/raw/     CSV datasets used by the workflow
outputs/       Generated charts/reports (created when scripts run)
```

## Workflow
1. Review `scripts/01_create_database.sql` and create the database/schema in SQL Server.
2. Install the Python packages used by the scripts.
3. Generate demo data with `scripts/02_generate_healthcare_data.py`, or use the included CSV files.
4. Load the CSV files into SQL Server using `scripts/03_load_data_to_sqlserver.py` after confirming the table schema and paths.
5. Run `scripts/04_create_clinical_views.sql` to create the analytical views.
6. Run the statistical, survival, time-series, and reporting scripts after confirming the SQL connection and required views/tables.

## Setup
Create a virtual environment and install the packages needed by the scripts. Example:
```bash
python -m venv .venv
# Windows PowerShell:
.venv\Scripts\Activate.ps1
pip install pandas numpy Faker sqlalchemy pyodbc scikit-learn scipy statsmodels matplotlib lifelines
```

Install Microsoft SQL Server and the matching Microsoft ODBC driver separately. Update the SQLAlchemy connection string in the scripts to match your local SQL Server instance and database. The current scripts reference a local instance named `SMASH`; that name will not work for everyone. Do not commit passwords or secrets.

## Important path note
The Python scripts use relative paths such as `../data/raw` and `../outputs`. Run the scripts with the working directory set to the `scripts` folder, or update the paths to match your environment. Some scripts expect tables/views to exist in SQL Server before they run.

## Current limitations
- Local SQL Server configuration is environment-specific.
- Confirm that the database schema and CSV column names match before loading.
- Validate the analytical results and generated outputs before using them in a report.
- This is a portfolio/demo project, not a clinical decision-support system.

## Suggested next improvements
- Add screenshots of output charts and dashboards.
- Document validated results and model metrics.
- Add a `requirements.txt` and a `.env.example` if configuration is moved to environment variables.
- Add automated data-quality checks and tests.

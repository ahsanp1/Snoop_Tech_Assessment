# Data Pipeline for Transaction Data

## Overview

This Python code implements an ETL pipeline for processing transaction data from a JSON file into a normalized format with data quality checks, and loading into a mock datamart.

The pipeline performs the following key steps:

1. Read transaction data from a JSON file
2. Normalize the data into a Pandas DataFrame
3. Perform data quality checks on the normalized data:
   - Duplicate check
   - Currency check
   - Date format check
4. Remove records failing quality checks 
5. Create transaction and customer DataFrames
6. Upsert transaction and customer data into mock datamart CSV files
7. Log any errors into a CSV error log

## Code Structure

The code is structured into functions performing each pipeline step:

- `json_to_dataframe()`: Reads JSON file and normalizes into DataFrame
- `duplicate_check()`: Checks for duplicate records
- `currency_check()`: Checks for invalid currency codes 
- `date_check()`: Checks for invalid date formats
- `upsert_datamart()`: Upserts DataFrame into mock datamart CSV
- `error_logging()`: Logs errors into CSV file

The main driver code executes the functions in sequence to implement the full pipeline.

## Usage

The code requires the following input file:

- `tech_assessment_transactions.json`: Source transaction data in JSON format

It outputs the following:

- Normalized and archived CSV: `tech_assessment_transactions.csv` 
- Mock datamart CSVs: `fact_transactions.csv`, `dim_customers.csv`
- Error log CSV: `error_logs.csv`

The input and output files are configured based on parameters at the top of the script.

To run the code, simply execute the Jupyter notebook cell-by-cell.

## Next Steps

Some ways this pipeline could be enhanced:

- Parameterize configuration to make it reusable
- Add logging for debugging
- Containerize into Docker for portability
- Set up automated testing
- Integrate with actual database/data warehouse instead of CSV mocks
- Add type checking with Pydantic or other library
- Improve error handling

Let me know if you have any other questions!

### Healthcare-Billing---Data-Cleaning
Data cleaning, validation, and preprocessing in Python (Pandas) for a 55,000+ record healthcare billing and insurance dataset.

## Overview
Raw healthcare billing records frequently contain formatting inconsistencies, duplicate visit logs, text-encoded dates, and invalid financial entries that can distort revenue and payout metrics. This notebook executes a structured, step-by-step data quality audit resulting in a verified dataset of **54,860 clean records across 15 columns**.

## Key Data Cleaning Steps

* **Schema & Text Standardization:** Normalized all 15 column headers into `snake_case` and formatted categorical text attributes (`name`, `medical_condition`, `insurance_provider`, `hospital`, `doctor`, etc.) into consistent Title Case.
* **Missing Value Audit:** Verified zero null or missing entries across all columns.
* **Duplicate Removal:** Identified and dropped **534 exact multi-column visit duplicates** based on unique clinical and demographic keys to prevent double-counting.
* **Date Validation & Type Conversion:** Confirmed chronological consistency (`discharge_date >= date_of_admission`) and converted `date_of_admission` and `discharge_date` from plain text (`str`) into `datetime64[us]` objects for length-of-stay and time-series calculations.
* **Financial Integrity Filtering:** Isolated and removed **106 zero or negative billing records** (`billing_amount <= 0`), ensuring accurate positive revenue distributions.

## Tech Stack
* **Language:** Python 3
* **Libraries:** Pandas
* **Environment:** Jupyter Notebook

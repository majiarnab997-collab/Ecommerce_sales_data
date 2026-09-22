# E-Commerce Sales Analysis and Statistical Modeling

## Project Overview

The main objective of this project is to clean raw transaction data from an e-commerce platform, gain business insights through descriptive and inferential statistics, and estimate sales using machine learning regression techniques.

## Directory Layout

* `data/raw/`: Contains the original and unmodified raw dataset (`ecommerce_sales_data.csv`).
* `data/cleaned/`: Contains the cleaned and validated dataset.
* `notebooks/`:

  * `01_inspection.ipynb`: Initial data inspection and identification of inconsistencies.
  * `02_cleaning.ipynb`: Handling missing values, type conversion, and outliers.
  * `03_analysis.ipynb`: Statistical tests, hypothesis testing, and regression modeling.
* `docs/`: Contains the data dictionary, data cleaning audit log, and documentation of theoretical assumptions.

## Environment Setup

To run the project, create and activate a Python virtual environment and install the required dependencies:

```bash
# Create a virtual environment
python -m venv venv

# Activate the environment (Windows PowerShell)
venv\Scripts\activate

# Install the required libraries
pip install -r requirements.txt
```

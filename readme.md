# Stock Market Data Engineering Pipeline

## Author
M Krithika

---

## Overview

This project demonstrates the design and implementation of a complete data engineering pipeline for financial time-series data.

The pipeline processes two years of daily stock price data for multiple tickers and produces clean, analysis-ready monthly summaries along with commonly used technical indicators.

The focus of this project is on:
- Correct time-series aggregation
- Data quality and validation
- Modular and readable Python code
- Practical financial analytics

---

## Problem Statement

The goal of this project is to build a reliable data pipeline that:

- Transforms daily stock price data into monthly aggregates
- Computes monthly OHLC values
- Calculates technical indicators such as SMA and EMA
- Produces structured outputs suitable for downstream analytics or modeling
---

## Solution Approach

The solution performs the following steps in sequence:

1. Load and preprocess the daily stock price data  
2. Resample the data to monthly frequency using **month-end dates**  
3. Compute monthly OHLC values:
   - **Open**: First trading day open price of the month  
   - **High**: Maximum price within the month  
   - **Low**: Minimum price within the month  
   - **Close**: Last trading day close price of the month  
4. Calculate technical indicators based on **monthly closing prices**:
   - SMA 10  
   - SMA 20  
   - EMA 10  
   - EMA 20  
5. Ensure exactly **24 months of data per ticker**  
6. Partition the final dataset by ticker  
7. Write the results to individual CSV files  
8. Validate output structure and row counts  

---
## Key Engineering Decisions

- Used month-end resampling to align with standard financial reporting
- Calculated indicators on monthly closing prices to reduce noise
- Enforced fixed 24-month output per ticker for consistency
- Added a separate validation script to ensure correctness and data integrity
- Partitioned output by ticker to simplify downstream consumption
---
## Project Structure

```text
FamPay Assessment/
├── main.py
├── validate_output.py
├── stock_data.csv
├── requirements.txt
├── .gitignore
├── output/
│   ├── result_AAPL.csv
│   ├── result_AMD.csv
│   ├── result_AMZN.csv
│   ├── result_AVGO.csv
│   ├── result_CSCO.csv
│   ├── result_MSFT.csv
│   ├── result_NFLX.csv
│   ├── result_PEP.csv
│   ├── result_TMUS.csv
│   └── result_TSLA.csv
└── README.md

```
---

## Requirements

- Python 3.8 or higher  
- pandas  

---

## Installation

Install the required dependency using pip:

```bash
pip install pandas
```

Or install from the requirements file:
```bash
pip install -r requirements.txt
```

---

## Dataset

Download the dataset from the following GitHub repository:

https://github.com/sandeep-tt/tt-intern-dataset

Save the file as `stock_data.csv` in the project root directory.


### Tickers Included

AAPL, AMD, AMZN, AVGO, CSCO, MSFT, NFLX, PEP, TMUS, TSLA

---

## Output Data Schema

Each output file contains **monthly aggregated data** with the following columns:


### Column Descriptions

- **date**: Month-end date  
- **open**: First trading day open price of the month  
- **high**: Highest price during the month  
- **low**: Lowest price during the month  
- **close**: Last trading day close price of the month  
- **sma_10**: 10-month simple moving average of closing price  
- **sma_20**: 20-month simple moving average of closing price  
- **ema_10**: 10-month exponential moving average of closing price  
- **ema_20**: 20-month exponential moving average of closing price  

Each ticker output contains **exactly 24 rows**, representing two years of monthly data.

---

## Running the Script

Execute the main processing script using:
```bash
python main.py
```

The script will:

- Load and preprocess the dataset  
- Generate monthly OHLC summaries  
- Compute technical indicators  
- Save results to the `output` directory  
- Print a validation report to the console  

---

### Validation Script

The project also includes a separate validation script to verify the correctness of the generated outputs.

Run the validation script using:

```bash
python validate_output.py





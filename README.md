# ST2195 Assignment 6

## Overview

This repository contains scripts and analysis for the sixth assignment of the ST2195 Programming for Data Science course. The assignment involves downloading the European Central Bank (ECB) speeches dataset and the daily EUR/USD reference exchange rate from the ECB Statistical Data Warehouse, performing data cleaning and analysis, and extracting insights related to the impact of ECB speeches on the exchange rate. The scripts provided in this repository have been shared by the class teacher, Inès Krissaane.

## Data

The datasets used in this analysis are:

- `speeches.csv`: Contains the date and contents of ECB speeches.[ECB speeches dataset](https://www.ecb.europa.eu/press/key/html/downloads.en.html).
- `fx.csv`: Contains the daily EUR/USD reference exchange rate. [Daily EUR/USD](https://data.ecb.europa.eu/data/datasets/EXR/EXR.D.USD.EUR.SP00.A).

These datasets can be downloaded from the ECB Statistical Data Warehouse. For the `speeches.csv` dataset, only the `date` and `contents` columns are retained.

## Scripts

The repository includes two scripts, one in Python and one in R, that perform the following operations:

1. Load and merge the datasets, keeping all information available for the dates in which there is a measurement in `fx.csv`.
2. Remove entries with obvious outliers or mistakes, if any.
3. Handle missing observations for the exchange rate by replacing any missing exchange rate with the latest information available. Entries without available replacement are removed entirely from the dataset.
4. Calculate the exchange rate return and extend the original dataset with the following variables:
   - `good_news`: Equal to 1 when the exchange rate return is larger than 0.5 percent, 0 otherwise.
   - `bad_news`: Equal to 1 when the exchange rate return is lower than -0.5 percent, 0 otherwise.
5. Remove the entries for which the `contents` column has NA values. Generate and store in CSV the following tables:
   - `good_indicators`: With the 20 most common words (excluding articles, prepositions, and similar connectors) associated with entries wherein `good_news` is equal to 1.
   - `bad_indicators`: With the 20 most common words (excluding articles, prepositions, and similar connectors) associated with entries wherein `bad_news` is equal to 1.

The scripts are:

- `st2195_assignment_6.ipynb`: Jupyter notebook with Python code.
- `st2195_assignment_6.Rmd`: R Markdown document with R code.

## Results

The analysis results are stored in the following CSV files:

- `good_indicators.csv`: Contains the 20 most common words associated with positive exchange rate returns.
- `bad_indicators.csv`: Contains the 20 most common words associated with negative exchange rate returns.

## Usage

To replicate the analysis, clone this repository, navigate to the directory containing the scripts, and run the Python and R scripts. Ensure that the required datasets are downloaded and saved as `speeches.csv` and `fx.csv` in the same directory.

## Dependencies

- Python:
  - pandas
  - matplotlib
- R:
  - dplyr
  - tidyr
  - zoo
  - text2vec
# Stock-Price-Prediction-Using-75-Financial-Ratios

## Overview
Built an end-to-end predictive modeling workflow in R to analyze how financial ratios influence stock performance across Dow 30 companies.

This project combines financial ratio data with historical stock prices to evaluate multiple modeling approaches and identify which financial indicators are most predictive of stock performance.

## Business Question
This project explores two primary questions:

* Which financial ratios are most predictive of stock prices across Dow 30 companies?
* Do different companies or industries rely on different financial indicators?

The goal was to better understand whether financial fundamentals can help explain stock performance and support more data-driven investment analysis.

## Data
1. Financial ratio dataset from [Wharton Research Data Services](https://wrds-www.wharton.upenn.edu/)
    - Dow 30 companies' monthly financial ratio data from January 2010 to December 2022
      - Dataset contains 75 financial ratio variables
    - Examples of ratios included:
      - profitability ratios
      - liquidity ratios
      - leverage ratios
      - valuation ratios
      - operational efficiency ratios
2. Stock price dataset from [Yahoo Finance via R tidyquant](https://www.dropbox.com/s/we2ed1i1t98cin9/stock_prices.csv?dl=0).
    - Dow 30 companies' monthly stock price data from January 2010 to December 2022

## Methodology
* Data Cleaning:
    - Removed rows with missing stock prices
    - Removed financial ratio features with high missingness
    - Imputed remaining missing values
    - Removed unusable variables with excessive missing data
    
* Data Preparation:
    - Merged stock price data with financial ratio data
    - Normalized stock prices for model comparison
    - Prepared features for predictive modeling
    
* Feature Engineering:
    - Evaluated dimensionality reduction techniques
    - Selected features for final modeling workflow
      
## Model Comparison
* PCA:
    - Tested PCA for dimensionality reduction.
    - PCA did not yield strong results because variance was distributed relatively evenly across multiple principal components, making it difficult to clearly identify the most critical financial ratios.
    - PCA was not selected for the final model.
* Lasso Regression:
    - Used cross-validation to identify the optimal lambda value.
    - Result: R² = 0.534
    - Lasso improved feature selection but underperformed compared to Random Forest.
* Random Forest:
    - Built Random Forest models using train/test split methodology.
    - Result: R² = 0.975
    - Random Forest models performed best since they captured non-linear relationships, well-handled high-dimensional features, and provided feature importance rankings.
    - Random Forest was selected as the final model.

## Key Findings
* The most important financial indicators included:
    - Price-to-Book Ratio
    - Book-to-Market Ratio
    - Debt-to-Capital Ratio
    - Long-Term Debt to Book Equity
    - Operating Profit Margin Before Depreciation
* Additionally:
    - Sales and earnings-related ratios were frequently important across companies.
    - Some industries relied more heavily on debt-related ratios.
    - Different companies showed unique financial drivers of stock performance.
      
## Limitations
* Dataset only includes Dow 30 companies.
* Financial ratios alone cannot capture all market behavior.
* Stock prices are influenced by external macroeconomic factors not included in this analysis.
* High historical model performance may not generalize to future market conditions.

## My contribution
* This project was originally completed in an academic team setting and later reorganized into an individual portfolio project to better showcase my technical work.
* My contributions included:
    - Data cleaning and preprocessing
    - Missing value imputation
    - Model experimentation
    - Model evaluation
    - Feature importance analysis
    - Data visualization

## Tools
* R (RStudio): `tidyquant`, `tidyverse`, `glmnet`, `randomForest`, `ggplot2`, R markdown

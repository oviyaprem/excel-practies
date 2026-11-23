# E-Commerce Sales Analysis

Module-End Assignment: *Data Cleaning, Analysis & Visualization with Excel* (Data Analytics).

## Files

| File | Description |
|---|---|
| `Oviya Premkumar Ecommerce_Sales_Dataset_updated .xlsx` | Final Excel workbook, one tab per step |
| `Oviya Premkumar E-commerce Summary-2.docx` | One-page summary of decisions and findings (page 1), followed by screenshots of the cleaning log, cleaned data, statistics, insights and dashboard |
| `README.md` | This file |

## Workbook tabs

| Tab | Assignment requirement |
|---|---|
| `Raw_Data`, `Customer_Dim`, `Product_Dim`, `Store_Dim`, `Sales_Fact` | Data import and organisation (Excel Tables) |
| `Data_Cleaning` | Cleaning log, validation checks and every value that was filled in |
| `Master_Sales` | Tables combined with `XLOOKUP` |
| `Calc_Columns` | Formulas: `TEXT`, `YEAR`, `IF`, `INDEX/MATCH` |
| `Analysis` | Descriptive statistics (mean, median, mode, standard deviation, variance, skewness, kurtosis, quartiles) |
| `Insights` | `SUMIFS`, `COUNTIFS`, `AVERAGEIFS`, Category × Region summary, sparklines, Top 5 products |
| `Dashboard` | PivotTables, slicers, PivotCharts, KPI cards and charts |

## Steps

1. **Import** the four tables: customers (500), products (100), stores (20) and sales (2,000 orders).
2. **Clean**
   * `C-` / `P-` ID prefixes changed to `CUST` / `PROD` with `SUBSTITUTE`.
   * Customer names tidied with `PROPER(TRIM(...))`, removing titles and suffixes.
   * Country spellings standardised, then the column removed (every value is `USA`).
   * Blank `Loyalty_Level` set to `Not Enrolled`; blank product `Cost` filled with the median.
   * 16 blank sales values (in 15 orders) recalculated from `Total = Quantity × Unit_Price × (1 − Discount)` (yellow cells).
   * No duplicates found. Data-validation rules added to Quantity, Discount and Payment_Type.
3. **Combine** the tables in `Master_Sales` with `XLOOKUP`.
4. **Summarise** with formulas, descriptive statistics and three PivotTables (product, region, year).
5. **Visualise** on the `Dashboard`: pie, column and line PivotCharts with two slicers (`Payment_Type`, `Store Region`), plus KPI cards and three more charts (Category × Region, monthly trend, Top 5 products).

## Key results

* Revenue 2,174,395 from 2,000 orders; average order value 1,087.20.
* North, South and East each earn about 29% of revenue; West earns 12.4%.
* Sports and Electronics are the top categories; PayPal is the top payment type.

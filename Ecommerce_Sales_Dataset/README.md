# E-Commerce Sales Data Analysis

Module-End Assignment: *Data Cleaning, Analysis & Visualization with Excel* (see `DA V8 M1.pdf`).

**Files**

* `Oviya Premkumar Ecommerce_Sales_Dataset_updated.xlsx` – final workbook
* `Oviya Premkumar E-commerce Summary.docx` – one-page summary of decisions and findings

## Workbook tabs

| Tab | Purpose |
|---|---|
| `Raw_Data` | Original data, kept for reference |
| `Customer_Dim`, `Product_Dim`, `Store_Dim`, `Sales_Fact` | Imported tables (Excel Tables) with cleaning columns |
| `Master_Sales` | Sales joined with customer, product and store details using `XLOOKUP` |
| `Data_Cleaning` | Cleaning log, validation checks and every filled-in value |
| `Calc_Columns` | Row-level formulas (`TEXT`, `YEAR`, `IF`, `XLOOKUP`) |
| `Analysis` | Descriptive statistics |
| `Insights` | KPIs, summary tables, sparklines, written findings |
| `Dashboard` | PivotTables, slicers, PivotCharts, KPI strip and charts |

## Steps

1. **Import and organise** – the four tables (customer, product, store, sales) are Excel Tables.
2. **Clean**
   * `C-` / `P-` ID prefixes changed to `CUST` / `PROD` with `SUBSTITUTE`.
   * Customer names tidied with `PROPER(TRIM(...))`, removing titles and suffixes.
   * Country spellings standardised, then the column removed (every value is `USA`).
   * Blank `Loyalty_Level` set to `Not Enrolled`; blank product `Cost` filled with the median.
   * 15 blank sales values recalculated from `Total = Quantity × Unit_Price × (1 − Discount)` (highlighted yellow).
   * No duplicates found. Data-validation rules added to Quantity, Discount and Payment_Type.
3. **Combine** – `Master_Sales` uses `XLOOKUP` on the cleaned IDs.
4. **Statistics** – mean, median, mode, standard deviation, variance, skewness, kurtosis and quartiles in the Analysis ToolPak layout, using formulas.
5. **Summarise and visualise** – 3 PivotTables (product, region, year), 2 slicers (`Payment_Type`, `Store Region`), pie, column and line PivotCharts, plus KPI cards and 3 more charts (Category × Region, monthly trend, Top 5 products).

## Key results

* Revenue 2,174,395 from 2,000 orders; average order value 1,087.20.
* North, South and East each earn about 29%; West earns 12.4%.
* Sports and Electronics are the top categories; PayPal is the top payment type.

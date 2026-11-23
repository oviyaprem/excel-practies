# E-Commerce Sales Data Analysis

Module-End Assignment: *Data Cleaning, Analysis & Visualization with Excel* (Data Analytics).

## Files

| File | Description |
|---|---|
| `Oviya Premkumar Ecommerce_Sales_Dataset_updated .xlsx` | Excel workbook with the cleaning, lookups, statistics, pivot tables and dashboard |
| `Oviya Premkumar E-commerce Summary-2.docx` | Summary document with screenshots |
| `README.md` | This file |

## Workbook tabs

`Raw_Data`, `Customer_Dim`, `Product_Dim`, `Store_Dim`, `Sales_Fact`, `Master_Sales`, `Data_Cleaning`, `Analysis`, `Dashboard`

## Steps performed

### 1. Data import and organisation

* Imported the 4 star-schema tables: `Customer_Dim` (500 customers), `Product_Dim` (100 products), `Store_Dim` (20 stores) and `Sales_Fact` (2,000 orders).

### 2. Data cleaning (`Customer_Dim` and `Product_Dim`)

* **Customer ID:** replaced `C-` with `CUST`: `=SUBSTITUTE(A2, "C-", "CUST")`
* **Customer name:** removed extra spaces and titles, fixed capitalisation: `=PROPER(TRIM(SUBSTITUTE(SUBSTITUTE(C2, "dr. ", ""), "Ms. ", "")))`
* **Product ID:** replaced `P-` with `PROD` to match `Sales_Fact`: `=SUBSTITUTE(A2, "P-", "PROD")`
* **Missing product cost:** filled with the column median: `=IF(G2="", MEDIAN(G:G), G2)`

### 3. Combining tables (`Master_Sales`)

`Sales_Fact` joined to the other tables with `XLOOKUP`:

* Customer name: `=XLOOKUP(C2, Customer_Dim!B:B, Customer_Dim!D:D)`
* Product name: `=XLOOKUP(D2, Product_Dim!B:B, Product_Dim!C:C)`
* Store region: `=XLOOKUP(E2, Store_Dim!A:A, Store_Dim!C:C)`

### 4. Descriptive statistics (`Analysis`)

Calculated on `Total_Amount`:

| Statistic | Formula |
|---|---|
| Mean | `=AVERAGE(Sales_Fact!J:J)` |
| Median | `=MEDIAN(Sales_Fact!J:J)` |
| Standard deviation | `=STDEV.P(Sales_Fact!J:J)` |
| Minimum | `=MIN(Sales_Fact!J:J)` |
| Maximum | `=MAX(Sales_Fact!J:J)` |

### 5. Pivot tables and dashboard (`Dashboard`)

* 3 PivotTables of `Sum of Total_Amount` by **product**, **store region** and **order year (2023–2025)**.
* 3 chart types linked to the pivots: pie chart, 3D column chart and line chart.
* 2 slicers (`Payment_Type` and `Store Region`) that filter the pivots and charts.

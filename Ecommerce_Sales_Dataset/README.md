# E-Commerce Sales Data Analysis Project

## Steps Performed to Create the Results

### Step 1: Data Import & Organization

* Imported the 4 base star-schema tables (`Customer_Dim`, `Product_Dim`, `Store_Dim`, and `Sales_Fact`).

* Organized the workflow across separate tabs (`Raw_Data`, `Master_Sales`, `Data_Cleaning`, `Analysis`, and `Dashboard`).

### Step 2: Data Cleaning (`Customer_Dim` & `Product_Dim`)

* **Customer ID Standardization:** Replaced `C-` prefixes with `CUST` using:

  ```
  =SUBSTITUTE(A2, "C-", "CUST")
  ```

* **Customer Name Formatting:** Removed extra spaces, stripped honorifics (`dr. `, `Ms. `), and applied proper capitalization using:

  ```
  =PROPER(TRIM(SUBSTITUTE(SUBSTITUTE(C2, "dr. ", ""), "Ms. ", "")))
  ```

* **Product ID Standardization:** Replaced `P-` prefixes with `PROD` to match `Sales_Fact` using:

  ```
  =SUBSTITUTE(A2, "P-", "PROD")
  ```

* **Missing Cost Imputation:** Filled missing `Cost` values with the column median (`242.97`) using:

  ```
  =IF(G2="", MEDIAN(G:G), G2)
  ```

### Step 3: Combining Tables (`Master_Sales`)

* Merged dimension attributes into `Sales_Fact` using `XLOOKUP`:

  * **Customer Name:** `=XLOOKUP(C2, Customer_Dim!B:B, Customer_Dim!D:D)`

  * **Product Category (pulls Product Name):** `=XLOOKUP(D2, Product_Dim!B:B, Product_Dim!C:C)`

  * **Store Region:** `=XLOOKUP(E2, Store_Dim!A:A, Store_Dim!C:C)`

### Step 4: Descriptive Statistics (`Analysis`)

* Calculated summary metrics on `Total_Amount` (`Sales_Fact!J:J`, stored in `General` number format):

  * **Mean:** `=AVERAGE(Sales_Fact!J:J)` → `1087.63`

  * **Median:** `=MEDIAN(Sales_Fact!J:J)` → `868.72`

  * **Standard Deviation:** `=STDEV.P(Sales_Fact!J:J)` → `819.92`

  * **Minimum:** `=MIN(Sales_Fact!J:J)` → `18.46`

  * **Maximum:** `=MAX(Sales_Fact!J:J)` → `3908.24`

### Step 5: Pivot Tables & Dashboard (`Dashboard`)

* Built **3 Pivot Tables** summarizing `Sum of Total_Amount` by **Product**, **Store Region**, and **Order Year (2023–2025)**.

* Created **3 chart types** linked to the Pivot Tables: a **Pie Chart**, a **3D Bar/Column Chart**, and a **Line Chart**.

* Added **2 Slicers** (`Payment_Type` and `Store Region`) to dynamically filter the Pivot Tables and charts.
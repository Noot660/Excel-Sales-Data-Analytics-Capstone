# Advanced Excel Sales & Returns Data Analytics (Capstone Project)

## 📌 Project Overview
This project demonstrates a complete end-to-end Data Analytics workflow using **Microsoft Excel** and **Power Query**. The objective was to extract a highly inconsistent, messy sales dataset and a separate returns dataset, perform comprehensive ETL (Extract, Transform, Load) processing, integrate the tables, and build an analytical summary table to uncover critical business insights regarding revenue and losses.

## 🛠️ Tech Stack & Skills Demonstrated
*   **Tools:** Microsoft Excel, Power Query Editor
*   **Data Analysis Techniques:** ETL, Data Cleaning, Advanced Conditional Logic, Data Integration (Merging/VLOOKUP style), Pivot Tables & Business Intelligence.

## 🧹 The ETL & Data Cleaning Process (Power Query)
The raw data contained multiple anomalies that would corrupt any standard analytical formulas. The following structural transformations were implemented:
1.  **Text Standardization:** Applied `Trim` and `Capitalize Each Word` on `Customer_Name` and `Region` columns to remove redundant spaces and fix inconsistent casing (e.g., 'north' vs 'North').
2.  **Advanced Value Replacement:** Addressed incomplete product IDs (e.g., `02` instead of `PROD_02`). Used Advanced Power Query options with **"Match entire cell contents"** to avoid string corruption (preventing double prefixes like `PROD_PROD_02`).
3.  **Date Standardisation:** Fixed a critical timeline issue where dates used mixed separators (dots, dashes, slashes). Replaced anomalies to uniform delimiters and converted the data type to standard `Date`. Missing date entries were intentionally left as `null` to preserve reporting integrity.
4.  **Data Type Enforcement:** Cleaned and cast the `Quantity` column into a Whole Number format after removing leading/trailing spaces, enabling mathematical computations.

## 🔗 Data Integration & Advanced Calculations
*   **Table Merging:** Performed a **Left Outer Join** to merge the Sales dataset with the Returns dataset using `Invoice_No` as the primary key.
*   **Custom Column (Total Revenue):** Calculated gross revenue using: `[Quantity] * [Price_Per_Unit]`
*   **Conditional Logic (Net Revenue):** Created a robust financial column to track actual kept revenue by applying the following dynamic logic:
    `if [Return_Reason] = null then [Total_Revenue] else 0`

## 📊 Key Business Insights (Pivot Table Summary)
After successfully loading the processed data into Excel, a Pivot Table was constructed to analyze financial leaks across regions:
*   **Total Gross Revenue:** $1,069.50
*   **Total Net Revenue:** $713.00
*   **Total Return Financial Loss:** $356.50

### 🚨 Critical Regional Discoveries:
1.  **The East Region Crisis:** The East region generated a massive gross revenue of **$450.00**, but suffered a shattering loss of **$300.00** due to customer returns explicitly labeled as **"Damaged"**. This flags an urgent operational bottleneck in delivery quality or warehouse management in the East.
2.  **The South Star Performer:** The South region brought in **$275.00** in gross revenue with **0% returns**, establishing itself as the most reliable and efficient region in terms of customer satisfaction and product handling.
3.  **Central Efficiency:** Central region maintained a flawless record with **$100.00** gross sales and zero financial leaks from returns.

---
## 📁 Repository Structure
*   `Excel_Sales_Analytics_Dashboard.xlsx` - The final production workbook containing the Power Query connections and the Pivot Table report.
*   `raw_sales_data.csv` - The original uncleaned transactional sales dataset.
*   `raw_returns_data.xlsx` - The original logistics return reasons workbook.

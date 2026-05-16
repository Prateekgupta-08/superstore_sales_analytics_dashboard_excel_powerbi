# Global Superstore Sales Analysis — Power BI Dashboard

A full end-to-end sales analytics project built in Power BI using the Global Superstore dataset. The report was designed to give the team a single place to track sales performance, profitability, shipping behavior, and customer trends across global markets — without having to touch the raw data file.

---

## Background

The Global Superstore dataset is a large transactional retail dataset covering orders placed across **147 countries** from **2011 to 2014**. Before any visuals were built, the raw Excel file went through a complete ETL process in Power Query — handling data type issues, removing irrelevant columns, and shaping the data into a clean, reliable model.

The end goal was a dashboard the team can actually use to ask questions like: which markets are profitable, which product categories are dragging margins down, and where should we focus shipping and logistics attention.

---

## Dataset

**Source file:** `global_superstore.xlsx`

| Detail | Value |
|---|---|
| Total Rows | 51,290 orders |
| Time Period | 2011 – 2014 |
| Countries | 147 |
| Markets | US, EU, APAC, LATAM, EMEA, Africa, Canada |
| Customer Segments | Consumer, Corporate, Home Office |
| Product Categories | Furniture, Office Supplies, Technology |
| Sub-Categories | 17 (Phones, Chairs, Binders, Storage, Tables, etc.) |
| Ship Modes | Standard Class, Second Class, First Class, Same Day |
| Order Priorities | Critical, High, Medium, Low |

**Full list of columns in the dataset:**

Row ID, Order ID, Order Date, Ship Mode, Customer ID, Customer Name, Segment, City, State, Country, Postal Code, Market, Region, Product ID, Category, Sub-Category, Product Name, Sales, Quantity, Discount, Profit, Shipping Cost, Order Priority

---

## ETL Process (Power Query)

The raw Excel file had a number of issues that needed sorting before the data could be trusted in visuals. Here's what was done inside Power Query Editor:

1. **Connected the Excel source** and loaded all 51,290 rows into Power Query
2. **Set correct data types** — Order Date was stored as a number (Excel serial date) and had to be converted to a proper Date type; Sales, Profit, Discount, and Shipping Cost set as Decimal Number; Quantity set as Whole Number
3. **Removed the Postal Code column** — too many nulls across international records, not useful for this analysis
4. **Checked for and removed duplicate Row IDs** to ensure row-level integrity
5. **Renamed columns** where the original names were ambiguous or inconsistently cased
6. **Filtered out any fully blank rows** that appeared at the bottom of the sheet
7. **Verified the final row count** matched the source before closing and applying

The cleaned model was then loaded into Power BI's data model for relationship management and DAX measures.

---

## Dashboard Overview

### Page 1 — Sales & Profit Overview

A global summary of how the business performed across the full 4-year period.

- Total Sales, Total Profit, Total Quantity, and Total Orders as KPI cards
- Sales and Profit trend by Year (line chart)
- Sales by Market (bar chart — comparing US, EU, APAC, LATAM, EMEA, Africa, Canada)
- Profit by Category (Furniture, Office Supplies, Technology)
- Top 10 Sub-Categories by Sales

### Page 2 — Geographic Analysis

A map-driven view to understand where the business is active and where profit is being generated.

- Sales by Country (filled map)
- Profit by Region breakdown
- Shipping Cost vs Sales scatter by Market
- Order Priority distribution (Critical / High / Medium / Low)

### Page 3 — Customer & Segment Analysis

Drilling into who is buying and how they behave.

- Sales and Profit by Segment (Consumer, Corporate, Home Office)
- Top customers by Sales and Profit
- Segment breakdown by Ship Mode
- Repeat order analysis by Customer ID

### Page 4 — Product Performance

Understanding which products and categories are driving value and which are not.

- Category and Sub-Category sales matrix
- Profit margin heatmap by Sub-Category
- Discount impact on Profit (scatter chart)
- Lowest margin Sub-Categories flagged for review

---

## Key Numbers

| Metric | Value |
|---|---|
| Total Sales | $12,642,501 |
| Total Profit | $1,467,457 |
| Total Orders | 25,035 |
| Total Units Sold | 178,312 |
| Unique Customers | 1,590 |
| Unique Products | 10,292 |
| Countries Covered | 147 |

---

## Key Insights from the Data

- **Technology drives the most revenue** but Office Supplies holds better margins at scale due to lower COGS.
- **Furniture is a consistent margin problem** — specifically Tables, which shows negative profit across multiple markets even with decent sales volume. Heavy discounting is the main culprit.
- **The US market leads in both Sales and Profit**, but APAC is growing faster in order volume.
- **Africa and Canada are small markets** but show healthier profit-to-sales ratios — potentially worth expanding.
- **High discount rates directly kill profit margins** — visible in the scatter analysis where orders above 30% discount almost always result in negative profit.
- **Standard Class shipping dominates** (~60% of orders), but Critical priority orders still frequently use it, suggesting a disconnect between priority labeling and actual fulfillment behavior.
- **Consumer segment is the largest by volume**, but Corporate customers have higher average order values and better margin per transaction.

---

## Project Structure

```
global-superstore-analysis/
├── Sample_Superstore_Analysis_Report.pbix     # Power BI report file
├── data/
│   └── global_superstore.xlsx                  # Source dataset
├── screenshots/
│   ├── page1_overview.png
│   ├── page2_geo.png
│   ├── page3_customers.png
│   └── page4_products.png
└── README.md
```

---

## How to Use

1. Clone or download this repository
2. Open `Sample_Superstore_Analysis_Report.pbix` in Power BI Desktop
3. If the data source path is broken, go to **Home > Transform Data > Data Source Settings** and update the path to point to your local `data/global_superstore.xlsx`
4. Click **Refresh** and the report will load
5. Use the slicers on each page to filter by Market, Segment, Category, Year, or Region

---

## Tools Used

- **Power BI Desktop** — data modeling, ETL, DAX measures, and dashboard development
- **Power Query (M Language)** — data cleaning and transformation pipeline
- **Microsoft Excel** — source data format (global_superstore.xlsx)
- **Bing Maps** — integrated map visual for geographic sales distribution

---


## Author

Built as part of a data analytics portfolio project, demonstrating end-to-end Power BI development from raw data ingestion and Power Query ETL through to a multi-page interactive dashboard built for business decision-making.

https://github.com/Prateekgupta-08/Retail-Sales-Analytics-Dashboard/blob/main/Business_Use_Case_Superstore.docx
https://github.com/Prateekgupta-08/Retail_Sales_Analytics_Dashboard/blob/main/Screenshot%202026-05-16%20080546.png

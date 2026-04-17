# Sales Analytics Dashboard (Power BI)

The goal of this project is to modernize internet sales reporting by replacing static, hard-to-read reports with interactive dashboards that support faster and more informed decision-making.

This project presents an interactive Sales Analytics Dashboard built in Power BI, based on the AdventureWorks dataset.
The report focuses on analyzing sales performance, customer behavior, and product-level insights across time, categories, and geographies.

The dashboard is divided into three main sections:

Sales Overview
Customer Details
Product Details

Each page is fully interactive and responds to filters such as year, month, category, and product attributes.

## Business Value
This dashboard enables:

- tracking performance against budget
- identifying top-performing customers and products
- spotting seasonal trends
- analyzing geographic sales distribution

The report allows dynamic filtering by **year and month**, and provides a clear view of:
- total sales vs budget
- top customers and products
- product category distribution
- sales trends over time
- geographic distribution of customers

Because sales representatives manage different products and client portfolios, the solution must allow flexible filtering to analyze performance at both individual and aggregate levels.

Additionally, the company evaluates its performance against predefined budget targets (provided in a separate dataset). 
The analysis should include comparisons to the 2021 budget, along with historical data covering the two preceding years to provide meaningful context and trend insights.

-------------------------------------------------------------------------

## User Stories:


<img width="581" height="328" alt="image" src="https://github.com/user-attachments/assets/44fc69d9-0796-4816-abe5-25c0ecf606a6" />

-------------------------------------------------------------------------

# Sales Overview

This page provides a high-level summary of business performance.
<img width="1445" height="803" alt="image" src="https://github.com/user-attachments/assets/b2737a24-9141-4848-ac0f-30efc7454be0" />

Key elements:
- Total Sales KPI with comparison to budget
- Sales vs Budget trend over months
- Top 10 Customers and Top 10 Products
- Sales by Product Category (distribution)
- Geographical sales map
Insights:
Clear seasonality — sales increase significantly toward the end of the year
Product category Bikes dominates total revenue
Strong concentration of sales in specific regions


# Customer Details
<img width="1450" height="816" alt="image" src="https://github.com/user-attachments/assets/e72100da-9206-4f94-bb33-2c9d2df56c7f" />

This section focuses on customer-level analysis.

Key elements:
- Total Sales and Budget KPIs
- Top 10 Customers ranking
- Sales trend by day of week
- Sales distribution by Customer City (map)
- Detailed customer table with monthly breakdown
Insights:
Sales vary depending on the day of the week
A small group of customers generates a large portion of revenue
Geographic clustering of customers is clearly visible

# Product Details
<img width="1441" height="811" alt="image" src="https://github.com/user-attachments/assets/561c2264-d346-4b18-8eaf-8b490dcd1b85" />

This page dives deeper into product performance.

Key elements:
- Top 10 Best Selling Products
- Bottom 10 Worst Selling Products
- Sales by Quarter (multi-year comparison)
- Sales distribution by Subcategory
- Product table with descriptions
Insights:
Significant performance gap between top and bottom products
Strong growth in Q4 across all years
Sales heavily concentrated in specific subcategories

## Interactivity

The dashboard includes multiple filters:

- Year
- Month
- Product Category
- Product attributes (color, size, model)

All visuals are interconnected, enabling dynamic exploration of data.

## Key Takeaways
Sales are highly seasonal, with peak performance in Q4
A limited number of products and customers drive most revenue
Category dominance (especially Bikes) can mask performance of other segments
Underperforming products are clearly identifiable for optimization

## Tools & Technologies
Power BI
DAX (for KPI calculations and measures)
SQL (data extraction and transformation)
AdventureWorks dataset

--

## Data Model

The report is built using a **star schema**:

### Fact Tables:
- `FACT_InternetSales`
- `FACT_Budget`

### Dimension Tables:
- `DIM_Calendar`
- `DIM_Customers`
- `DIM_Products`

Relationships:
- DIM_Calendar -> FACT_InternetSales (DateKey)
- DIM_Calendar -> FACT_Budget (Date)
- DIM_Products -> FACT_InternetSales (ProductKey)
- DIM_Customers -> FACT_InternetSales (CustomerKey)

<img width="1142" height="776" alt="image" src="https://github.com/user-attachments/assets/b2c9f34b-b3aa-4915-9338-cb6ed42471de" />

---

## Key Measures (DAX)

```DAX
Sales = SUM(FACT_InternetSales[SalesAmount])

Budget_Amount = SUM(FACT_Budget[Budget])

Sales vs Budget = [Sales] - [Budget_Amount]

Sales vs Budget % = 
DIVIDE([Sales], [Budget_Amount]) - 1




# Sales Overview Dashboard (Power BI)

The goal of this project is to modernize internet sales reporting by replacing static, hard-to-read reports with interactive dashboards that support faster and more informed decision-making.

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


**User Stories:**


<img width="581" height="328" alt="image" src="https://github.com/user-attachments/assets/44fc69d9-0796-4816-abe5-25c0ecf606a6" />

-------------------------------------------------------------------------

## Tools & Technologies
- Power BI
- Power Query (ETL)
- DAX
- SQL (data extraction & transformation)

---
## Key Features

### Dynamic KPI Card
- Displays total **Sales**
- Shows **Budget** comparison
- Highlights variance (positive/negative) with visual indicator

---

### Time Analysis
- Interactive slicers for:
  - Year
  - Month
- Line chart:
  - Sales vs Budget over time
  - Easy trend comparison

---

### Top Performers
- **Top 10 Customers**
- **Top 10 Products**
- Conditional formatting (heatmap style) for quick comparison

---

### Product Analysis
- Donut chart showing **Sales by Product Category**
- Quick identification of dominant categories

---

### Geographical Insights
- Map visualization of **Sales by Customer City**
- Helps identify regional patterns

---

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




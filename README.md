# DataCo Global Sales & Customer Intelligence Report (January 2015 – January 2018)

![Header_image](<DataCo Global Header.jpg>)

## Executive Summary 
DataCo Global processed **180,519** order items across **65,752** unique orders between **January 2015 and January 2018**, earning **$36.78m** in gross sales, **$3.97m** in net profit (10.78% profit margin), and **384,079** units sold. Full-year sales held steady between 2015 ($12.34m) and 2016 ($12.30m, -0.30% YoY) before slipping 4.03% in 2017 ($11.81m), while total profit stayed nearly flat at $1.30m (-0.46% YoY).

Three issues stand out. Sales rely heavily on **Europe ($10.87m)** and **LATAM ($10.28m)**, the **Consumer segment (51.9% of sales)**, and the **Fan Shop department (46.5% of sales)**. Meanwhile, **54.8%** of all shipments (98,977 items) face late delivery risk, with **First Class (95.3% late risk)** and **Second Class (76.6% late risk)** routinely missing promised delivery windows. In addition, **18.7%** of order items (33,784 rows) lost money, cutting **$3.88m** from total profit. Updating shipping promises, limiting steep discounts on unprofitable items, and improving fulfillment in Western Europe and Central America would protect profit margins and improve on-time delivery.

## Business Context
DataCo Global is a multinational B2C retailer selling sports, apparel, outdoor, and lifestyle products across five global markets. With thousands of customers and 118 products across 50 categories, management lacked a single reporting model to track sales trends, regional profit, customer segments, and shipping delays. Leadership needed a clean, two-page Power BI dashboard built on a star schema to monitor Year-over-Year (YoY) KPIs and spot late delivery risks across regions and product lines. 

## Objectives
- What are DataCo Global's headline sales, profit, quantity sold, and average delivery time, plus their Year-over-Year (YoY) changes?
-	Which markets, regions, departments, and products bring in the most sales and profit?
-	How do Consumer, Corporate, and Home Office customer segments compare?
-	Where are late delivery risks and shipping delays most common across shipping modes, regions, and product categories? 


## Data Overview 
The data is DataCo Global's order log exported as an Excel file containing **180,519 rows** across **50 columns**, covering **1 January 2015 to 31 January 2018** (three full years from 2015 to 2017 plus January 2018). It spans **65,752** unique orders, **20,652** customers across **3** segments, **118** products across **50** categories and **11** departments, and **64,867** location keys across **5** global markets, **23** order regions, and **164** countries.

## Key Findings
-	Total gross sales reached **$36.78m** with **$3.97m** in net profit (10.78% margin) across 384,079 units sold; full-year 2017 sales fell 4.03% YoY ($11.81m vs. $12.30m in 2016) while profit dipped only 0.46% YoY ($1.30m vs. $1.31m).
-	Actual delivery took 3.50 days on average against a 2.93-day target, leaving 54.8% of all order items (98,977) flagged for late delivery risk.
-	**First Class** (95.3% late risk; 2.00 actual vs. 1.00 expected days) and **Second Class** (76.6% late risk; 3.99 actual vs. 2.00 expected days) cause most missed delivery targets.
-	Europe ($10.87m; 29.6% of sales) and LATAM ($10.28m; 27.9% of sales) lead total revenue, with Western Europe ($5.89m) and Central America ($5.67m) ranking as the top order regions.
-	Consumer buyers bring in 51.9% of sales ($19.10m) and 52.3% of profit ($2.07m), ahead of Corporate ($11.17m) and Home Office ($6.52m).
-	Fan Shop ($17.11m; 46.5% of sales) and Apparel ($7.98m; 21.7% of sales) lead department revenue, while the Field & Stream Sportsman 16 Gun Fire Safe is the top product ($6.93m sales; $756.2k profit).
-	33,784 order items (18.7% of rows) had negative profit totaling -$3.88m, heavily reducing overall margin.

## Dashboard

![Dashboard](<DataCo Global Dashboard.png>)

## Link To Power BI Report
Click [here](https://app.powerbi.com/view?r=eyJrIjoiYTEyMjg3YmQtYTYzZC00OWU0LThjMGUtYjZhNDU5ZjgyYjUzIiwidCI6ImFkNTcwZDE3LWE1ZWQtNDAzMC1iMjVlLTE0NWQyNjIyMDYwYSJ9) to access the full Report.

## Data Cleaning and Transformation 
All cleaning and data modeling steps were done in Power Query and DAX to turn the flat 50-column file into a star schema:
-	Checked primary keys: confirmed all 180,519 FactSales ID values are unique with no duplicate rows.
-	Handled missing values: replaced 8 blank entries in Customer Lname with "Unknown" and kept 3 missing values in Customer Zipcode as null so map visuals remain accurate.
-	Fixed data types: converted Order Date and Shipment Date from Excel serial numbers into proper Date columns, and set currency, whole number, and flag types across all metrics.
-	Standardized text values: trimmed extra spaces and cleaned inconsistent location names (such as changing "EE. UU." to "United States" and fixing double spaces in "South of USA").
-	Built a Star Schema: split the flat dataset into FactSales (sales metrics, foreign keys, and shipping fields) connected via one-to-many relationships to DimCustomer (20,652 customers), DimProduct (118 products), DimLocation (64,867 locations), and a custom DimDate calendar table (Year, Quarter, Month, Month Name, Week Number, Day of Week). 

## Detailed Findings & Analysis
### Headline Performance & YoY Trends 
Across the full period, DataCo Global recorded **$36,784,735.01** in gross sales ($33,054,402.38 net of item discounts), **$3,966,902.97** in net profit, and **384,079** units sold with an average delivery time of 3.50 days:
-	2015: $12.34m sales | $1.32m profit | 138,480 units | 3.50 avg delivery days.
-	2016: $12.30m sales (-0.30% YoY) | $1.31m profit (-0.66% YoY) | 137,352 units (-0.81% YoY) | 3.49 avg delivery days (-0.19% YoY).
-	2017: $11.81m sales (-4.03% YoY) | $1.30m profit (-0.46% YoY) | 106,124 units (-22.74% YoY) | 3.50 avg delivery days (+0.29% YoY).
-	January 2018 (partial year): $331.7k sales | $33.8k profit | 2,123 units (down 67.8% from January 2017's $1.03m because the active catalog narrowed to single-unit technology, apparel, and specialty items).
### Market & Regional Contribution
-	Europe: $10.87m sales (29.6%), $1.17m profit (10.76% margin), 55.2% late delivery risk.
-	LATAM: $10.28m sales (27.9%), $1.12m profit (10.93% margin), 54.4% late delivery risk.
-	Pacific Asia: $8.27m sales (22.5%), $857.8k profit (10.37% margin), 55.0% late delivery risk.
-	USCA: $5.07m sales (13.8%), $564.3k profit (11.14% margin — highest regional margin), 54.8% late delivery risk.
-	Africa: $2.29m sales (6.2%), $252.1k profit (10.99% margin), 54.6% late delivery risk.
By order region, Western Europe ($5.89m sales; $625.4k profit) and Central America ($5.67m sales; $616.3k profit) generate 31.4% of global revenue, followed by South America ($2.96m), Northern Europe ($2.16m), Southern Europe ($2.05m), and Oceania ($2.02m).
### Product, Category & Department Breakdown 
Sales are heavily concentrated in sports, outdoor, and fan gear:
-	Top Departments: Fan Shop ($17.11m sales; $1.83m profit), Apparel ($7.98m sales; $881.9k profit), Golf ($4.61m sales; $497.5k profit), and Footwear ($4.01m sales; $410.2k profit) account for 91.6% of total company sales.
-	Top Categories: Fishing ($6.93m sales; $756.2k profit), Cleats ($4.43m sales; $494.6k profit), Camping & Hiking ($4.12m sales; $427.5k profit), Cardio Equipment ($3.69m sales; $383.0k profit), and Women's Apparel ($3.15m sales; $350.4k profit).
-	Top Products: Field & Stream Sportsman 16 Gun Fire Safe ($6.93m sales; 18.8% of total sales), Perfect Fitness Perfect Rip Deck ($4.42m sales), Diamondback Women's Serene Classic Comfort Bike ($4.12m sales), and Nike Men's Free 5.0+ Running Shoe ($3.67m sales).
### Customer Segment Performance
-	Consumer: 10,695 customers, $19.10m sales (51.9%), $2.07m profit (52.3%), 3.50 avg delivery days, 54.8% late risk.
-	Corporate: 6,239 customers, $11.17m sales (30.4%), $1.20m profit (30.3%), 3.49 avg delivery days, 54.7% late risk.
-	Home Office: 3,718 customers, $6.52m sales (17.7%), $690.8k profit (17.4%), 3.51 avg delivery days, 55.1% late risk.
Profit margins stay steady across all three segments (10.6%–10.9%), showing that revenue differences come from customer count rather than pricing or discount gaps.
### Delivery Performance & Late Risk
-	Delivery Status Breakdown: Late delivery makes up 54.8% of order items (98,977; 4.09 avg days), Advance shipping 23.0% (41,592; 2.50 avg days), Shipping on time 17.8% (32,196; 2.98 avg days), and Shipping canceled 4.3% (7,754; $1.57m in lost sales).
-	Shipping Mode Breakdown: Standard Class carries 59.7% of orders (107,752 rows) with a 38.1% late risk (4.00 actual vs. 4.00 expected days). Second Class (19.5% of orders) averages 3.99 days against a 2.00-day target (76.6% late risk), while First Class (15.4% of orders) averages 2.00 days against a 1.00-day target (95.3% late risk). Same Day shipping (5.4% of orders) averages 0.48 days with a 45.7% late risk.
-	Regional & Category Risk Hotspots: Central Africa (58.0% late risk), South Asia (56.3%), East Africa (55.9%), and Western Europe (55.8%) see the highest regional delay rates, while Pet Shop (58.9%), Book Shop (56.5%), and Health and Beauty (55.8%) lead category-level late risk.

## Recommendations
-	**Adjust First and Second Class delivery promises**: First Class (95.3% late risk) and Second Class (76.6% late risk) take 2 and 4 days on average; updating customer delivery estimates by +1 to +2 days or improving carrier speed will stop routine SLA misses.
-	**Cap steep discounts on unprofitable items**: Review the 33,784 money-losing rows (-$3.88m total loss) and set minimum profit rules on discounted orders, especially in Footwear (10.24% margin) and smaller departments (7.0%–8.9% margins).
-	**Improve fulfillment in top revenue regions**: Focus warehouse and carrier improvements on Western Europe ($5.89m sales; 55.8% late risk) and Central America ($5.67m sales; 54.8% late risk), where delays put the largest share of revenue at risk.
-	**Speed up payment approvals**: Over one-third of order items sit in PENDING_PAYMENT (22.1%), PENDING (11.2%), ON_HOLD (5.4%), or SUSPECTED_FRAUD (2.3%); faster payment checks for DEBIT (38.4%) and TRANSFER (27.6%) orders will reduce dispatch delays.
-	**Grow Corporate and Home Office accounts**: Offer targeted bulk deals to expand Corporate (30.4% share) and Home Office (17.7% share) repeat orders without cutting into profit margins.

## Tools Used
-	**Power Query**: data cleaning, null handling, type fixes, and star schema table setup
-	**DAX**: custom DimDate calendar table, core KPI measures (Total Sales, Total Profit, Total Quantity, Avg Delivery Time), and YoY growth formulas (SAMEPERIODLASTYEAR)
-	**Power BI Desktop**: data modeling and a two-page interactive dashboard (Executive Summary and Deep Dive View) with connected slicers 

## Conclusion 
DataCo Global has built a strong **$36.78m** global business led by **Europe, LATAM, Consumer buyers, and Fan Shop and Apparel products**. However, a **54.8%** late delivery risk rate,caused mainly by unrealistic **First and Second Class** delivery targets,and **$3.88m in losses** from heavily discounted orders hold back net profit. Updating shipping timelines, setting discount limits, and improving fulfillment in Western Europe and Central America give DataCo Global the clearest path to higher profit and happier customers.


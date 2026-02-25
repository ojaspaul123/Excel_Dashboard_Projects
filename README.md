Mobile Sales Analytics – Excel & Power BI
This project analyzes mobile phone sales data across brands, cities, and time using Excel and Power BI.
​

1. Data Source
File: Mobile-Sales-Data.xlsx

Sheet: Sheet1

Key columns:

Transaction ID, Day, Month, Year, Day Name

Brand, Mobile Model, Units Sold, Price Per Unit

Customer Name, Customer Age, City

Payment Method, Customer Ratings
​

2. Business Questions
Which brands and models generate the highest sales and revenue?

Which cities contribute the most to sales volume and value?

What is the trend of sales over time (daily, monthly, yearly)?

How do payment methods and customer ratings vary by brand and city?
​

3. Excel Visualizations
Open Mobile-Sales-Data.xlsx and create:

Pivot tables for:

Total Revenue = Units Sold × Price Per Unit

Revenue by Brand, Model, City, Month, Year
​

Charts:

Column chart: Revenue by Brand

Line chart: Monthly Revenue Trend

Bar chart: Revenue by City

Pie/Donut: Sales share by Payment Method
​

Optional:

Slicers for Year, Brand, City to make an interactive Excel dashboard.

4. Power BI Dashboard
Open Mobile_Sales_Dashboard.pbix in Power BI Desktop.

4.1 Data Model
Import table from Mobile-Sales-Data.xlsx (Sheet1).

Add a calculated column or measure for Total Revenue:

Total Revenue = Units Sold × Price Per Unit
​

4.2 Core Visuals
Recommended report pages:

Overview

Cards: Total Revenue, Total Units Sold, Total Transactions

Clustered column: Revenue by Brand

Line chart: Revenue by Month / Year
​

City & Customer Insights

Map / bar chart: Revenue by City

Bar chart: Units Sold by City

Column chart: Average Customer Rating by Brand
​

Product & Payment Analysis

Table or matrix: Brand, Model, Units Sold, Revenue, Avg Rating

Pie/Donut: Revenue by Payment Method

Bar chart: Revenue by Mobile Model (Top N)
​

4.3 Interactivity
Slicers: Year, Month, Brand, City, Payment Method

Cross-filtering between visuals to explore patterns (e.g., city-wise performance for a specific brand).
​

5. How to Run
Open Mobile-Sales-Data.xlsx in Excel to view raw data and pivot-based charts.
​

Open Mobile_Sales_Dashboard.pbix in Power BI Desktop.

Refresh data if path changes (Home → Transform data → Data source settings → Change Source).

6. Possible Extensions
Add DAX measures (e.g., YoY growth, Avg Revenue per Transaction).

Create a Brand Performance page focusing on Xiaomi, Samsung, Apple, Vivo, OnePlus separately.
​

Publish the report to Power BI Service and share with stakeholders.

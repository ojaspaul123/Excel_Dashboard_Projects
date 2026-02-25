# 📊 Mobile Sales Dashboard — Power BI Concepts Guide

A breakdown of all the Power BI concepts used in this `.pbix` file, organized by category for easy understanding.

---

## 🗂️ Report Structure

The dashboard is split into **3 pages (Report Sections)**:

| Page Name | Purpose |
|---|---|
| **DashBoard** | Main overview — KPIs, charts, map, slicers |
| **MTD, QTD, YTD** | Time-intelligence trends (Month/Quarter/Year to Date) |
| **Same Period of Last Year** | Year-over-year comparison using Last Year DAX measure |

---

## 📐 Data Model

### Table Used
- **`Mobile_Sales`** — The core fact table containing all transactional sales data.
- **`Custom_Calender`** — A custom date/calendar table used for time-intelligence calculations.

### Fields in `Mobile_Sales`
| Field | Type | Description |
|---|---|---|
| `Total_Sales` | Measure | Sum of all sales revenue |
| `Total_Quantity` | Measure | Total units sold |
| `Transaction` | Measure | Count of transactions |
| `Average_Price` | Measure | Average selling price |
| `MTD` | Measure | Month-to-Date sales (DAX time-intelligence) |
| `QTD` | Measure | Quarter-to-Date sales (DAX time-intelligence) |
| `YTD` | Measure | Year-to-Date sales (DAX time-intelligence) |
| `Last_year` | Measure | Same period prior year sales (DAX SAMEPERIODLASTYEAR) |
| `Customer Ratings` | Column | Raw rating score per transaction |
| `Rating_Status` | Column | Categorized rating: Good / Average / Poor |
| `City` | Column | City where sale occurred |
| `Mobile Model` | Column | Model name of the mobile sold |
| `Brand` | Column | Brand of the mobile |
| `Payment Method` | Column | UPI, Debit Card, Credit Card, etc. |

### Fields in `Custom_Calender`
| Field | Description |
|---|---|
| `DATE` | Full date column — base for all time calculations |
| `Day Name` | Name of the day (Monday, Tuesday, ...) |
| Date Hierarchy (`Year → Quarter → Month → Day`) | Used for drill-down in visuals |

---

## 🧮 DAX Concepts Used

### 1. Basic Aggregation Measures
Used for the KPI cards on every page.
```
Total_Sales     = SUM(Mobile_Sales[Sales Amount])
Total_Quantity  = SUM(Mobile_Sales[Quantity])
Transaction     = COUNT(Mobile_Sales[Transaction ID])
Average_Price   = AVERAGE(Mobile_Sales[Price])
```

### 2. Time-Intelligence Measures
These require a proper **Date Table** (the `Custom_Calender` table) marked as a Date Table in Power BI.

| Measure | DAX Function | What it does |
|---|---|---|
| `MTD` | `TOTALMTD()` | Cumulative sales from start of the month to selected date |
| `QTD` | `TOTALQTD()` | Cumulative sales from start of the quarter |
| `YTD` | `TOTALYTD()` | Cumulative sales from Jan 1 to selected date |
| `Last_year` | `SAMEPERIODLASTYEAR()` | Sales for the exact same date range in the previous year |

### 3. Conditional Categorization
The `Rating_Status` column likely uses:
```
Rating_Status = IF([Customer Ratings] >= 4, "Good",
                IF([Customer Ratings] >= 3, "Average", "Poor"))
```

---

## 📊 Visuals Used

### Page 1 — DashBoard
| Visual | Field Used | Concept |
|---|---|---|
| **Card (×4)** | Total_Sales, Total_Quantity, Transaction, Average_Price | KPI Card visual for single metric display |
| **Line Chart** | Total_Quantity by Month | Trend over time |
| **Pie Chart** | Transaction by Payment Method | Part-to-whole proportion |
| **Map (Bing Maps)** | Total_Sales by City | Geospatial visual — uses city names to auto-geocode |
| **Funnel Chart** | Ratings by Rating_Status | Ranked comparison of categories |
| **Bar Chart** | Total_Sales by Mobile Model | Horizontal bar for ranking |
| **Area Chart** | Total_Sales by Day Name | Trend with filled area under the line |

### Page 2 — MTD, QTD, YTD
| Visual | Fields Used | Concept |
|---|---|---|
| **Line Chart** | Total_Sales vs MTD by Month | Overlay comparison of actual vs running total |
| **Line Chart** | Total_Sales vs QTD by Year | Quarter accumulation trend across years |
| **Line Chart** | Total_Sales vs YTD by Year | Full year accumulation view |

### Page 3 — Same Period of Last Year
| Visual | Fields Used | Concept |
|---|---|---|
| **Table** | Year, Quarter, Month, Day, Total_Sales, Last_year | Detailed row-level comparison |
| **Clustered Bar Chart (×3)** | Total_Sales vs Last_year by Year / Quarter / Month | Side-by-side current vs prior year |

---

## 🎛️ Slicers and Filters

Slicers allow report viewers to interactively filter all visuals on a page.

| Slicer | Type | Field |
|---|---|---|
| Month selector | **List Slicer** | `Custom_Calender[Month]` — January to December |
| Mobile Model | **Dropdown Slicer** | `Mobile_Sales[Mobile Model]` |
| Payment Method | **Dropdown Slicer** | `Mobile_Sales[Payment Method]` |
| Brand | **Dropdown Slicer** | `Mobile_Sales[Brand]` |
| Year | **Dropdown Slicer** | `Custom_Calender[Year]` (on pages 2 & 3) |

> **Concept:** Slicers use **cross-filtering** — selecting a value filters all connected visuals on the page simultaneously.

---

## 🔗 Relationships (Data Model)

The two tables are connected through a **one-to-many relationship**:

```
Custom_Calender[DATE]  ──────►  Mobile_Sales[Date]
      (One)                           (Many)
```

This relationship is what makes **time-intelligence DAX functions** (MTD, QTD, YTD, Last Year) work correctly. Without a proper date table connected this way, those functions would not compute accurately.

---

## 🏗️ Key Power BI Concepts Summary

| Concept | Where Used |
|---|---|
| **Measures (DAX)** | All KPI cards and time-intelligence charts |
| **Calculated Columns** | Rating_Status categorization |
| **Date Table** | Custom_Calender for all time-intelligence |
| **Time Intelligence** | MTD, QTD, YTD, SAMEPERIODLASTYEAR |
| **Relationships** | Calendar ↔ Sales table join |
| **Cross-filtering** | Slicers filtering all visuals |
| **Drill-down Hierarchy** | Year → Quarter → Month → Day on date axis |
| **Geospatial Visual** | Bing Map for city-level sales |
| **Report Pages** | 3 separate pages for different analysis angles |
| **Conditional Logic (IF/SWITCH)** | Rating status classification |

---

*Built with Power BI Desktop · Data: Mobile_Sales_Data.xlsx · Author: Ojas Paul*

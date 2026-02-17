# 📊 Sales Executive Dashboard — README

> **File:** `Sales_Executive_DashBoard.xlsm`
> **Type:** Excel Macro-Enabled Workbook (.xlsm)
> **Sheets:** `RAW DATA` · `DASHBOARD`

---

## 🗂️ Overview

The **Sales Executive Dashboard** is an interactive Excel workbook designed to monitor and compare the performance of sales executives across multiple cities in India. It provides real-time visual summaries of total sales figures, target hit percentages, and shortfall metrics — all filterable by city using a toggle-based navigation bar.

---

## 🏙️ City Filter (Navigation Bar)

At the top of the dashboard, there is a **city selection bar** with the following locations:

| Chennai | Delhi | Mumbai | Nagpur | Patna | **Pune** | Ranchi | Surat |
|---------|-------|--------|--------|-------|----------|--------|-------|

> 🟡 The **highlighted city (yellow)** is the currently active filter. In the screenshot, **Pune** is selected.  
> Clicking any city button will refresh all four data boards and charts for that region.

---

## 🗃️ Data Boards (4 Panels)

The dashboard is divided into **4 interactive boards**, each toggled by a checkbox:

### ✅ Board 1 — Total Sales by Executive
Displays a ranked list of Sales Executives and their **Sum of Total Sales** for the selected city.

| Sales Executive | Sum of Total Sales |
|----------------|--------------------|
| Abdul Hamid | 286 |
| Anjali Sahay | 346 |
| Ashok Mahto | 302 |
| Mercy Thampi | 349 |
| Neeru Mehta | 286 |
| Rajshree Dhabekar | 322 |
| Sajid Naqvi | 335 |
| Shailaja Kamal | 341 |
| Shubhanjali Joshi | 367 |
| Sunita Madnani | 332 |

---

### ✅ Board 2 — Total Sales (Second Dataset)
A secondary view of **Sum of Total Sales** — typically representing a different product line, quarter, or comparison period.

| Sales Executive | Sum of Total Sales |
|----------------|--------------------|
| Abdul Hamid | 286 |
| Anuj Sharma | 213 |
| Dinesh Kumar | 166 |
| Jitendra Kumar | 236 |
| Kamini Tiwari | 268 |
| Mangal Singh | 245 |
| Neeru Mehta | 286 |
| Prabha Desikan | 171 |
| Rajeev Garg | 217 |
| Rekha Gupta | 285 |

---

### ✅ Board 3 — Target Hit %
Shows how much of the sales target each executive has achieved, expressed as a **percentage**.

| Sales Executive | Sum of Target Hit % |
|----------------|----------------------|
| Abdul Hamid | 57.20% |
| Anjali Sahay | 69.20% |
| Ashok Mahto | 60.40% |
| Mercy Thampi | 69.80% |
| Neeru Mehta | 57.20% |
| Rajshree Dhabekar | 64.40% |
| Sajid Naqvi | 67.00% |
| Shailaja Kamal | 68.20% |
| Shubhanjali Joshi | 73.40% ⭐ |
| Sunita Madnani | 66.40% |

> ⭐ **Top Performer:** Shubhanjali Joshi achieved the highest target hit rate at **73.40%**.

---

### ✅ Board 4 — Away From Target %
Indicates how far each executive is from hitting their full target — i.e., the **remaining gap**.

| Sales Executive | Sum of Away From Target % |
|----------------|---------------------------|
| Abdul Hamid | 42.80% |
| Anuj Sharma | 57.40% |
| Dinesh Kumar | 66.80% |
| Jitendra Kumar | 52.80% |
| Kamini Tiwari | 46.40% |
| Mangal Singh | 51.00% |
| Neeru Mehta | 42.80% |
| Prabha Desikan | 65.80% |
| Rajeev Garg | 56.60% |
| Rekha Gupta | 43.00% |

> 💡 **Lowest Gap:** Abdul Hamid and Neeru Mehta are closest to target with only **42.80%** remaining.

---

## 📈 Charts & Visualizations

Three charts are embedded in the dashboard for quick at-a-glance insights:

### 📊 1. Horizontal Bar Chart — Sales by Executive
- **Type:** Horizontal Bar
- **Purpose:** Compare individual sales totals side by side
- **X-axis:** Total Sales (0 to 400)
- **Y-axis:** Sales Executive names
- **Highlight:** Shubhanjali Joshi leads with **367** total sales

---

### 🥧 2. Pie Chart — Sales Distribution
- **Type:** Donut / Pie
- **Purpose:** Shows the proportional contribution of each executive to total sales
- **All slices are approximately equal (~9–11%)**, indicating a fairly balanced team performance
- Distinct colors represent each executive

---

### 📉 3. Line Chart — Trend Analysis (Total)
- **Type:** Line / Scatter
- **Purpose:** Shows performance trends across all executives
- **Y-axis values** range from approximately **1.00 to 6.80**
- Named executives on X-axis: Abdul Hamid, Anuj Sharma, Dinesh Kumar, Jitendra Kumar, Kamini Tiwari, Mangal Singh, Neeru Mehta, Prabha Desikan, Rajeev Garg, Rekha Gupta

---

## 🗄️ Sheet Structure

| Sheet Name | Description |
|------------|-------------|
| `RAW DATA` | The underlying dataset — all sales records, executive names, targets, and actuals |
| `DASHBOARD` | The visual, interactive dashboard built from PivotTables and Macro controls |

> ⚠️ Do **not** manually edit the `DASHBOARD` sheet. All data flows from `RAW DATA`.

---

## ⚙️ How to Use

1. **Open the file** in Microsoft Excel (macros must be enabled).
2. Click **Enable Macros** when prompted on launch.
3. Use the **city buttons** at the top to filter data by region.
4. Toggle **Board 1 / Board 2 / Board 3 / Board 4** checkboxes to show or hide panels.
5. All charts update automatically based on the active city selection.

---

## ✅ Key Metrics at a Glance (Pune — Sample)

| Metric | Value |
|--------|-------|
| 🏆 Highest Total Sales | Shubhanjali Joshi — **367** |
| 📉 Lowest Total Sales | Abdul Hamid / Neeru Mehta — **286** |
| 🎯 Best Target Hit % | Shubhanjali Joshi — **73.40%** |
| 🔴 Furthest from Target | Dinesh Kumar — **66.80% remaining** |
| 🟢 Closest to Target | Abdul Hamid / Neeru Mehta — **42.80% remaining** |

---

## 📌 Notes

- All percentages in Board 3 and Board 4 are **complementary** (Target Hit % + Away From Target % ≈ 100%).
- The workbook uses **VBA macros** for city filtering — ensure macro execution is permitted in your Excel Trust Center settings.
- Data is filtered per city; switching cities will update all boards and charts simultaneously.

---

*README generated for `Sales_Executive_DashBoard.xlsm` — for internal use and onboarding reference.*

# Retail Sales and Inventory Analytics - Power BI Portfolio Project

This repository contains a comprehensive Power BI project that transforms raw CSV files from a toy retailer into an interactive, seven-page report. It integrates sales, product, store, and inventory data, allowing managers to instantly analyze revenue sources, profitable products, and stock levels across 50 stores in 29 cities in Mexico.

---

## Project Overview

* **Scenario:** A retail company needs a centralized report to review sales performance and inventory across its national stores.
* **Data Sources:** Six CSV files (`sales.csv`, `inventory.csv`, `stores.csv`, `products.csv`, `calendar.csv`, `data_dictionary.csv`) from the Maven Toys dataset.
* **Period Covered:** Sales from January 1, 2022 to September 30, 2023.
* **Tools Used:** Power BI Desktop, Power Query (M), DAX, Python (`seaborn`, `matplotlib`).

---

## Repository Structure

```text
├── Data/
│   ├── calendar.csv
│   ├── data_dictionary.csv
│   ├── inventory.csv
│   ├── products.csv
│   ├── sales.csv
│   └── stores.csv
├── Dashboard/
│   └── Store_Data_Dashboard.pbix
└── README.md
```

---

## Key Features & Skills Demonstrated

* **Data Cleaning & Transformation (Power Query):**
  * Connected multiple CSV files using folder/file connectors.
  * Cleaned column headers, promoted headers, fixed data types, and trimmed text whitespace.
  * Processed price columns to extract clean numerical data.

* **Data Modeling:**
  * Star-schema layout featuring two Fact tables (`sales`, `inventory`) and three Dimension tables (`stores`, `products`, `Sales_calendar`).
  * Enforced 1-to-many single-direction relationships to maintain clean data flow and high dynamic query performance.

* **Advanced DAX & Analytics:**
  * Dynamic `CALENDAR` generation to ensure gapless date tracking.
  * Key metrics calculated using `SUMX`, `RELATED`, `CALCULATE`, and variable pattern (`VAR` / `RETURN`).
  * Time-Intelligence metrics for YoY and MoM growth tracking.

* **Visualizations & Python Integration:**
  * Integrated Python (`seaborn`) scatter plot matrix for custom Revenue vs. Cost analysis.
  * Custom Report Page Tooltips, dynamic bookmarks for visual toggling, and AI visuals (*Decomposition Tree*, *Key Influencers*).
  * Conditional formatting for high-impact metric scanning.

* **Row-Level Security (RLS):**
  * Configured static RLS roles to restrict dataset access based on specific business parameters (e.g., product categories).

---

## Data Model Architecture

The data model follows a **Star Schema** design:
* **Fact Tables:** 
  * `sales`: High-volume transactional records.
  * `inventory`: Snapshot of physical store stock levels.
* **Dimension Tables:** 
  * `stores`: Metadata on store location, city, and date opened.
  * `products`: Product hierarchy, category, unit cost, and price.
  * `Sales_calendar`: Dedicated date dimension table.

---

## Report Structure

1. **Overview Page:** High-level executive KPI indicators comparing monthly targets ($600K threshold) against actual revenue, margin, and category split.
2. **Store Sales:** In-depth regional volume comparison using treemaps, custom Python scatter plots, and column charts.
3. **Product Sales:** Breakdown of top revenue-driving categories and individual stock share across product lines.
4. **AI Insights:** Interactive Decomposition Tree and Key Influencer visuals to isolate primary drivers of revenue growth.
5. **Inventory Snapshot:** Analysis of stock on hand versus units sold to prevent stockouts and identify slow-moving inventory.
6. **Detailed Matrix Page:** Tabular view with gradient conditional formatting highlighting month-over-month profitability.
7. **Tooltip Page (Hidden):** Contextual pop-up visualizing dynamic product-category breakdowns upon hover.

---

## Key Business Insights

* **Overall Performance:** Generated **$14.44M** in revenue and **$4.01M** in gross profit (~28% overall profit margin).
* **Top Sales Channel:** Downtown store locations generate **56.9%** of all revenue.
* **Category Dynamics:** While *Toys* accounts for the highest overall volume (~35%), the *Electronics* category yields nearly equal total profit ($1.00M vs $1.08M) on less than half the total revenue volume.
* **Stock Alert:** *Electronics* currently holds the lowest percentage of inventory on hand (~8.1%), presenting a high risk for out-of-stock scenario on high-margin goods.

---

## Getting Started

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/powerbi-store-data.git
   ```
2. **Setup Data Directory:**
   Ensure all 6 CSV files are located inside the `/Data` directory.
3. **Update Data Source in Power BI:**
   * Open `Store_Data_Dashboard.pbix` in Power BI Desktop.
   * Go to **Transform Data > Data source settings**.
   * Update the path to point to your local directory where the CSV files reside.
4. **Refresh & Explore:**
   * Hit **Refresh** on the Home tab to build the model.
   * Make sure Python with `seaborn` and `matplotlib` packages installed if you want to view the Python visual page.
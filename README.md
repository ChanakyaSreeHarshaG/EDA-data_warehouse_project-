# 📊 EDA-data_warehouse Project

> A comprehensive collection of SQL scripts for **Exploratory Data Analysis (EDA)** and **Advanced Analytics** built on top of the [SQL Data Warehouse Project](https://github.com/ChanakyaSreeHarshaG/SQl-Data_Warehouse_Project). This project transforms clean Gold layer data into meaningful business insights using pure SQL.

---

## 🔗 Project Context

This project is **Part 2** of a two-part data portfolio series:

| Part | Project | Description |
|---|---|---|
| 1️⃣ | [SQL Data Warehouse](https://github.com/ChanakyaSreeHarshaG/SQl-Data_Warehouse_Project) | Built Bronze → Silver → Gold layers using Medallion Architecture |
| 2️⃣ | **SQL EDA & Analytics** *(this repo)* | Explored and analyzed the Gold layer data using SQL |

The data analyzed here comes directly from the `gold.fact_sales`, `gold.dim_customers`, and `gold.dim_products` tables built in Part 1.

---

## 📖 Project Overview

This project demonstrates how to extract actionable business insights from a structured data warehouse using SQL alone — no Python, no BI tool, just well-crafted queries.

**What's covered:**
- Database exploration & data profiling
- Key business measures & metrics
- Time-based trend analysis
- Cumulative analytics
- Performance comparisons
- Customer & product segmentation
- Part-to-whole analysis
- Window functions for advanced reporting

---

## 🗂️ Analytics Categories

### 🔍 1. Database Exploration
Understanding the structure and quality of the data before analysis:
- Table row counts and column inventory
- NULL checks and data completeness
- Distinct value exploration across dimensions
- Date range validation

### 📏 2. Measures & Metrics
Core business KPIs calculated from the fact table:
- Total Sales Revenue
- Total Quantity Sold
- Average Order Value
- Total Number of Orders
- Total Number of Customers
- Total Number of Products

### 📅 3. Changes Over Time
Tracking how the business performs across time periods:
- Monthly and yearly sales trends
- Year-over-year (YoY) revenue comparison
- Month-over-month (MoM) growth analysis
- Seasonal patterns in order volumes

### 📈 4. Cumulative Analytics
Running totals and moving averages to understand growth trajectory:
- Cumulative revenue over time
- Running total of orders placed
- Moving average of sales amounts

### 🏆 5. Performance Analysis
Ranking and comparing entities to identify top and bottom performers:
- Top 10 products by revenue
- Top 10 customers by sales amount
- Worst performing product categories
- Product performance vs. category average

### 🧩 6. Segmentation
Grouping customers and products into meaningful segments:
- Customer segmentation by purchase value (High / Mid / Low)
- Product segmentation by cost range
- Customer age group analysis using birthdate
- Geographic segmentation by country

### 🥧 7. Part-to-Whole Analysis
Understanding how individual parts contribute to the total:
- Revenue contribution by product category (%)
- Sales share by customer country (%)
- Product line contribution to total revenue

### 🪟 8. Window Functions
Advanced SQL techniques for ranking and analytical queries:
- `RANK()` and `DENSE_RANK()` for product/customer leaderboards
- `LAG()` and `LEAD()` for period-over-period comparisons
- `SUM() OVER()` for running totals
- `AVG() OVER()` for moving averages

---

## 📂 Repository Structure

```
EDA-data_warehouse_project/
│
├── datasets/                        # Gold layer CSV exports (fact & dimensions)
│
├── docs/                            # Reference diagrams
│   └── data_flow_diagram.png        # From the Data Warehouse project
│
├── scripts/
│   ├── 1_database_exploration/      # Profiling and data discovery queries
│   ├── 2_measures_and_metrics/      # Core KPI queries
│   ├── 3_changes_over_time/         # Trend analysis queries
│   ├── 4_cumulative_analytics/      # Running totals & moving averages
│   ├── 5_performance_analysis/      # Rankings & comparisons
│   ├── 6_segmentation/              # Customer & product segments
│   ├── 7_part_to_whole/             # Contribution & share analysis
│   └── 8_window_functions/          # Advanced SQL window queries
│
├── README.md
└── LICENSE
```

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **SQL Server Express** | Database engine |
| **SSMS** | Query development & execution |
| **T-SQL** | All analytics scripts (100% SQL) |
| **Git / GitHub** | Version control |

---

## 🚀 How to Run

1. **Complete Part 1 first** — Make sure you've run the [Data Warehouse Project](https://github.com/ChanakyaSreeHarshaG/SQl-Data_Warehouse_Project) to set up the Gold layer tables

2. **Clone this repo**
   ```bash
   git clone https://github.com/ChanakyaSreeHarshaG/EDA-data_warehouse_project-.git
   ```

3. **Open SSMS** and connect to your SQL Server instance

4. **Run scripts in order** — Start with `1_database_exploration` and work through each folder sequentially

5. **Explore the results** — Each script is self-contained and produces a result set you can analyze directly in SSMS

---

## 💡 Key Business Questions Answered

- 📦 Which products generate the most revenue?
- 👥 Who are our highest-value customers?
- 📅 What months/years had the highest sales?
- 🌍 Which countries contribute most to total revenue?
- 📊 How is revenue distributed across product categories?
- 🔄 Is the business growing month over month?
- 🧑‍🤝‍🧑 How can customers be segmented by spending behavior?

---

## 🔍 Sample Insight — Customer Segmentation

```sql
-- Segment customers by total purchase value
SELECT
    customer_key,
    first_name,
    last_name,
    SUM(sales_amount) AS total_sales,
    CASE
        WHEN SUM(sales_amount) >= 10000 THEN 'High Value'
        WHEN SUM(sales_amount) >= 5000  THEN 'Mid Value'
        ELSE 'Low Value'
    END AS customer_segment
FROM gold.fact_sales f
JOIN gold.dim_customers c ON f.customer_key = c.customer_key
GROUP BY customer_key, first_name, last_name
ORDER BY total_sales DESC;
```

---

## 🛡️ License

This project is licensed under the [MIT License](LICENSE).

---

## 🙋 About Me

Hi, I'm **Chanakya Sree Harsha G** — building my data engineering and analytics portfolio one project at a time.

This is Part 2 of my data portfolio series. Check out Part 1 (the Data Warehouse) and stay tuned for Part 3 (Advanced Analytics & Reporting).

Feel free to connect on [LinkedIn](https://www.linkedin.com/in/chanakyasreeharsha) or explore more on [GitHub](https://github.com/ChanakyaSreeHarshaG).

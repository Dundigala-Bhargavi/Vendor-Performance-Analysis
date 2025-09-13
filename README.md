# 🧾 Vendor Performance Analysis – Retail Inventory & Sales

Analyzing vendor efficiency and profitability to support strategic purchasing and inventory decisions using **SQL, Python, and Power BI**.

---

## Overview
This project evaluates **vendor performance** and **retail inventory dynamics** to drive strategic insights for purchasing, pricing, and inventory optimization.  

A complete data pipeline was built using:  
- **SQL** – ETL, joins, filtering, CTEs  
- **Python** – Analysis and hypothesis testing  
- **Power BI** – Interactive dashboards  

---

## Business Problem
Effective inventory and sales management are critical in the retail sector. This project aims to:  
- Identify underperforming brands needing pricing or promotional adjustments  
- Determine vendor contributions to sales and profits  
- Analyze the cost-benefit of bulk purchasing  
- Investigate inventory turnover inefficiencies  
- Statistically validate differences in vendor profitability  

---

## Dataset
- Multiple CSV files located in `/data/` folder (`sales.csv`, `vendors.csv`, `inventory.csv`)  
- Summary table created from ingested data and used for analysis  

---

## Tools & Technologies
- **SQL** – Common Table Expressions, Joins, Filtering  
- **Python** – Pandas, Matplotlib, Seaborn, SciPy  
- **Power BI** – Interactive Visualizations  
- **GitHub** – Version control  

---

## Data Cleaning & Preparation
- Removed transactions with:  
  - Gross Profit ≤ 0  
  - Profit Margin ≤ 0  
  - Sales Quantity = 0  
- Created summary tables with vendor-level metrics  
- Converted data types, handled outliers, merged lookup tables  

---

## Exploratory Data Analysis (EDA)
**Negative or Zero Values Detected:**  
- Gross Profit: Min -52,002.78 (loss-making sales)  
- Profit Margin: Min -∞ (sales at zero or below cost)  
- Unsold Inventory: Indicating slow-moving stock  

**Outliers Identified:**  
- High Freight Costs (up to 257K)  
- Large Purchase/Actual Prices  

**Correlation Analysis:**  
- Weak correlation between Purchase Price & Profit  
- Strong correlation between Purchase Qty & Sales Qty (0.999)  
- Negative correlation between Profit Margin & Sales Price (-0.179)  

---

## Research Questions & Key Findings
- **Brands for Promotions:** 198 brands with low sales but high profit margins  
- **Top Vendors:** Top 10 vendors = 65.69% of purchases → risk of over-reliance  
- **Bulk Purchasing Impact:** 72% cost savings per unit in large orders  
- **Inventory Turnover:** $2.71M worth of unsold inventory  
- **Vendor Profitability:**  
  - High Vendors: Mean Margin = 31.17%  
  - Low Vendors: Mean Margin = 41.55%  
- **Hypothesis Testing:** Statistically significant differences in profit margins → distinct vendor strategies

## Dashboard
Power BI Dashboard shows:  
- Vendor-wise Sales and Margins  
- Inventory Turnover  
- Bulk Purchase Savings  
- Performance Heatmaps  

---  

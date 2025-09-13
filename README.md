# Vendor Performance Data Analytics

A comprehensive data-driven analysis of **vendor performance** and **product pricing optimization** for an inventory-based retail business.  
The workflow covers raw data ingestion, exploratory analysis, metrics computation, and actionable insights—integrating multiple tables tied from the procurement chain to final sales.

---

## Project Workflow Overview

- **Data Ingestion:**  
  Raw CSV files are systematically loaded into SQLite tables using pandas and SQLAlchemy, with logging for ingestion performance and traceability.
- **Database Structure:**  
  Inventory, purchases, sales, vendor price, and invoice data are normalized into dedicated tables, supporting both granular and aggregated analytics.

---

## Database and Data Structure

### Tables

| Table Name           | Description                                                             |
|----------------------|------------------------------------------------------------------------|
| begin_inventory      | Snapshots of inventory at period start (qty, price, location)          |
| end_inventory        | Snapshots of inventory at period end                                    |
| purchases            | Detailed purchase transactions per store, product, vendor              |
| sales                | Product sales with qty, dollar value, tax, vendor reference            |
| purchase_prices      | Purchase price info (brand, description, vendor, etc.)                 |
| vendor_invoice       | Vendor-level invoice/transactional summary (dollars, freight, approval)|

---

## Exploratory Analysis Approach

- Assessed data integrity, coverage, and relationships between tables.  
- Listed schema, checked column completeness and cross-references.  
- Identified fields relevant for profitability and pricing—like `PurchasePrice`, `ActualPrice`, `ExciseTax`, `FreightCost`, etc.

---

## Metric Computation & Aggregates

Key performance indicators (KPIs) for each Vendor-Brand:

- **Gross Profit**  
  $$
  \text{Gross Profit} = \text{Total Sales Dollars} - \text{Total Purchase Dollars} - \text{FreightCost}
  $$
- **Profit Margin**  
  $$
  \text{Profit Margin} = \frac{\text{Gross Profit}}{\text{Total Sales Dollars}}
  $$
- **Stock Turnover**  
  $$
  \text{Stock Turnover} = \frac{\text{Total Sales Quantity}}{\text{Total Purchase Quantity}}
  $$
- **Sales to Purchase Ratio**  
  $$
  \text{Sales to Purchase Ratio} = \frac{\text{Total Sales Quantity}}{\text{Total Purchase Quantity}}
  $$

Aggregates tie purchase volume, sales volume, excise tax, cost structure, and price realization together.

---

## Deep Dive: Vendor and Brand Analysis

### Top Vendors by Profitability (Sample Table)

| Vendor               | Brand           | Gross Profit  | Profit Margin | Turnover | Sales/Purchase Ratio |
|----------------------|----------------|---------------|---------------|----------|---------------------|
| BROWN-FORMAN CORP    | Jack Daniels   | 1,290,667.91  | 25.30%        | 0.98     | 1.34                |
| DIAGEO NORTH AMERICA | Ketel One Vodka| 1,199,901.61  | 28.41%        | 0.98     | 1.40                |
| MARTIGNETTI COMPANIES| Tito’s Vodka   | 1,015,032.27  | 21.06%        | 0.98     | 1.27                |

**Insights**  
- Highest gross profits belong to leading national spirits brands, with robust pricing strategies and high stock turnover.  
- Profit margins clustering at 20–28% indicate healthy vendor negotiation or market positioning.  
- Turnover and sales ratios near 1 indicate efficient inventory movement.

### Excise Tax & Freight Impact

- Excise tax can represent up to 5%+ of sales value for certain brands and must be incorporated in pricing.  
- Freight costs can erode profit—vendors with lower freight per unit are more desirable.

---

## Product Pricing Optimization

- Some brands achieve margins >20% after all costs; others barely break even due to high tax, freight, or vendor pricing.  
- Larger bottle sizes sometimes deliver better per-liter profit, affecting stocking recommendations.  
- Outlier analysis flags sales below purchase + excise + freight costs for review.

---

## Actionable Recommendations

### Vendor Selection
- Prefer vendors with higher gross profit, lower freight, and strong turnover.  
- Monitor vendors with margin erosion.

### Pricing Strategy
- Review brands with net profit below threshold; raise prices where feasible.  
- Periodically renegotiate purchase prices for underperforming vendors.  
- Segment products by turnover for promotions.

### Inventory Management
- Maintain optimum stock turnover; avoid overstocking slow movers.  
- Reorder quantities based on sales-to-purchase ratios, focusing on fast movers.

### Compliance & Risk
- Ensure excise tax and freight are incorporated transparently into cost structure.

---

## Visual Summaries (Sample Table)

| VendorName           | Brand           | PurchasePrice | ActualPrice | TotalSalesQuantity | GrossProfit  | ProfitMargin |
|----------------------|----------------|---------------|-------------|------------------|--------------|--------------|
| BROWN-FORMAN CORP    | Jack Daniels   | 26.27         | 36.99       | 142,049          | 1,290,667.91 | 25.30%       |
| DIAGEO NORTH AMERICA | Ketel One Vodka| 21.89         | 29.99       | 135,838          | 1,199,901.61 | 28.41%       |

---

## Conclusion

This project automated ingestion and analysis of complex inventory, purchase, and sales datasets for profitability and pricing insights.  
It provides a robust methodology for ongoing vendor evaluation, pricing optimization, and risk/reorder planning, and is scalable for continued growth in retail.


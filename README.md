# 🚀 Sales Pipeline Dashboard | Power BI Project

This Power BI project visualizes the **entire B2B sales process**, integrating data from four sources:

- `accounts.csv`
- `products.csv`
- `sales_pipeline.csv`
- `sales_teams.csv`

---

## 🧹 Data Preparation & Cleaning

- Removed irrelevant columns (e.g., `subsidiary_of`)
- Standardized date formats and numeric values
- Ensured consistency in `product`, `account`, and `sales_agent` fields

---

## 🔗 Data Modeling

**Relationships created:**

- `sales_pipeline[account]` → `accounts[account]`  
- `sales_pipeline[product]` → `products[product]`  
- `sales_pipeline[sales_agent]` → `sales_teams[sales_agent]`  

All relations are *many-to-one* and directional as required by the model.

---

## 🧮 DAX Measures

```DAX
Total Revenue = SUM(sales_pipeline[close_value])

Closed Deals = 
CALCULATE(
    COUNTROWS(sales_pipeline),
    sales_pipeline[deal_stage] = "Closed Won"
)

Avg Deal Size = 
DIVIDE([Total Revenue], [Closed Deals])

Top Product = 
CALCULATE(
    FIRSTNONBLANK(products[product], 1),
    TOPN(1, VALUES(products[product]), [Total Revenue])
)
```

---

## 📊 Visuals in the Dashboard

1. **KPI Cards**:
   - Total Revenue  
   - Closed Deals  
   - Avg Deal Size  
   - Top Product

2. **Bar Chart**:
   - Deal Count by Sales Agent

3. **Funnel Chart**:
   - Deals by Stage (to visualize drop-offs)

4. **Map**:
   - Revenue by Office Location (from accounts)

5. **Column Chart**:
   - Revenue by Product Series

6. **Pie Chart**:
   - Revenue by Sector

---

## 🧠 Business Insight

This dashboard allows business leaders to:
- Identify top-performing agents and products
- See which stages in the funnel are losing deals
- Compare revenue across regions or sectors
- Strategically guide training, resourcing, or campaigns

---

## 📁 Files

All datasets and PBIX file are included in this repository.  
Feel free to fork, customize, and use it in your own projects.

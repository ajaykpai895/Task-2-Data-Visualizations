# Task 2 — Data Visualization and Storytelling

## 📌 Objective
Create visualizations that convey a compelling business story using sales data.

## 🛠 Tools Used
- Power BI Desktop
- Dataset: product_sales_dataset_final.csv (200,000 rows)

## 📊 Dashboard Pages

| Page | Visual Type | Description |
|------|------------|-------------|
| 1 | KPI Cards | Total Revenue, Profit, Orders, Profit Margin % |
| 2 | Line Chart | Revenue & Profit trend over time |
| 3 | Bar Chart | Revenue by Category |
| 4 | Map + Donut | Regional performance breakdown |
| 5 | Treemap + Bar | Top products and sub-categories |
| 6 | Scatter Chart | Revenue vs Profit by Category |

## 🧮 DAX Measures Created

```dax
Total Revenue = SUM('product_sales_dataset_final'[Revenue])
Total Profit = SUM('product_sales_dataset_final'[Profit])
Total Orders = DISTINCTCOUNT('product_sales_dataset_final'[Order_ID])
Total Quantity = SUM('product_sales_dataset_final'[Quantity])
Profit Margin % = DIVIDE([Total Profit], [Total Revenue], 0) * 100
Avg Order Value = DIVIDE([Total Revenue], [Total Orders], 0)
Revenue YoY Growth % = 
VAR CurrentYear = YEAR(MAX('product_sales_dataset_final'[Order_Date]))
VAR CY = CALCULATE([Total Revenue], YEAR('product_sales_dataset_final'[Order_Date]) = CurrentYear)
VAR PY = CALCULATE([Total Revenue], YEAR('product_sales_dataset_final'[Order_Date]) = CurrentYear - 1)
RETURN DIVIDE(CY - PY, PY, 0) * 100
```

## 🔍 Key Business Insights

- **Electronics** leads all categories in total revenue
- **South region** contributes the highest share of sales
- **Q4 months** show consistent revenue spikes across years
- Some categories show **high revenue but low profit margins** — a pricing opportunity
- Top 10 products drive a disproportionate share of total revenue

## 📁 Repository Structure

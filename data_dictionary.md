# 📖 Data Dictionary

This file explains every column in the **Sample – Superstore** dataset so anyone
reading the project understands the data.

- **File name:** `Sample - Superstore.csv`
- **Rows:** 9,994 (one row per product on an order)
- **Grain (what one row means):** a single product line within a customer order

---

## Column Reference

| # | Column Name | Type | Description | Example |
|---|-------------|------|-------------|---------|
| 1 | Row ID | Number | Unique ID for each row | 1 |
| 2 | Order ID | Text | Unique ID for each order (can appear on multiple rows) | CA-2017-152156 |
| 3 | Order Date | Date | Date the customer placed the order | 11/8/2017 |
| 4 | Ship Date | Date | Date the order was shipped | 11/11/2017 |
| 5 | Ship Mode | Text | Shipping speed chosen | Second Class |
| 6 | Customer ID | Text | Unique ID for each customer | CG-12520 |
| 7 | Customer Name | Text | Name of the customer | Claire Gute |
| 8 | Segment | Text | Type of customer | Consumer / Corporate / Home Office |
| 9 | Country | Text | Country of the sale | United States |
| 10 | City | Text | City of the customer | Henderson |
| 11 | State | Text | State of the customer | Kentucky |
| 12 | Postal Code | Number | ZIP code | 42420 |
| 13 | Region | Text | Sales region | West / East / Central / South |
| 14 | Product ID | Text | Unique ID for each product | FUR-BO-10001798 |
| 15 | Category | Text | Broad product group | Furniture / Office Supplies / Technology |
| 16 | Sub-Category | Text | Specific product group | Chairs, Phones, Binders, Tables, etc. |
| 17 | Product Name | Text | Full product name | Bush Somerset Bookcase |
| 18 | Sales | Number ($) | Revenue from that line (after discount) | 261.96 |
| 19 | Quantity | Number | Units sold on that line | 2 |
| 20 | Discount | Number (0–1) | Discount applied (0.20 = 20% off) | 0.00 |
| 21 | Profit | Number ($) | Profit from that line (can be negative) | 41.91 |

---

## Key Terms

- **Sales** – the money earned from a line item *after* any discount is applied.
- **Profit** – what's left after costs. **Negative profit means the company lost
  money on that sale** (often because the discount was too deep).
- **Discount** – stored as a decimal. `0.15` means a 15% discount.
- **Profit Margin** – Profit ÷ Sales, shown as a percentage. A common health
  metric: higher is better.

---

## Calculated Fields Used in This Project

These are not in the raw file — we create them during analysis:

| Field | Formula | Meaning |
|-------|---------|---------|
| Profit Margin | `Profit / Sales` | Profitability as a % |
| Order Year | Year of `Order Date` | For year-over-year trends |
| Shipping Days | `Ship Date − Order Date` | How fast orders ship |

---

> ✅ Use this dictionary as your reference whenever a column name appears in the
> SQL queries or the Tableau dashboard.

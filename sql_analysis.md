# 🗄️ SQL Analysis

This file contains the SQL queries used to analyze the Superstore data, each
followed by a **plain-English explanation** of what it does and why.

---

## 🛠️ How to Run These Queries (No Experience Needed)

You don't need to install a database server. Use this free, beginner-friendly
tool:

1. Download **DB Browser for SQLite** (free): https://sqlitebrowser.org/dl/
2. Open it and click **New Database** → save it as `superstore.db`.
3. Go to **File → Import → Table from CSV file** and choose
   `Sample - Superstore.csv`.
4. Name the table **`superstore`** and click **OK** (let it create the table).
5. Click the **Execute SQL** tab. Paste any query below and press the
   ▶ **Run** button (or **Ctrl + Enter**).

> 💡 The queries are written in standard SQL and also work in MySQL / PostgreSQL
> with tiny tweaks. Column names with spaces or dashes are wrapped in double
> quotes, e.g. `"Order Date"`, `"Sub-Category"`.

---

## Query 1 — The Big Picture (Total Sales, Profit, Margin)

```sql
SELECT
    ROUND(SUM(Sales), 2)                     AS total_sales,
    ROUND(SUM(Profit), 2)                    AS total_profit,
    ROUND(SUM(Profit) / SUM(Sales) * 100, 2) AS profit_margin_pct,
    COUNT(DISTINCT "Order ID")               AS total_orders
FROM superstore;
```

**In plain English:** This adds up all sales and all profit across the whole
company, calculates the overall profit margin as a percentage, and counts how
many unique orders there were. It answers *"How big and how healthy is the
business?"*

---

## Query 2 — Sales & Profit by Region

```sql
SELECT
    Region,
    ROUND(SUM(Sales), 2)                     AS total_sales,
    ROUND(SUM(Profit), 2)                    AS total_profit,
    ROUND(SUM(Profit) / SUM(Sales) * 100, 2) AS profit_margin_pct
FROM superstore
GROUP BY Region
ORDER BY total_sales DESC;
```

**In plain English:** This groups every sale into its region (West, East,
Central, South) and totals sales and profit for each. `ORDER BY total_sales
DESC` puts the biggest region at the top. It reveals which regions carry the
business — and whether any sell a lot but earn little.

---

## Query 3 — Most Profitable Product Categories

```sql
SELECT
    Category,
    ROUND(SUM(Sales), 2)                     AS total_sales,
    ROUND(SUM(Profit), 2)                    AS total_profit,
    ROUND(SUM(Profit) / SUM(Sales) * 100, 2) AS profit_margin_pct
FROM superstore
GROUP BY Category
ORDER BY total_profit DESC;
```

**In plain English:** This compares the three big product groups — Furniture,
Office Supplies, and Technology — by how much profit each brings in. It shows
which category actually makes money versus which just makes noise.

---

## Query 4 — Sub-Categories That LOSE Money

```sql
SELECT
    "Sub-Category",
    ROUND(SUM(Sales), 2)  AS total_sales,
    ROUND(SUM(Profit), 2) AS total_profit
FROM superstore
GROUP BY "Sub-Category"
HAVING SUM(Profit) < 0
ORDER BY total_profit ASC;
```

**In plain English:** `HAVING SUM(Profit) < 0` keeps only the sub-categories
where the company *lost* money overall. This is the "problem list" — the exact
products draining profit. This is often the most valuable query in the whole
project.

---

## Query 5 — Top 10 Most Profitable Products

```sql
SELECT
    "Product Name",
    ROUND(SUM(Profit), 2) AS total_profit
FROM superstore
GROUP BY "Product Name"
ORDER BY total_profit DESC
LIMIT 10;
```

**In plain English:** This ranks individual products by total profit and shows
the top 10. `LIMIT 10` keeps the list short. These are the "hero" products worth
promoting and keeping in stock.

---

## Query 6 — Customer Segment Value

```sql
SELECT
    Segment,
    ROUND(SUM(Sales), 2)                     AS total_sales,
    ROUND(SUM(Profit), 2)                    AS total_profit,
    COUNT(DISTINCT "Customer ID")            AS num_customers
FROM superstore
GROUP BY Segment
ORDER BY total_profit DESC;
```

**In plain English:** This splits results by customer type (Consumer,
Corporate, Home Office), showing how much each segment buys, how much profit it
generates, and how many unique customers it contains. It answers *"Which type of
customer is most valuable?"*

---

## Query 7 — The Discount Problem

```sql
SELECT
    Discount,
    COUNT(*)              AS num_line_items,
    ROUND(AVG(Profit), 2) AS avg_profit_per_line
FROM superstore
GROUP BY Discount
ORDER BY Discount ASC;
```

**In plain English:** This groups sales by the discount given (0%, 10%, 20%, …)
and shows the **average profit** at each discount level. Watch what happens to
average profit as the discount climbs — this usually reveals the exact point
where discounts start destroying profit.

---

## Query 8 — Year-Over-Year Sales Trend

```sql
SELECT
    SUBSTR("Order Date", -4)                 AS order_year,
    ROUND(SUM(Sales), 2)                     AS total_sales,
    ROUND(SUM(Profit), 2)                    AS total_profit
FROM superstore
GROUP BY order_year
ORDER BY order_year ASC;
```

**In plain English:** This pulls the year out of each order date and totals
sales and profit per year, so you can see growth over time.

> ⚠️ **TEMPLATE NOTE — dates can be tricky.** SQLite may import dates as text.
> The `SUBSTR("Order Date", -4)` trick above grabs the **last 4 characters**
> (the year) and works when dates look like `11/8/2017`. If your dates imported
> in a different format, this may need adjusting. If your dates are stored
> properly, you can use `STRFTIME('%Y', "Order Date")` instead. Run Query 8 and
> check that the years look right (you should see 2014–2017).

---

## Query 9 — Best Shipping Mode by Volume

```sql
SELECT
    "Ship Mode",
    COUNT(*)             AS num_line_items,
    ROUND(SUM(Sales), 2) AS total_sales
FROM superstore
GROUP BY "Ship Mode"
ORDER BY num_line_items DESC;
```

**In plain English:** This counts how often each shipping option was used and
how much revenue flowed through it — useful context for logistics discussions.

---

## Query 10 — Top 5 States by Profit

```sql
SELECT
    State,
    ROUND(SUM(Profit), 2) AS total_profit
FROM superstore
GROUP BY State
ORDER BY total_profit DESC
LIMIT 5;
```

**In plain English:** This finds the five states contributing the most profit —
the geographic strongholds of the business.

---

## 📚 SQL Concepts Used (Quick Glossary)

| Keyword | What it does (plain English) |
|---------|------------------------------|
| `SELECT` | Choose which columns to show |
| `FROM` | Which table to pull from |
| `SUM()` / `AVG()` / `COUNT()` | Add up / average / count values |
| `GROUP BY` | Bundle rows together (e.g., one row per region) |
| `ORDER BY … DESC` | Sort results (DESC = biggest first) |
| `HAVING` | Filter *after* grouping (e.g., only losing products) |
| `LIMIT` | Show only the top N rows |
| `ROUND(x, 2)` | Round to 2 decimal places for clean numbers |
| `DISTINCT` | Count unique values only |

---

> ✅ **All 10 queries are ready to copy and run.** Anything marked "TEMPLATE
> NOTE" may need a small adjustment depending on how your file imported —
> everything else should run as-is.

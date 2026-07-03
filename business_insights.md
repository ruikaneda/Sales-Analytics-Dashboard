# 💡 Business Insights

Key findings from the SQL analysis and Tableau dashboard.

> ⚠️ **IMPORTANT — READ THIS FIRST:** The numbers below are **realistic example
> figures** for this specific public dataset. They are here so your project
> looks complete. **After you run the queries yourself, confirm each number and
> replace it with your verified result.** Where a number is an estimate, it's
> marked *(example — verify)*.

---

## Insight 1 — The business sells a lot but margins are thin

- Total sales: **~$2.3M** *(example — verify)*
- Total profit: **~$286K** *(example — verify)*
- Overall profit margin: **~12.5%** *(example — verify)*

**What it means:** Revenue is healthy, but a ~12% margin is modest for retail.
Small improvements in profitability would meaningfully grow the bottom line.
This confirms leadership's suspicion: *volume is fine, profitability is the
problem.*

---

## Insight 2 — The West and East regions carry the company

- **West** typically leads in both sales and profit, followed by **East**.
- **Central** often shows the **weakest profit margin** despite decent sales
  *(example — verify)*.

**What it means:** Growth resources should protect the strong West/East regions
while investigating *why* Central converts sales into so little profit — likely a
discounting or product-mix issue.

---

## Insight 3 — Technology is the profit engine; Furniture drags

- **Technology** delivers the **highest profit** of the three categories.
- **Office Supplies** is steady and reliably profitable.
- **Furniture** generates strong sales but the **weakest profit** — some of its
  sub-categories actually lose money *(example — verify)*.

**What it means:** Not all revenue is equal. Furniture's high sales mask poor
profitability, so category-level sales targets alone are misleading.

---

## Insight 4 — Specific sub-categories lose money

- **Tables** and **Bookcases** frequently show **negative total profit** — the
  company loses money on them overall *(example — verify)*.
- **Copiers**, **Phones**, and **Accessories** are usually among the most
  profitable sub-categories *(example — verify)*.

**What it means:** A handful of products quietly erase profit earned elsewhere.
These are the clearest, fastest opportunities to fix.

---

## Insight 5 — Deep discounts destroy profit

- At **0% discount**, average profit per line is strongly positive.
- As discounts rise, average profit falls — and beyond roughly **20–30%**,
  average profit typically turns **negative** *(example — verify with Query 7)*.

**What it means:** Discounting isn't free marketing — past a certain point it
sells products at a loss. This is likely the single biggest lever on
profitability.

---

## Insight 6 — The Consumer segment is the largest

- **Consumer** is the biggest segment by sales and profit, followed by
  **Corporate**, then **Home Office** *(example — verify)*.

**What it means:** Consumer buyers are the core of the business, but Corporate
and Home Office may offer growth headroom worth targeted attention.

---

## Insight 7 — Growth is trending upward

- Sales generally **grow year over year** across the period *(example — verify
  with Query 8)*.

**What it means:** The company is expanding — which makes fixing the margin and
discount problems *now* even more valuable, since gains compound as volume grows.

---

## 🧾 One-Paragraph Summary (for your dashboard or LinkedIn)

> *Analysis of ~$2.3M in retail sales revealed a healthy top line but a modest
> ~12.5% profit margin. Technology drove the most profit while Furniture —
> despite strong sales — dragged results down, with Tables and Bookcases losing
> money outright. The biggest lever was discounting: profit turned negative once
> discounts exceeded roughly 20–30%. Recommendations focused on discount caps,
> product-mix fixes, and protecting the high-performing West and East regions.*
> *(Replace the numbers above with your verified figures.)*

---

> ✅ Every insight ties back to a specific SQL query in `sql_analysis.md`, so you
> can always show your work.

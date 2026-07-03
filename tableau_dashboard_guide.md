# 📊 Tableau Dashboard Guide (Beginner-Friendly)

This guide walks you through building an interactive sales dashboard in
**Tableau Public** (100% free), step by step. No prior Tableau experience
needed.

---

## 🛠️ Setup

1. Download **Tableau Public** (free): https://public.tableau.com/en-us/s/download
2. Install it and open it.
3. On the left under **Connect → To a File**, click **Text file** and select
   `Sample - Superstore.csv` (or **Microsoft Excel** and select your cleaned
   `superstore_clean.xlsx`).
4. Your data appears. Click the **Sheet 1** tab at the bottom to start building.

> 💡 In Tableau, **blue pills = categories (dimensions)** like Region, and
> **green pills = numbers (measures)** like Sales. You drag these "pills" onto
> the canvas to build charts.

---

## 📈 Sheet 1 — KPI Cards (Big Numbers)

Goal: three headline numbers — Total Sales, Total Profit, Profit Margin.

1. On a new sheet, double-click **Sales** in the Data pane. A single big number
   appears (the total).
2. **Worksheet → Rename Sheet** → name it `KPI - Total Sales`.
3. Repeat on new sheets for **Profit** (`KPI - Total Profit`).
4. For **Profit Margin**, first create a calculated field:
   - **Analysis → Create Calculated Field**
   - Name: `Profit Margin`
   - Formula: `SUM([Profit]) / SUM([Sales])`
   - Click **OK**, then double-click it onto a new sheet.
   - Format it as a percentage: right-click the number → **Format → Numbers →
     Percentage**.
   - Name the sheet `KPI - Profit Margin`.

---

## 🗺️ Sheet 2 — Sales by Region (Map)

Goal: a U.S. map colored by sales.

1. New sheet. Double-click **State** — Tableau auto-creates a map.
2. Drag **Sales** onto the **Color** box (in the **Marks** card).
3. Drag **Sales** onto the **Tooltip** box so numbers show on hover.
4. Rename the sheet `Map - Sales by State`.

> Darker states = higher sales. This is your visual centerpiece.

---

## 📊 Sheet 3 — Profit by Category & Sub-Category (Bar Chart)

Goal: see which products make or lose money.

1. New sheet. Drag **Profit** to **Columns**.
2. Drag **Sub-Category** to **Rows**.
3. Click the **Sort descending** button on the toolbar so the biggest bars are
   on top.
4. Drag **Profit** onto the **Color** box. Tableau will color positive profit
   one color and **negative profit another** — the money-losers pop out
   instantly.
5. Rename the sheet `Bar - Profit by Sub-Category`.

---

## 📉 Sheet 4 — Sales Trend Over Time (Line Chart)

Goal: show growth year over year.

1. New sheet. Drag **Order Date** to **Columns**.
   - Click the little **+** on the `YEAR(Order Date)` pill to expand to quarters
     or months if you want more detail.
2. Drag **Sales** to **Rows**. A line appears.
3. Drag **Profit** to **Rows** too (next to Sales) to compare both lines.
4. Rename the sheet `Line - Sales & Profit Trend`.

---

## 🥧 Sheet 5 — Sales by Segment (Pie or Bar)

Goal: compare Consumer vs Corporate vs Home Office.

1. New sheet. Drag **Segment** to **Rows** and **Sales** to **Columns**.
2. (Optional) In the **Marks** card, change the drop-down from *Automatic* to
   *Pie* if you prefer a pie chart.
3. Rename the sheet `Segment - Sales Breakdown`.

---

## 🖼️ Building the Dashboard (Combining Everything)

1. At the bottom, click the **New Dashboard** icon (looks like a grid with a
   plus).
2. Set **Size** (left panel) to **Automatic** or a fixed size like 1200 × 800.
3. **Drag each sheet** from the left panel onto the canvas:
   - Put the three **KPI cards** across the top.
   - Put the **Map** and **Bar chart** in the middle.
   - Put the **Line chart** and **Segment chart** at the bottom.
4. Add a title: **Dashboard → Show Title**, then double-click it to rename it
   `Sales Analytics Dashboard`.

---

## 🎛️ Add Interactivity (Filters)

This is what makes it feel professional.

1. Click your **Map**. Click the small **funnel icon** → **Use as Filter**.
   Now clicking a state filters the whole dashboard.
2. To add a Region dropdown: on any sheet, right-click **Region** → **Show
   Filter**. On the dashboard, right-click the filter → **Apply to Worksheets →
   All Using This Data Source**.

Now a viewer can click a region or state and every chart updates. 🎉

---

## 🌐 Publishing to Tableau Public (Free)

1. **File → Save to Tableau Public As…**
2. Sign in (create a free account if needed).
3. Give it a name like `Sales Analytics Dashboard`.
4. It uploads and opens in your browser. **Copy that URL** — this is your live
   dashboard link.
5. Paste that link into your **README.md** (the "Live Tableau dashboard" line)
   and onto your resume.

---

## 📸 Taking Screenshots for GitHub

Because GitHub can't show a live Tableau file, add images instead:

1. On your finished dashboard, take a screenshot:
   - **Windows:** press **Windows + Shift + S**, drag over the dashboard, then
     paste into Paint and save as `dashboard_overview.png`.
   - **Mac:** press **Cmd + Shift + 4**, drag over the dashboard — it saves to
     your Desktop.
2. Put the image in the repository's **`/images`** folder.
3. In `README.md`, replace the placeholder line with:

   ```
   ![Dashboard Overview](images/dashboard_overview.png)
   ```

> 📌 **Do NOT fake screenshots.** Only add real images of the dashboard you
> actually build. Until then, leave the placeholder text in place.

---

## ✅ Dashboard Checklist

- [ ] 3 KPI cards (Sales, Profit, Margin)
- [ ] Map of sales by state
- [ ] Bar chart of profit by sub-category (with negative profit highlighted)
- [ ] Line chart of sales & profit over time
- [ ] Segment breakdown
- [ ] At least one interactive filter
- [ ] Published to Tableau Public
- [ ] Screenshot saved to `/images` and linked in README

---

> 💡 **TEMPLATE NOTE:** Exact button names can vary slightly between Tableau
> versions, but the drag-and-drop logic is the same. If a button looks
> different, hover over icons to find the matching tooltip.

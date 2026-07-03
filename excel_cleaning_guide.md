# 🧹 Excel Cleaning Guide (Beginner-Friendly)

Before analysis, we inspect and clean the data in Excel. The Superstore dataset
is already fairly tidy, so this guide focuses on the **checks a good analyst
always performs** — and documents that the data is clean.

> 🎯 **Why this matters:** Employers love seeing that you *verify* data quality,
> not just chart it. Doing these checks (even when data is clean) is exactly what
> real analysts do.

---

## Step 0 — Open and Save a Working Copy

1. Open `Sample - Superstore.csv` in Excel.
2. **File → Save As** → choose **Excel Workbook (.xlsx)** and name it
   `superstore_clean.xlsx`. (Always keep the original CSV untouched.)

---

## Step 1 — Freeze the Header Row

1. Click on cell **A2**.
2. Go to **View → Freeze Panes → Freeze Top Row**.

Now the column titles stay visible as you scroll. ✅

---

## Step 2 — Check for Duplicate Rows

1. Select all data: click any cell, then press **Ctrl + A**.
2. Go to **Data → Remove Duplicates**.
3. In the pop-up, make sure **"My data has headers"** is checked, then click
   **OK**.
4. Excel will tell you how many duplicates it removed.

> 📝 Expected result: **0 duplicates removed.** Note this in your project — it
> proves the data is clean.

---

## Step 3 — Check for Blank / Missing Values

1. Select the whole data range (**Ctrl + A**).
2. Go to **Home → Find & Select → Go To Special**.
3. Choose **Blanks** and click **OK**.
4. Excel highlights any empty cells.

> 📝 Expected result: **no blanks** in this dataset. If any appear in a real
> project, you would fill or investigate them.

---

## Step 4 — Confirm Date Columns Are Real Dates

1. Click on the **Order Date** column header to select it.
2. Look at the number format box (**Home** tab). It should say **Date**.
3. If it shows **Text**, select the column → **Data → Text to Columns → Finish**.
   Excel will convert the text into real dates.
4. Repeat for **Ship Date**.

> 🎯 This matters because Tableau and SQL need real dates to build time trends.

---

## Step 5 — Check Numbers Are Numbers

1. Click the **Sales** column.
2. Look at the bottom-right **status bar** — Excel shows **Sum** and **Average**.
   - If you see a Sum, the column is numeric ✅
   - If you don't, the values are stored as text and need **Text to Columns**
     (same as Step 4).
3. Repeat for **Profit**, **Quantity**, and **Discount**.

---

## Step 6 — Create Helper Columns (Optional but Impressive)

Add two calculated columns to the right of the data.

**Profit Margin** (in the first empty column, e.g., column V):
1. In the header cell, type: `Profit Margin`
2. In the row below, type this formula:

   ```
   =IF(R2=0, 0, U2/R2)
   ```

   > `R2` is the Sales cell and `U2` is the Profit cell. **Check your own column
   > letters** — they may differ. Then format the column as **Percentage**.

**Order Year** (next empty column):
1. Header: `Order Year`
2. Formula:

   ```
   =YEAR(C2)
   ```

   > `C2` is the Order Date cell. Adjust the letter to match your file.

3. To apply a formula down the whole column: click the cell, then
   **double-click the small square** at the bottom-right corner of the cell.

---

## Step 7 — Build a Quick Pivot Table (Sanity Check)

This confirms your data makes sense before you move to SQL/Tableau.

1. Click any cell in the data.
2. Go to **Insert → PivotTable → OK**.
3. In the field list on the right:
   - Drag **Region** into the **Rows** box.
   - Drag **Sales** into the **Values** box.
   - Drag **Profit** into the **Values** box.
4. You now see total sales and profit per region.

> 📝 Expected: four regions (West, East, Central, South) with West typically
> highest in sales. If your totals look reasonable, your data is ready.

---

## Step 8 — Save

Press **Ctrl + S**. Your cleaned file `superstore_clean.xlsx` is ready for
Tableau, and the original CSV is ready for SQL.

---

## ✅ Cleaning Summary (for your project write-up)

Copy this into your notes:

- Verified 9,994 rows, 21 columns
- Duplicates checked → 0 found
- Blank values checked → none found
- Date columns confirmed as valid dates
- Numeric columns (Sales, Profit, Quantity, Discount) confirmed numeric
- Added calculated fields: Profit Margin, Order Year
- Validated totals with a pivot table by region

---

> 📌 **TEMPLATE NOTE:** Your exact column letters (R, U, C above) depend on how
> your file loads. Always click the actual cell to confirm before typing a
> formula.

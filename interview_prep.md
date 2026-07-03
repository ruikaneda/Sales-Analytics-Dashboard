# 🎤 Interview Prep

Practice questions and strong sample answers so you can confidently explain this
project. Read the answers, then **rewrite them in your own words** — interviewers
can tell memorized scripts from real understanding.

> 📝 Sample answers use example figures. Replace them with your verified numbers.

---

## 🗣️ The 30-Second Project Pitch (memorize the shape, not the words)

> "I built an end-to-end sales analytics project on a ~10,000-row retail dataset.
> I cleaned the data in Excel, used SQL to analyze profit across regions,
> products, and discount levels, and built an interactive Tableau dashboard. The
> key finding was that the business was selling well but discounting too deeply —
> profit went negative past about a 20% discount — so I recommended a discount
> cap and fixing a few money-losing product lines."

---

## Category 1 — About the Project

**Q: Walk me through this project.**
A: Start with the *business problem* (sales growing but profit flat), then your
*process* (Excel cleaning → SQL analysis → Tableau dashboard), then the *key
insight* (discounts eroding profit), and end with your *recommendation*
(discount cap). Keep it under 90 seconds.

**Q: Why did you choose this dataset?**
A: It mirrors real retail data — orders, products, regions, discounts, and
profit — so it let me practice the full analyst workflow: cleaning, querying,
visualizing, and making recommendations that a business could actually act on.

**Q: What was the hardest part?**
A: Honest answer works best. Example: "Getting the date field to behave in SQL —
it imported as text, so I had to extract the year carefully and validate the
results against Excel before trusting my trend analysis."

---

## Category 2 — SQL Questions

**Q: What does GROUP BY do?**
A: It bundles rows that share a value into a single summary row. For example,
`GROUP BY Region` turns thousands of rows into one row per region so I can total
sales and profit for each.

**Q: What's the difference between WHERE and HAVING?**
A: `WHERE` filters individual rows *before* grouping; `HAVING` filters *after*
grouping, on the grouped results. I used `HAVING SUM(Profit) < 0` to show only
sub-categories that lost money overall.

**Q: How did you find the products losing money?**
A: I grouped by sub-category, summed profit, and used `HAVING SUM(Profit) < 0` to
keep only the negative ones. That surfaced Tables and Bookcases as the main
culprits.

**Q: What aggregate functions did you use?**
A: `SUM` for totals, `AVG` for average profit per discount level, `COUNT` for
order and customer counts, and `ROUND` to clean up the decimals.

---

## Category 3 — Tableau / Visualization Questions

**Q: Why Tableau over just Excel charts?**
A: Tableau makes the analysis *interactive* — stakeholders can click a region or
state and every chart updates. It also handles maps and large datasets more
smoothly, and it's easy to publish and share a live link.

**Q: How did you make money-losing products obvious?**
A: I put Profit on the color of the bar chart, so negative-profit sub-categories
render in a distinct color and jump out immediately — no reading required.

**Q: What makes a good dashboard?**
A: It answers the key questions fast, has a clear hierarchy (big KPIs on top,
detail below), uses color intentionally, and is interactive without being
cluttered. The goal is a decision in seconds, not a data dump.

---

## Category 4 — Business / "So What" Questions

**Q: What was your most important insight?**
A: That discounting was the biggest lever on profit — past roughly 20%, average
profit per sale went negative. It reframed the problem from "sell more" to "sell
smarter."

**Q: What would you recommend to leadership?**
A: Three things: cap standard discounts around 20% with approval needed beyond
that, fix or drop the money-losing sub-categories, and investigate why the
Central region's margin lags. I'd also make the dashboard a monthly report.

**Q: How would you measure if your recommendation worked?**
A: Track profit margin month over month after the discount cap, watch whether the
previously money-losing sub-categories turn positive, and compare Central's
margin against the other regions over time.

**Q: What would you do differently or explore next?**
A: I'd add cost data to analyze true unit economics, segment customers by
lifetime value, and forecast sales to plan inventory. I'd also A/B test the
discount cap before rolling it out company-wide.

---

## Category 5 — Curveballs

**Q: How do you know your numbers are correct?**
A: I validated across tools — my SQL totals matched my Excel pivot tables and my
Tableau KPIs. When three independent methods agree, I trust the result.

**Q: This is a sample dataset — is that a limitation?**
A: Yes, and I'd say so honestly. It's clean and static, so real work would
involve messier data, more validation, and refreshing data over time. But the
*analytical process* — clean, query, visualize, recommend — is identical to what
I'd do on the job.

---

## ✅ Confidence Checklist Before an Interview

- [ ] I can give the 30-second pitch without notes
- [ ] I can explain GROUP BY, HAVING, and one query out loud
- [ ] I can name my top insight and my top recommendation
- [ ] I can open my Tableau dashboard and walk through it live
- [ ] I know my key numbers *and* I've verified them myself
- [ ] I can honestly name one limitation and one next step

---

> 💪 **Biggest tip:** Interviewers care less about perfect SQL and more about
> whether you can turn data into a decision. Always end an answer with the
> business impact.

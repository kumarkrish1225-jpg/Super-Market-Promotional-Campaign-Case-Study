# Supermarket Promotion Analysis (Difference-in-Differences)

Did the promotion actually work, or would sales have looked the same without it?

That's the question this project answers. A simple before/after comparison can't tell you that — spending naturally moves up and down week to week regardless of any campaign. So instead I used a **Difference-in-Differences (DiD)** approach: compare how much the promoted group changed against how much a control group changed over the same weeks, and whatever's left over is the actual effect of the promotion.

## The data
Weekly transaction data for supermarket customers, split by category (wine, fruit, meat, fish, sweets, regular products), plus purchase behavior like web visits, store purchases, and deal usage. Each customer is flagged as promo-exposed or not. A data dictionary is included on the Code Sheet tab.

## What I did
- Built pivot tables to get total and average spend by week, broken out by promo vs. no-promo
- Made a pivot chart to see the trend visually before doing any math
- Used `AVERAGEIFS` to pull specific numbers (e.g. avg spend for promo customers in week 3)
- Ran the DiD calculation:
  - Change in treatment group (post minus pre)
  - Change in control group (post minus pre)
  - **DiD = treatment change − control change**
- Redid it a second time using averages instead of totals, since the pre-period had more weeks than the post-period, and pulled the numbers dynamically with `GETPIVOTDATA` so it updates if the pivot changes

## Takeaway
The DiD estimate strips out the trend that would've happened anyway and leaves just the effect of the promotion — which is the number that actually matters if you're deciding whether to run it again.

## Built with
Excel — PivotTables, PivotCharts, AVERAGEIFS, GETPIVOTDATA

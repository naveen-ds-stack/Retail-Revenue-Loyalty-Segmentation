# Retail Revenue & Loyalty Segmentation

Clothing drives $104K of revenue (45%+ of total) while 3,116 loyal customers represent the highest-value retention target. This project analyzes 3,900 retail transactions across Python, PostgreSQL, and Power BI to uncover spending patterns, segment customers by loyalty, and surface actionable pricing and retention recommendations.

---

## Business Problem

A retail business needs to understand where its revenue is concentrated, which customers are worth retaining, and whether its discount strategy is helping or eroding margins. This project answers those questions by building a full analytics pipeline from raw transaction data to an interactive executive dashboard.

---

## Key Findings

| Finding | Detail |
|---|---|
| Top revenue category | Clothing — $104,264 (45%+ of total) |
| Loyal customers | 3,116 out of 3,900 (79.9%) |
| Male vs female revenue gap | Male customers generate 2.1x more total revenue ($157K vs $75K) — gap is volume-driven, not behavioural |
| Outerwear pattern | Lowest order volume but highest average spend per transaction — premium upsell opportunity |
| Subscribers vs non-subscribers | Subscribers show higher average spend and total revenue contribution |
| Missing data resolved | 37 Review Rating nulls imputed using category-level median to preserve data integrity |

**Critical insight:** The male/female revenue gap is driven entirely by transaction volume, not average spend per customer. Both genders spend similarly per order. This means the retention strategy should focus on increasing purchase frequency for female customers rather than increasing their spend per visit.

---

## Business Recommendations

- **Loyalty program priority:** Target the 3,116 loyal customers with exclusive benefits before acquiring new ones — retention is cheaper than acquisition
- **Outerwear pricing:** Low volume but high average spend signals a premium segment willing to pay more — test price increases or bundling
- **Discount audit:** Discount usage varies significantly by product. Products with high discount dependency but average revenue are eroding margin without volume payoff
- **Subscription growth:** Subscribers outperform non-subscribers on both spend and frequency — subscriber conversion should be a primary CRM goal
- **Female customer frequency:** Close the revenue gap by increasing purchase occasions for female customers, not by changing price points

---

## Analytical Workflow

**Step 1 — Data Cleaning (Python)**
- Loaded 3,900-row dataset into pandas
- Standardised column names for database compatibility
- Resolved 37 missing Review Rating values using category-level median imputation (preserves segment-specific rating patterns better than global median)

**Step 2 — Feature Engineering (Python)**
- `age_group`: Young Adult, Adult, Middle-aged, Senior (binned from continuous age)
- `purchase_frequency_days`: Numeric interval mapped from textual frequency labels (enables quantitative analysis of purchase cadence)

**Step 3 — Database Integration (PostgreSQL)**
- Cleaned DataFrame loaded into PostgreSQL
- Supports reproducible SQL-based business analysis independent of Python environment

**Step 4 — SQL Business Analysis (10 queries)**

| # | Business Question |
|---|---|
| Q1 | Total revenue by gender |
| Q2 | Discount users who still spend above average |
| Q3 | Top 5 products by average review rating |
| Q4 | Average purchase amount: Standard vs Express shipping |
| Q5 | Subscriber vs non-subscriber spend and revenue comparison |
| Q6 | Top 5 products with highest discount purchase rates |
| Q7 | Customer segmentation: New, Returning, Loyal (SQL CTE) |
| Q8 | Top 3 products within each category (window function) |
| Q9 | Repeat buyers and subscription behaviour correlation |
| Q10 | Revenue contribution by age group |

**Step 5 — Power BI Dashboard**
- KPI cards: total customers, average purchase amount, average review rating, subscription split
- Revenue and sales by category
- Revenue and sales by age group
- Slicers: subscription status, gender, category, shipping type

---

## Tech Stack

- Python, pandas for data cleaning and feature engineering
- PostgreSQL for relational storage and SQL analysis
- SQL for 10 business queries (aggregations, CTEs, window functions)
- Power BI for interactive executive dashboard
- Jupyter Notebook for Python workflow

---

## Dataset

- 3,900 rows, 18 columns
- Customer demographics: Age, Gender, Location, Subscription Status
- Purchase details: Item, Category, Amount, Season, Size, Color
- Behaviour: Discount Applied, Promo Code, Previous Purchases, Frequency, Review Rating, Shipping Type

---

## Repository Structure

```
retail-revenue-loyalty-segmentation/
├── README.md
├── customer_shopping_behavior_analysis.ipynb
├── customer_shopping_behavior_sql_queries.sql
├── customer_shopping_behavior_dashboard.pbix
├── data/
│   └── customer_shopping_behavior.csv
└── screenshots/
    ├── sql_01_revenue_by_gender.png
    ├── sql_02_high_spending_discount_users.png
    ├── sql_03_top_5_products_by_rating.png
    ├── sql_04_shipping_type_comparison.png
    ├── sql_05_subscribers_vs_nonsubscribers.png
    ├── sql_06_discount_dependent_products.png
    ├── sql_07_customer_segmentation.png
    ├── sql_08_top_3_products_per_category.png
    ├── sql_09_repeat_buyers_subscriptions.png
    ├── sql_10_revenue_by_age_group.png
    └── power_bi_dashboard.png
```

---

## How to Run

**Python Analysis**
1. Open `customer_shopping_behavior_analysis.ipynb` in Jupyter Notebook or VS Code
2. Update the CSV file path to your local data directory
3. Run all cells in sequence to reproduce cleaning and feature engineering

**SQL Analysis**
1. Create the database and customer table in PostgreSQL
2. Load the cleaned dataset exported from the Python notebook
3. Run queries from `customer_shopping_behavior_sql_queries.sql`

**Power BI Dashboard**
1. Open `customer_shopping_behavior_dashboard.pbix` in Power BI Desktop
2. Connect to your PostgreSQL database or import the cleaned CSV directly

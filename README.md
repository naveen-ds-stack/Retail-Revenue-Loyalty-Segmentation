# Customer Shopping Behavior Analysis

Customer Shopping Behavior Analysis is an end-to-end data analytics project that combines Python, SQL, PostgreSQL, and Power BI to study purchase patterns, customer segments, product performance, and subscription behavior using 3,900 transaction records. The project moves from data cleaning and feature engineering to database analysis and dashboard storytelling for business decision-making.

## Project Overview

This project analyzes customer shopping behavior across multiple product categories to uncover insights about spending patterns, loyalty, ratings, shipping preferences, and customer demographics. The goal is to support strategic business decisions using transactional and behavioral data.

## Tech Stack

- Python and pandas for data loading, cleaning, transformation, and exploratory analysis.
- SQL for business query analysis.
- PostgreSQL for storing the cleaned data and running analysis queries.
- Power BI for interactive dashboard creation and presentation of insights.
- Jupyter Notebook for the Python workflow.

## Dataset Summary

- Rows: 3,900
- Columns: 18
- Key features:
  - Customer demographics: Age, Gender, Location, Subscription Status
  - Purchase details: Item Purchased, Category, Purchase Amount, Season, Size, Color
  - Shopping behavior: Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type
- Missing data: 37 values in the Review Rating column before cleaning.

## Key Columns

- Customer ID
- Age
- Gender
- Item Purchased
- Category
- Purchase Amount
- Location
- Size
- Color
- Season
- Review Rating
- Subscription Status
- Shipping Type
- Discount Applied
- Promo Code Used
- Previous Purchases
- Payment Method
- Frequency of Purchases

## Workflow

### 1. Data Cleaning in Python
The notebook loads the shopping dataset into pandas, explores the structure with `head()`, `info()`, and `describe()`, and checks for missing values. Missing values in `Review Rating` are filled using the median rating within each product category, and column names are standardized for better usability.

### 2. Feature Engineering
The project creates an `age_group` column by binning customer ages into groups such as Young Adult, Adult, Middle-aged, and Senior. It also builds a `purchase_frequency_days` column by mapping textual purchase frequency values into numeric day intervals.

### 3. Database Integration
The cleaned DataFrame is loaded into PostgreSQL for SQL-based analysis. This database layer supports business queries focused on revenue, loyalty, discounts, and subscriptions.

### 4. SQL Business Analysis
The SQL script answers several practical business questions, including:
- Revenue by gender
- High-spending discount users
- Top 5 products by rating
- Average purchase amount by shipping type
- Subscribers vs. non-subscribers
- Products with the highest discount purchase rates
- Customer segmentation into New, Returning, and Loyal groups
- Top 3 products in each category
- Repeat buyers and subscription behavior
- Revenue contribution by age group

### 5. Power BI Dashboard
The project includes an interactive Power BI dashboard with KPI cards and visual summaries for:
- Number of customers
- Average purchase amount
- Average review rating
- Subscription split
- Revenue by category
- Sales by category
- Revenue by age group
- Sales by age group

## Key Insights

- Clothing leads both revenue and sales volume among the categories shown in the dashboard.
- The dataset shows a strong concentration of loyal customers.
- Subscribers and non-subscribers can be compared to understand revenue contribution and behavior differences.
- Age group analysis helps identify the most valuable customer segment.
- Discount usage varies across product types, which can inform pricing strategy.

## Business Recommendations

- Promote subscriber-exclusive benefits to improve subscription growth.
- Create loyalty programs to move repeat buyers into the loyal segment.
- Review discount policy to balance sales growth with margin control.
- Highlight top-rated and best-selling products in campaigns.
- Target high-revenue age groups and express-shipping users more effectively.

## Repository Structure

```bash
.
├── customer_shopping_python.ipynb
├── customer_shopping_sql_queries.sql
├── Customer-Shopping-Behavior-Analysis-1.pdf
└── README.md
```

## How to Run

### Python Analysis
1. Open `customer_shopping_python.ipynb` in Jupyter Notebook or VS Code.
2. Update the dataset file path if needed, because the notebook currently references a local CSV path.
3. Run the notebook cells in sequence to reproduce preprocessing and feature engineering steps.

### SQL Analysis
1. Create the target database and customer table structure in PostgreSQL or a compatible SQL environment.
2. Load the cleaned dataset into the database.
3. Run the queries from `customer_shopping_sql_queries.sql` to reproduce the business analysis.

### Power BI Dashboard
1. Import the cleaned dataset or connect Power BI to the PostgreSQL database used in the project.
2. Recreate visuals for KPIs, category-level revenue, sales patterns, subscription split, and age-group performance.
3. Add slicers for subscription status, gender, category, and shipping type to make the dashboard interactive.

## Resume-Ready Summary

This project demonstrates a complete analytics workflow: cleaning customer purchase data in Python, transforming and loading it into PostgreSQL, answering business questions with SQL, and building a Power BI dashboard for executive-friendly reporting.

## License

This project is intended for portfolio and educational use.

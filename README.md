# Customer Shopping Behavior Analysis

Customer Shopping Behavior Analysis is an end-to-end data analytics project that combines Python, SQL, PostgreSQL, and Power BI to study purchase patterns, customer segments, product performance, and subscription behavior using 3,900 transaction records. The project moves from data cleaning and feature engineering to database analysis and dashboard storytelling for business decision-making.
## Project overview

This project analyzes customer shopping behavior across multiple product categories to uncover insights about spending patterns, loyalty, ratings, shipping preferences, and customer demographics. The presentation states that the main goal is to guide strategic business decisions using transactional and behavioral data .

## Tech stack

- Python and pandas for data loading, cleaning, transformation, and exploratory analysis 
- SQL for business query analysis
- PostgreSQL for storing the cleaned data and running analysis queries 
- Power BI for interactive dashboard creation and presentation of insights 
- Jupyter Notebook for the Python workflow 

## Dataset summary

The dataset contains 3,900 rows and 18 columns covering customer demographics, purchase details, and shopping behavior fields such as discount usage, previous purchases, frequency, review rating, and shipping type . The project also identifies 37 missing values in the `Review Rating` column before cleaning.

### Key columns

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

### 1. Data cleaning in Python

The notebook loads the shopping dataset into pandas, explores the structure with `head()`, `info()`, and `describe()`, and checks for missing values . Missing values in `Review Rating` are filled using the median rating within each product category, and column names are standardized for better usability .

### 2. Feature engineering

The project creates an `agegroup` column by binning customer ages into groups such as Young Adult, Adult, Middle-aged, and Senior [1]. It also builds a `purchasefrequencydays` column by mapping textual purchase frequency values into numeric day intervals.

### 3. Database integration

The presentation notes that the cleaned DataFrame is loaded into PostgreSQL for SQL-based analysis . This database layer supports business queries focused on revenue, loyalty, discounts, and subscriptions.

### 4. SQL business analysis

The SQL script answers several practical business questions, including revenue by gender, high-spending discount users, top-rated products, subscriber behavior, discount-heavy products, and age-group revenue contribution. It also includes customer segmentation logic and a ranked top-products-per-category query using a window function .

### 5. Power BI dashboard

The presentation includes an interactive Power BI dashboard with KPI cards and visual summaries for number of customers, average purchase amount, and average review rating . It also shows slicers for subscription, gender, category, and shipping type, along with visuals for subscription split, revenue by category, sales by category, revenue by age group, and sales by age group .

## Key analyses

- Revenue comparison by gender 
- Customers using discounts while spending above average 
- Top 5 products by average review rating 
- Average purchase amount by shipping type 
- Subscribers vs. non-subscribers by customer count, average spend, and total revenue 
- Products with the highest discount purchase rates 
- Customer segmentation into New, Returning, and Loyal groups 
- Top 3 products in each category 
- Repeat buyers and subscription behavior 
- Revenue contribution by age group 

## Dashboard highlights

According to the presentation, the Power BI dashboard reports 3.9K customers, an average purchase amount of 59.76, and an average review rating of 3.75. It also highlights that Clothing leads both revenue and sales volume among categories shown in the dashboard visuals.

## Business recommendations

The presentation recommends promoting subscriber-exclusive benefits to improve subscription growth and creating loyalty programs to move repeat buyers into the loyal segment. It also suggests reviewing discount policy, highlighting high-performing products in campaigns, and targeting high-revenue age groups and express-shipping users more effectively.

## Repository structure

```bash
.
├── customer_shopping_python.ipynb
├── customer_shopping_sql_queries.sql
├── Customer-Shopping-Behavior-Analysis-1.pdf
└── README.md
```

## How to run

### Python analysis

1. Open `customer_shopping_python.ipynb` in Jupyter Notebook or VS Code .
2. Update the dataset file path if needed, because the notebook currently references a local CSV path .
3. Run the notebook cells in sequence to reproduce preprocessing and feature engineering steps .

### SQL analysis

1. Create the target database and customer table structure in PostgreSQL or a compatible SQL environment .
2. Load the cleaned dataset into the database .
3. Run the queries from `customer_shopping_sql_queries.sql` to reproduce the business analysis.

### Power BI dashboard

1. Import the cleaned dataset or connect Power BI to the PostgreSQL database used in the project .
2. Recreate visuals for KPIs, category-level revenue, sales patterns, subscription split, and age-group performance based on the presentation layout .
3. Add slicers for subscription status, gender, category, and shipping type to make the dashboard interactive .

## Resume-ready summary

This project demonstrates a complete analytics workflow: cleaning customer purchase data in Python, transforming and loading it into PostgreSQL, answering business questions with SQL, and building a Power BI dashboard for executive-friendly reporting.

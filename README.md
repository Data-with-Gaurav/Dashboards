# 1) Order to Cash Dashboard - Power BI
Power BI Order to Cash dashboard built for Executive and Regional Heads. Data insights are generated and recommendation is provided in order to improve the sales, 
reduce overdue amount and improve over all customer experience 

# Data
It consists 4 tables from sales, receivables_ledger, receivables and dunning calls dataset

## Key features of the dashboard
It contains 3 tabs 
a) Overview specially curated for executives 
b) Data insights which covers insights of Sales, Account receivable, and customer experience 
c) Recommendation which summarizes what data tells us and recommends next steps for Simco
Key features of the dashboard - Key Influencers , Python Forecasting , and Smart narrative feature

## Python Script 
Triple exponential smoothing model is used to predict sales forecast for 12 months period - Python script 

## Smart narrative & Key Influencers
Narrative is automatically generated as per filter selection and key influencers for drop in sales and increase in overdue amount is identified using in built smart narrative and key influencers in Power BI

# 2) Euro climate Data Insights - Power BI 
Euro climate data set is used to analyze Green house emissions Vs Contribution to climate change, understanding countries impacting Fossil fuels

# 3) Sustainabiity Dashboard - SAP Analytics Cloud 

## Data
Food and Beverages manufacturing company with global operations. 

## Assumptions
There is one factory location per country and multiple per region. The ‘Overview’ section of the dashboard is intended for an executive audience. The subsequent sections provide more granular detail and are intended for regional leads.

## Dashboard details
This dashboard is divided into many sections that provide comprehensive sustainability statistics across four areas – Carbon, Water Usage, Energy Efficiency and Food Waste. It helps the organisation to compare performance in each area against targets and allows for comparison across locations. This will help with abiding by regulations and with efficiency in the use of resources to bring down the firms emissions levels.

**Schema (PostgreSQL v13)**

    CREATE SCHEMA dannys_diner;
    SET search_path = dannys_diner;
    
    CREATE TABLE sales (
      "customer_id" VARCHAR(1),
      "order_date" DATE,
      "product_id" INTEGER
    );
    
    INSERT INTO sales
      ("customer_id", "order_date", "product_id")
    VALUES
      ('A', '2021-01-01', '1'),
      ('A', '2021-01-01', '2'),
      ('A', '2021-01-07', '2'),
      ('A', '2021-01-10', '3'),
      ('A', '2021-01-11', '3'),
      ('A', '2021-01-11', '3'),
      ('B', '2021-01-01', '2'),
      ('B', '2021-01-02', '2'),
      ('B', '2021-01-04', '1'),
      ('B', '2021-01-11', '1'),
      ('B', '2021-01-16', '3'),
      ('B', '2021-02-01', '3'),
      ('C', '2021-01-01', '3'),
      ('C', '2021-01-01', '3'),
      ('C', '2021-01-07', '3');
     
    
    CREATE TABLE menu (
      "product_id" INTEGER,
      "product_name" VARCHAR(5),
      "price" INTEGER
    );
    
    INSERT INTO menu
      ("product_id", "product_name", "price")
    VALUES
      ('1', 'sushi', '10'),
      ('2', 'curry', '15'),
      ('3', 'ramen', '12');
      
    
    CREATE TABLE members (
      "customer_id" VARCHAR(1),
      "join_date" DATE
    );
    
    INSERT INTO members
      ("customer_id", "join_date")
    VALUES
      ('A', '2021-01-07'),
      ('B', '2021-01-09');

---

**Query #1**

    SELECT
      	product_id,
        product_name,
        price
    FROM dannys_diner.menu
    ORDER BY price DESC
    LIMIT 5;

| product_id | product_name | price |
| ---------- | ------------ | ----- |
| 2          | curry        | 15    |
| 3          | ramen        | 12    |
| 1          | sushi        | 10    |

---

[View on DB Fiddle](https://www.db-fiddle.com/f/2rM8RAnq7h5LLDTzZiRWcd/138)




# Sales Insights Dashboard

**Project Overview:**
This project involved designing a comprehensive Power BI dashboard for a brick-and-mortar business to analyze and visualize sales trends of AtliQ hardware goods. Using Power BI and SQL, the dashboard provides an interactive and insightful view of the sales performance, enabling users to make data-driven decisions effectively.

**Key Features:**
- **Sales Trend Analysis:** Displays trends in sales performance, offering a clear visualization of patterns over time.
- **Data-Driven Insights:** Allows business users to understand and interpret sales data at a glance, making it easier to identify growth opportunities and optimize strategies.

**Tools Used:** Power BI, SQL

This project showcases the practical application of data visualization and analysis to support informed decision-making in a retail business environment.

## SQL Queries for Customer and Transaction Analysis

This document showcases various SQL queries for analyzing customer and transaction data. Each query includes a description of its purpose.

## SQL Queries
- [1. Show All Customer Records](#1-show-all-customer-records)
- [2. Total Number of Customers](#2-total-number-of-customers)
- [3. Transactions for Chennai Market](#3-transactions-for-chennai-market)
- [4. Distinct Product Codes Sold in Chennai](#4-distinct-product-codes-sold-in-chennai)
- [5. Transactions in US Dollars](#5-transactions-in-us-dollars)
- [6. Transactions in 2020 (Join by Date Table)](#6-transactions-in-2020-join-by-date-table)
- [7. Total Revenue in 2020](#7-total-revenue-in-2020)
- [8. Total Revenue in January 2020](#8-total-revenue-in-january-2020)
- [9. Total Revenue in 2020 for Chennai](#9-total-revenue-in-2020-for-chennai)

---

### 1. Show All Customer Records

This query retrieves all records from the `customers` table.

```sql
SELECT * FROM customers;
```
### 2. Total Number of Customers

This query returns the total count of customers in the customers table.

```sql
SELECT COUNT(*) FROM customers;
```

### 3.Transactions for Chennai Market

This query fetches all transaction records from the transactions table where the market code is Mark001 (Chennai).

```sql
SELECT * FROM transactions WHERE market_code = 'Mark001';
```

### 4.Distinct Product Codes Sold in Chennai

This query retrieves distinct product codes for products sold in the Chennai market.

```sql
SELECT DISTINCT product_code FROM transactions WHERE market_code = 'Mark001';
```

### 5.Transactions in US Dollars

This query displays all transactions where the currency is in USD.

```sql
SELECT * FROM transactions WHERE currency = "USD";
```

### 6. Transactions in 2020 (Join by Date Table)

This query joins the transactions table with the date table to show all transactions from the year 2020.

```sql
SELECT transactions.*, date.* 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020;
```

### 7. Total Revenue in 2020

This query calculates the total revenue generated in the year 2020, considering both INR and USD currencies.

```sql
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 
  AND (transactions.currency = "INR" OR transactions.currency = "USD");
```

### 8. Total Revenue in January 2020

This query shows the total revenue generated in January 2020.

```sql
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 
  AND date.month_name = "January" 
  AND (transactions.currency = "INR" OR transactions.currency = "USD");
```

### 9. Total Revenue in 2020 for Chennai
This query calculates the total revenue generated in 2020 for the Chennai market (market code Mark001).

```sql
SELECT SUM(transactions.sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 
  AND transactions.market_code = "Mark001";
```






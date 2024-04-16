# Exploring Walmart's Sales Dynamics

## Introduction
This initiative examines Walmart's sales data, focusing on identifying the strongest branches and products, observing sales trends across different items, and analyzing consumer behavior. Our objective is to use this information to refine and enhance the effectiveness of sales strategies. The foundation of this analysis is the dataset sourced from the [Kaggle](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting).

"For participants in this job-seeking challenge, historical sales information from 45 distinct Walmart stores across different regions is provided. With multiple departments in each store, the challenge is to predict future departmental sales. The complexity increases with the inclusion of holiday markdown events within the dataset, which significantly impact sales, although predicting which departments will be affected and to what extent remains a challenge." source

## Project Goals
The main goal of this analysis is to derive insights from Walmart's sales data, aiming to decipher the diverse factors that drive sales performance across its various branches.

## MySQL Queries
### Create database
```sql
CREATE DATABASE IF NOT EXISTS walmartSales;
```

### Create table
```sql
CREATE TABLE IF NOT EXISTS sales(
	invoice_id VARCHAR(30) NOT NULL PRIMARY KEY,
    branch VARCHAR(5) NOT NULL,
    city VARCHAR(30) NOT NULL,
    customer_type VARCHAR(30) NOT NULL,
    gender VARCHAR(30) NOT NULL,
    product_line VARCHAR(100) NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    quantity INT NOT NULL,
    tax_pct FLOAT(6,4) NOT NULL,
    total DECIMAL(12, 4) NOT NULL,
    date DATETIME NOT NULL,
    time TIME NOT NULL,
    payment VARCHAR(15) NOT NULL,
    cogs DECIMAL(10,2) NOT NULL,
    gross_margin_pct FLOAT(11,9),
    gross_income DECIMAL(12, 4),
    rating FLOAT(2, 1)
)
```
### Data cleaning

### Add the `time_of_day` column
```sql
SELECT
	*
FROM sales;

SELECT
	time,
	(CASE
		WHEN `time` BETWEEN "00:00:00" AND "12:00:00" THEN "Morning"
        WHEN `time` BETWEEN "12:01:00" AND "16:00:00" THEN "Afternoon"
        ELSE "Evening"
    END) AS time_of_day
FROM sales;

ALTER TABLE sales ADD COLUMN time_of_day VARCHAR(20);

UPDATE sales
SET time_of_day = (
	CASE
		WHEN `time` BETWEEN "00:00:00" AND "12:00:00" THEN "Morning"
        WHEN `time` BETWEEN "12:01:00" AND "16:00:00" THEN "Afternoon"
        ELSE "Evening"
    END
);
```
### Add `day_name` column
```sql
ELECT
	date,
	DAYNAME(date)
FROM sales;

ALTER TABLE sales ADD COLUMN day_name VARCHAR(10);

UPDATE sales
SET day_name = DAYNAME(date);
```
### Add month_name column
```sql
SELECT
	date,
	MONTHNAME(date)
FROM sales;

ALTER TABLE sales ADD COLUMN month_name VARCHAR(10);

UPDATE sales
SET month_name = MONTHNAME(date);
```
### General Questions
#### How many unique cities does the data have?
```sql
SELECT 
	DISTINCT city
FROM sales;
```
#### In which city is each branch?
```sql
SELECT 
	DISTINCT city,
    branch
FROM sales;
```
### Product-related Questions
How many unique product lines does the data have?
```sql
ALTER TABLE sales RENAME COLUMN `Product line` TO Product_line;

SELECT
	DISTINCT product_line
FROM sales;
```
What is the most selling product line
```sql
SELECT
	SUM(quantity) AS qty,
    product_line
FROM sales
GROUP BY product_line
ORDER BY qty DESC;

```
What is the total revenue by month
```sql
SELECT
	month_name AS month,
	SUM(total) AS total_revenue
FROM sales
GROUP BY month_name 
ORDER BY total_revenue;
```
What month had the largest COGS?
```sql
SELECT
	month_name AS month,
	SUM(cogs) AS cogs
FROM sales
GROUP BY month_name 
ORDER BY cogs;
```
What product line had the largest revenue?
```sql
SELECT
	product_line,
	SUM(total) as total_revenue
FROM sales
GROUP BY product_line
ORDER BY total_revenue DESC;
```
What is the city with the largest revenue?
```sql
SELECT
	branch,
	city,
	SUM(total) AS total_revenue
FROM sales
GROUP BY city, branch 
ORDER BY total_revenue;
```
What product line had the largest VAT?
```sql
ALTER TABLE sales RENAME COLUMN `Tax 5%` TO tax_pct;

SELECT
	product_line,
	AVG(tax_pct) as avg_tax
FROM sales
GROUP BY product_line
ORDER BY avg_tax DESC;
```
Average sales condition
```sql
-- line showing "Good", "Bad". Good if its greater than average sales

SELECT 
	AVG(quantity) AS avg_qnty
FROM sales;

SELECT
	product_line,
	CASE
		WHEN AVG(quantity) > 6 THEN "Good"
        ELSE "Bad"
    END AS remark
FROM sales
GROUP BY product_line;
```
Which branch sold more products than average product sold?
```sql
SELECT 
	branch, 
    SUM(quantity) AS qnty
FROM sales
GROUP BY branch
HAVING SUM(quantity) > (SELECT AVG(quantity) FROM sales);
```
What is the most common product line by gender
```sql
SELECT
	gender,
    product_line,
    COUNT(gender) AS total_cnt
FROM sales
GROUP BY gender, product_line
ORDER BY total_cnt DESC;
```
What is the average rating of each product line
```sql
SELECT
	ROUND(AVG(rating), 2) as avg_rating,
    product_line
FROM sales
GROUP BY product_line
ORDER BY avg_rating DESC;
```
### Customers-related Questions
How many unique customer types does the data have?
```sql
ALTER TABLE sales RENAME COLUMN `customer type` TO customer_type;

SELECT
	DISTINCT customer_type
FROM sales;
```
How many unique payment methods does the data have?
```sql
SELECT
	DISTINCT payment
FROM sales;
```
What is the most common customer type?
```sql
SELECT
	customer_type,
	count(*) as count
FROM sales
GROUP BY customer_type
ORDER BY count DESC;
```
Which customer type buys the most?
```sql
SELECT
	customer_type,
    COUNT(*) AS Purchases
FROM sales
GROUP BY customer_type;
```
What is the gender of most of the customers?
```sql
SELECT
	gender,
	COUNT(*) as gender_cnt
FROM sales
GROUP BY gender
ORDER BY gender_cnt DESC;
```
What is the gender distribution per branch?
```sql
SELECT
  branch, gender,
	COUNT(*) as gender_cnt
FROM sales
GROUP BY branch, gender
ORDER BY gender_cnt DESC;
```
Which time of the day do customers give most ratings?
```sql
SELECT
	time_of_day,
	ROUND(AVG(rating),2) AS avg_rating
FROM sales
GROUP BY time_of_day
ORDER BY avg_rating DESC;
```
Which time of the day do customers give most ratings per branch?
```sql
SELECT
	branch, time_of_day,
	ROUND(AVG(rating),3) AS avg_rating
FROM sales
GROUP BY branch, time_of_day
ORDER BY avg_rating DESC;
```
Which day fo the week has the best avg ratings?
```sql
SELECT
	day_name,
	ROUND(AVG(rating),3) AS avg_rating
FROM sales
GROUP BY day_name 
ORDER BY avg_rating DESC;
```
Which day of the week has the best average ratings per branch?
```sql
SELECT 
	branch, day_name,
	COUNT(day_name) total_sales
FROM sales
GROUP BY branch, day_name
ORDER BY total_sales DESC;
```
### Sales-related Questions
Number of sales made in each time of the day per weekday 
```sql
SELECT
	time_of_day,
	COUNT(*) AS total_sales
FROM sales
GROUP BY time_of_day 
ORDER BY total_sales DESC;
```
Which of the customer types brings the most revenue?
```sql
SELECT
	customer_type,
	SUM(total) AS total_revenue
FROM sales
GROUP BY customer_type
ORDER BY total_revenue;
```
Which city has the largest tax/VAT percent?
```sql
SELECT
	city,
    ROUND(AVG(tax_pct), 2) AS avg_tax_pct
FROM sales
GROUP BY city 
ORDER BY avg_tax_pct DESC;
```
Which customer type pays the most in VAT?
```sql
SELECT
	customer_type,
	ROUND(AVG(tax_pct),3) AS total_tax
FROM sales
GROUP BY customer_type
ORDER BY total_tax;
```
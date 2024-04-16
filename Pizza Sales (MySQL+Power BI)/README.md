# Pizza Sales Analysis Project
 This project focuses on analyzing pizza sales data using MySQL and visualizing the insights with Power BI.
## Overview
 The objective of this project is to gain actionable insights into pizza sales performance through a comprehensive analysis of the data. Leveraging MySQL for data management and Power BI for visualization, this project provides a detailed examination of various aspects of pizza sales, including revenue, order trends, popular pizza categories, and more.

## Tools Used
- MySQL: The primary database management system used for storing and querying the pizza sales data. MySQL provides robust data handling capabilities essential for conducting thorough analysis.

- Power BI: A powerful business analytics tool utilized for creating interactive and visually appealing visualizations. Power BI enables the representation of complex data sets in intuitive dashboards and reports, facilitating easy interpretation of insights.

## Analysis Process
- Data Extraction: The pizza sales data is extracted from the database using MySQL queries. This step involves retrieving relevant information such as order details, pizza categories, quantities sold, and prices.

- Data Analysis: Various analytical techniques are applied to the prepared data to uncover meaningful insights. This involves calculating key performance indicators (KPIs), identifying trends, and exploring relationships within the data.

- Visualization: The insights derived from the analysis are visualized using Power BI. Interactive charts, graphs, and reports are created to present the findings in a clear and compelling manner.

## Dashboards
![alt text](<Pizza sales.jpg>)
![alt text](<Pizza sales-1.jpg>)

## MySQL Queries
### A. KPI’s
### 1. Total Revenue:
```sql
SELECT SUM(total_price) AS Total_Revenue
FROM pizza_sales;
```
### 2. Average order Value
```sql
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value
FROM pizza_sales;
```
### 3. Total Pizzas Sold
```sql
SELECT SUM(quantity) AS Total_pizza_sold
FROM pizza_sales;
```
### 4. Total Orders
```sql
SELECT COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales;
```
### 5. Average Pizzas Per Order
```sql
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza_sales;
```
### B. Daily Trend for Total Orders
```sql
UPDATE pizza_sales
SET order_date = STR_TO_DATE(order_date, '%d-%m-%Y')
WHERE STR_TO_DATE(order_date, '%d-%m-%Y') IS NOT NULL;

ALTER TABLE pizza_sales
MODIFY COLUMN order_date DATETIME;

SELECT DISTINCT DAYNAME(order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DAYNAME(order_date)
ORDER BY Total_Orders DESC; 
```
### C. Monthly Trend for Orders
```sql
SELECT MONTHNAME(order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
FROM pizza_sales
GROUP BY MONTHNAME(order_date)
ORDER BY Total_Orders DESC;
```
### D. % of Sales by Pizza Category
```sql
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category;
```
### E. % of Sales by Pizza Size
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size;

### F. Total Pizzas Sold by Pizza Category
```sql
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC;
```
### G. Top 5 Pizzas by Revenue
```sql
SELECT pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC
LIMIT 5;
```
### H. Bottom 5 Pizzas by Revenue
```sql
SELECT pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC
LIMIT 5;
```
### I. Top 5 Pizzas by Quantity
```sql
SELECT pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
LIMIT 5;
```
### J. Bottom 5 Pizzas by Quantity
```sql
SELECT pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC
LIMIT 5;
```
### K. Top 5 Pizzas by Total Orders
```sql
SELECT pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC
LIMIT 5;
```
### L. Bottom 5 Pizzas by Total Orders
```sql
SELECT pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC
LIMIT 5;
```
### Reference & Data Source [here](https://drive.google.com/drive/folders/17U0ah6Q4MJM_wIn_Xl4fHc-1fO6Q4s6z)
# PIZZA SALES


## A. KPI’s
### 1. Total Revenue:
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;

<img width="99" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/371983cb-359a-4cce-8844-e2872061a7aa">


### 2. Average Order Value
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales;

<img width="110" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/7985ad4a-0365-47c4-9602-6edbb932a183">


### 3. Total Pizzas Sold
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;

<img width="91" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/16e33347-de56-48d2-9378-a15ef8ca60ee">


### 4. Total Orders
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales;

<img width="73" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/f169b4d3-ce5b-4a54-bc93-eac7fe30e398">


### 5. Average Pizzas Per Order
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza_sales;

<img width="118" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/939138bb-600f-4d58-b068-83bed052428d">


## B. Daily Trend for Total Orders

UPDATE pizza_sales
SET order_date = STR_TO_DATE(order_date, '%d-%m-%Y')
WHERE STR_TO_DATE(order_date, '%d-%m-%Y') IS NOT NULL;

ALTER TABLE pizza_sales
MODIFY COLUMN order_date DATETIME;

SELECT DISTINCT DAYNAME(order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DAYNAME(order_date)
ORDER BY Total_Orders DESC; 

<img width="134" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/e4c9182b-0dcc-409c-afd4-aaebbb82a67f">


## C. Monthly Trend for Orders
SELECT MONTHNAME(order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
FROM pizza_sales
GROUP BY MONTHNAME(order_date)
ORDER BY Total_Orders DESC;

<img width="145" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/feef155a-8418-444f-aaca-6b29d9fcb011">


## D. % of Sales by Pizza Category
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category;

<img width="192" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/34b825eb-09ed-4447-b485-4753e3e0b976">


## E. % of Sales by Pizza Size
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size;

<img width="169" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/98f7887e-beb5-444c-94cd-9ca73410f671">


## F. Total Pizzas Sold by Pizza Category
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC;

<img width="188" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/4aed5963-d9c6-4340-abfd-d168b06e71bd">


## G. Top 5 Pizzas by Revenue
SELECT pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC
LIMIT 5;

<img width="227" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/8eed676e-e14a-43e5-894a-0c11607f938b">



## H. Bottom 5 Pizzas by Revenue
SELECT pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC
LIMIT 5;

<img width="224" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/cc596caa-2812-43b4-89a0-b62439ad4f1e">


## I. Top 5 Pizzas by Quantity
SELECT pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
LIMIT 5;

<img width="237" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/7e275141-a715-4bc3-b202-ecc1be30341a">


## J. Bottom 5 Pizzas by Quantity
SELECT pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC
LIMIT 5;

<img width="234" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/4e1cbce2-9927-4f3a-bc51-e2e1f0abd31b">


## K. Top 5 Pizzas by Total Orders
SELECT pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC
LIMIT 5;

<img width="218" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/78c9e32a-9d9a-4859-9574-89ea5de2de87">


## L. Borrom 5 Pizzas by Total Orders
SELECT pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC
LIMIT 5;

<img width="215" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/0aa1cbaf-b25b-4716-8b59-80744b8a1c40">














# PIZZA SALES MySQL Queries:


## A. KPI’s
### 1. Total Revenue:
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Revenue</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font><font color = "silver">;</font>&nbsp;
</font>

.<img width="99" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/371983cb-359a-4cce-8844-e2872061a7aa">


### 2. Average Order Value
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">(</font>&nbsp;<font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font>&nbsp;<font color = "silver">/</font>&nbsp;<font color = "fuchsia"><i>Count</i></font><font color = "maroon">(</font><font color = "blue">DISTINCT</font>&nbsp;<font color = "maroon">order_id</font><font color = "maroon">)</font>&nbsp;<font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Avg_order_Value</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font><font color = "silver">;</font>&nbsp;
</font>


.<img width="110" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/7985ad4a-0365-47c4-9602-6edbb932a183">


### 3. Total Pizzas Sold
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">quantity</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_pizza_sold</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font><font color = "silver">;</font>&nbsp;
</font>
  
.<img width="91" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/16e33347-de56-48d2-9378-a15ef8ca60ee">


### 4. Total Orders
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "fuchsia"><i>Count</i></font><font color = "maroon">(</font><font color = "blue">DISTINCT</font>&nbsp;<font color = "maroon">order_id</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Orders</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font><font color = "silver">;</font>&nbsp;
</font>


.<img width="73" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/f169b4d3-ce5b-4a54-bc93-eac7fe30e398">


### 5. Average Pizzas Per Order
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "fuchsia"><i>Cast</i></font><font color = "maroon">(</font><font color = "fuchsia"><i>Cast</i></font><font color = "maroon">(</font><font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">quantity</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "black"><i>DECIMAL</i></font><font color = "maroon">(</font><font color = "black">10</font><font color = "silver">,</font>&nbsp;<font color = "black">2</font><font color = "maroon">)</font><font color = "maroon">)</font>&nbsp;<font color = "silver">/</font>&nbsp;<font color = "fuchsia"><i>Cast</i></font><font color = "maroon">(</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "fuchsia"><i>Count</i></font><font color = "maroon">(</font><font color = "blue">DISTINCT</font>&nbsp;<font color = "maroon">order_id</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "black"><i>DECIMAL</i></font><font color = "maroon">(</font><font color = "black">10</font><font color = "silver">,</font>&nbsp;<font color = "black">2</font><font color = "maroon">)</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "black"><i>DECIMAL</i></font><font color = "maroon">(</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "black">10</font><font color = "silver">,</font>&nbsp;<font color = "black">2</font><font color = "maroon">)</font><font color = "maroon">)</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Avg_Pizzas_per_order</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font><font color = "silver">;</font>&nbsp;
</font>


.<img width="118" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/939138bb-600f-4d58-b068-83bed052428d">


## B. Daily Trend for Total Orders

<font face="Courier New" size="2">
<font color = "blue">UPDATE</font>&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">SET</font>&nbsp;&nbsp;&nbsp;&nbsp;<font color = "maroon">order_date</font>&nbsp;<font color = "silver">=</font>&nbsp;<font color = "#FF0080"><b>Str_to_date</b></font><font color = "maroon">(</font><font color = "maroon">order_date</font><font color = "silver">,</font>&nbsp;<font color = "red">'%d-%m-%Y'</font><font color = "maroon">)</font>
<br/><font color = "blue">WHERE</font>&nbsp;&nbsp;<font color = "#FF0080"><b>Str_to_date</b></font><font color = "maroon">(</font><font color = "maroon">order_date</font><font color = "silver">,</font>&nbsp;<font color = "red">'%d-%m-%Y'</font><font color = "maroon">)</font>&nbsp;<font color = "blue">IS</font>&nbsp;<font color = "blue">NOT</font>&nbsp;<font color = "blue">NULL</font><font color = "silver">;</font>
<br/>
<br/><font color = "blue">ALTER</font>&nbsp;<font color = "blue">TABLE</font>&nbsp;<font color = "maroon">pizza_sales</font>
<br/>&nbsp;&nbsp;<font color = "maroon">modify</font>&nbsp;<font color = "blue">COLUMN</font>&nbsp;<font color = "maroon">order_date</font>&nbsp;<font color = "black"><i>DATETIME</i></font><font color = "silver">;</font>
<br/>
<br/><font color = "blue">SELECT</font>&nbsp;<font color = "blue">DISTINCT</font>&nbsp;<font color = "#FF0080"><b>Dayname</b></font><font color = "maroon">(</font><font color = "maroon">order_date</font><font color = "maroon">)</font>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">order_day</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "#FF0080"><b>Count</b></font><font color = "maroon">(</font><font color = "blue">DISTINCT</font>&nbsp;<font color = "maroon">order_id</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">total_orders</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "#FF0080"><b>Dayname</b></font><font color = "maroon">(</font><font color = "maroon">order_date</font><font color = "maroon">)</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">total_orders</font>&nbsp;<font color = "blue">DESC</font><font color = "silver">;</font>&nbsp;
</font>

.<img width="134" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/e4c9182b-0dcc-409c-afd4-aaebbb82a67f">


## C. Monthly Trend for Orders
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "#FF0080"><b>Monthname</b></font><font color = "maroon">(</font><font color = "maroon">order_date</font><font color = "maroon">)</font>&nbsp;&nbsp;&nbsp;&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Month_Name</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "fuchsia"><i>Count</i></font><font color = "maroon">(</font><font color = "blue">DISTINCT</font>&nbsp;<font color = "maroon">order_id</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Orders</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "#FF0080"><b>Monthname</b></font><font color = "maroon">(</font><font color = "maroon">order_date</font><font color = "maroon">)</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">total_orders</font>&nbsp;<font color = "blue">DESC</font><font color = "silver">;</font>&nbsp;
</font>

,<img width="145" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/feef155a-8418-444f-aaca-6b29d9fcb011"> 





## D. % of Sales by Pizza Category
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">pizza_category</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "fuchsia"><i>Cast</i></font><font color = "maroon">(</font><font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "black"><i>DECIMAL</i></font><font color = "maroon">(</font><font color = "black">10</font><font color = "silver">,</font>&nbsp;<font color = "black">2</font><font color = "maroon">)</font><font color = "maroon">)</font>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "blue">AS</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "maroon">total_revenue</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "fuchsia"><i>Cast</i></font><font color = "maroon">(</font><font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font>&nbsp;<font color = "silver">*</font>&nbsp;<font color = "black">100</font>&nbsp;<font color = "silver">/</font>&nbsp;<font color = "maroon">(</font><font color = "blue">SELECT</font>&nbsp;<font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "black"><i>DECIMAL</i></font><font color = "maroon">(</font><font color = "black">10</font><font color = "silver">,</font>&nbsp;<font color = "black">2</font><font color = "maroon">)</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "maroon">PCT</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_category</font><font color = "silver">;</font>&nbsp;
</font>

.<img width="192" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/34b825eb-09ed-4447-b485-4753e3e0b976">


## E. % of Sales by Pizza Size
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">pizza_size</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "fuchsia"><i>Cast</i></font><font color = "maroon">(</font><font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "black"><i>DECIMAL</i></font><font color = "maroon">(</font><font color = "black">10</font><font color = "silver">,</font>&nbsp;<font color = "black">2</font><font color = "maroon">)</font><font color = "maroon">)</font>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "blue">AS</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "maroon">total_revenue</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "fuchsia"><i>Cast</i></font><font color = "maroon">(</font><font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font>&nbsp;<font color = "silver">*</font>&nbsp;<font color = "black">100</font>&nbsp;<font color = "silver">/</font>&nbsp;<font color = "maroon">(</font><font color = "blue">SELECT</font>&nbsp;<font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "black"><i>DECIMAL</i></font><font color = "maroon">(</font><font color = "black">10</font><font color = "silver">,</font>&nbsp;<font color = "black">2</font><font color = "maroon">)</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "maroon">PCT</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_size</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_size</font><font color = "silver">;</font>&nbsp;
</font>


.<img width="169" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/98f7887e-beb5-444c-94cd-9ca73410f671">


## F. Total Pizzas Sold by Pizza Category
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">pizza_category</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "fuchsia"><i>Sum</i></font><font color = "maroon">(</font><font color = "maroon">quantity</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Quantity_Sold</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">WHERE</font>&nbsp;&nbsp;<font color = "fuchsia"><i>Month</i></font><font color = "maroon">(</font><font color = "maroon">order_date</font><font color = "maroon">)</font>&nbsp;<font color = "silver">=</font>&nbsp;<font color = "black">2</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_category</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">total_quantity_sold</font>&nbsp;<font color = "blue">DESC</font><font color = "silver">;</font>&nbsp;
</font>


.<img width="188" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/4aed5963-d9c6-4340-abfd-d168b06e71bd">


## G. Top 5 Pizzas by Revenue
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">pizza_name</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "#FF0080"><b>Sum</b></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Revenue</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_name</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">total_revenue</font>&nbsp;<font color = "blue">DESC</font>
<br/><font color = "blue">LIMIT</font>&nbsp;&nbsp;<font color = "black">5</font><font color = "silver">;</font>&nbsp;
</font>

.<img width="227" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/8eed676e-e14a-43e5-894a-0c11607f938b">



## H. Bottom 5 Pizzas by Revenue
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">pizza_name</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "#FF0080"><b>Round</b></font><font color = "maroon">(</font><font color = "#FF0080"><b>Sum</b></font><font color = "maroon">(</font><font color = "maroon">total_price</font><font color = "maroon">)</font><font color = "silver">,</font>&nbsp;<font color = "black">2</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Revenue</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_name</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">total_revenue</font>&nbsp;<font color = "blue">ASC</font>
<br/><font color = "blue">LIMIT</font>&nbsp;&nbsp;<font color = "black">5</font><font color = "silver">;</font>&nbsp;
</font>



.<img width="224" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/cc596caa-2812-43b4-89a0-b62439ad4f1e">


## I. Top 5 Pizzas by Quantity
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">pizza_name</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "#FF0080"><b>Sum</b></font><font color = "maroon">(</font><font color = "maroon">quantity</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Pizza_Sold</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_name</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">total_pizza_sold</font>&nbsp;<font color = "blue">DESC</font>
<br/><font color = "blue">LIMIT</font>&nbsp;&nbsp;<font color = "black">5</font><font color = "silver">;</font>&nbsp;
</font>


.<img width="237" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/7e275141-a715-4bc3-b202-ecc1be30341a">


## J. Bottom 5 Pizzas by Quantity
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">pizza_name</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "#FF0080"><b>Sum</b></font><font color = "maroon">(</font><font color = "maroon">quantity</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Pizza_Sold</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_name</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">total_pizza_sold</font>&nbsp;<font color = "blue">ASC</font>
<br/><font color = "blue">LIMIT</font>&nbsp;&nbsp;<font color = "black">5</font><font color = "silver">;</font>&nbsp;
</font>

.<img width="234" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/4e1cbce2-9927-4f3a-bc51-e2e1f0abd31b">


## K. Top 5 Pizzas by Total Orders
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">pizza_name</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "#FF0080"><b>Count</b></font><font color = "maroon">(</font><font color = "blue">DISTINCT</font>&nbsp;<font color = "maroon">order_id</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Orders</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_name</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">total_orders</font>&nbsp;<font color = "blue">DESC</font>
<br/><font color = "blue">LIMIT</font>&nbsp;&nbsp;<font color = "black">5</font><font color = "silver">;</font>&nbsp;
</font>

.<img width="218" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/78c9e32a-9d9a-4859-9574-89ea5de2de87">


## L. Borrom 5 Pizzas by Total Orders
<font face="Courier New" size="2">
<font color = "blue">SELECT</font>&nbsp;<font color = "maroon">pizza_name</font><font color = "silver">,</font>
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "#FF0080"><b>Count</b></font><font color = "maroon">(</font><font color = "blue">DISTINCT</font>&nbsp;<font color = "maroon">order_id</font><font color = "maroon">)</font>&nbsp;<font color = "blue">AS</font>&nbsp;<font color = "maroon">Total_Orders</font>
<br/><font color = "blue">FROM</font>&nbsp;&nbsp;&nbsp;<font color = "maroon">pizza_sales</font>
<br/><font color = "blue">GROUP</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">pizza_name</font>
<br/><font color = "blue">ORDER</font>&nbsp;&nbsp;<font color = "blue">BY</font>&nbsp;<font color = "maroon">total_orders</font>&nbsp;<font color = "blue">ASC</font>
<br/><font color = "blue">LIMIT</font>&nbsp;&nbsp;<font color = "black">5</font><font color = "silver">;</font>&nbsp;
</font>

.<img width="215" alt="image" src="https://github.com/MehreganEs/Projects/assets/166671357/0aa1cbaf-b25b-4716-8b59-80744b8a1c40">














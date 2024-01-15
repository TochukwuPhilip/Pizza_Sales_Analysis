![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/94b5b882-3bd0-4861-8aa2-7c56bbf52bdb)![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/9f65a51d-925c-46f0-88e4-55eb79cba397)

# Introduction
In order to practice my SQL and Power BI skills and to apply them to a real-life scenario, I looked for a simple dataset that I can use for this purpose.
This task involves the analysis of pizza sales for a local pizza outlet.
The dataset for this task was sourced from the follow-along video of Swapnjeet S (Data Tutorials).

# Data Analysis Process:
![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/50dc98b3-c68b-4bbf-949f-b4b27f054629)



# Business Problem:
The client has requested to know at a glance their pizza sales performances and trends using the following metrics and key performance indices (KPIs).
The client's requests are as follows:
### KPI’s REQUIREMENT
We need to analyze key indicators for our pizza sales data to gain insights into our business performance. Specifically, we want to calculate the following metrics:
  1.	Total Revenue: The sum of the total price of all pizza orders.
  2.	Average Order Value: The average amount spent per order, calculated by dividing the total revenue by the total number of orders.
  3.	Total Pizzas Sold: The sum of the quantities of all pizzas sold.
  4.	Total Orders: The total number of orders placed.
  5.	Average Pizzas Per Orders: The average number of pizzas sold per order, calculated by dividing the total number of pizzas sold by the total number of orders.
### CHARTS REQUIREMENT
We would like to visualize various aspects of our pizza sales data to gain insights and understand key trends. We have identified the following requirements for creating charts:
  1.	Daily Trend of Total Orders:
Create a bar chart that displays the daily trend of total orders over a specific time period. This chart will help us identify any patterns or fluctuations in order volumes on a daily basis.
  2.	Monthly Trend of Total Orders:
Create a line chart that illustrates the hourly trend of total orders throughout the day. This chart will allow us to identify peak hours or periods of high order activity.
  3.	Percentage of Sales by Pizza Category:
Create a pie chart that shows the distribution of sales across different pizza categories. This chart will provide insights into the popularity of various pizza categories and their contribution to overall sales.
  4.	Percentage of Sales by Pizza Size:
Generate a pie chart that represents the percentage of sales attributed to different pizza sizes. This chart will help us understand customer preferences for pizza sizes and their impact on sales.
  5.	Total Pizzas Sold by Pizza Category:
Create a funnel chart that presents the total number of pizzas sold for each pizza category. This chart will allow us to compare the sales performance of different pizza categories.
  6.	Top 5 Best Sellers by Revenue, Total Quantity and Total Orders: Create a bar chart highlighting the top 5 best-selling pizzas based on the Revenue, Total Quantity, Total Orders. This chart will help us identify the most popular pizza options.
  7.	 Bottom 5 Worst Sellers by Revenue, Total Quantity and Total Orders: Create a bar chart showcasing the bottom 5 worst-selling pizzas based on the Revenue, Total Quantity, Total Orders. This chart will enable us to identify underperforming or less popular pizza options.

# Get Data:
The dataset for this task is a small data and was sourced from Swapnjeet S (Data Tutorials)'s [folder](https://docs.google.com/spreadsheets/d/1mF1G56ZrwQlksmS5meWgC1yXRgeqGV2T/edit?usp=drive_link)

![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/ff307472-6217-423c-87e3-f8584e2de4e9)
The dataset consists of 12 columns and 48,620 rows.
The columns include:
pizza_id, order_id,	pizza_name_id,	quantity,	order_date,	order_time,	unit_price,	total_price,	pizza_size,	pizza_category,	pizza_ingredients and	pizza_name.

# Explore and Clean the Data:
Data Exploration consists of Variable Identification, Missing values treatment, Outlier treatment, Variable transformation, Variable creation e.t.c
The variables in this dataset have been identified (pizza_id, order_id,	pizza_name_id,	quantity,	order_date,	order_time,	unit_price,	total_price,	pizza_size,	pizza_category,	pizza_ingredients and	pizza_name).
There are no missing values as the dataset is relatively small.
![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/15dbfbb0-03ef-4325-95ea-23e0b81b8df1)
Using the View menu on Power Query helps to see the column quality, column distribution and column profile. Through this, it is observed that our dataset is clean and ready for analysis. Although some new columns and measures will be created in order to answer some questions from the client.

# Data Analysis:
I have utilized Microsoft SQL to first query the data and answer the questions from the client and further employed the use of Power BI for visualization.
The results from both analysis will be used for comparison.
### PIZZA SALES SQL QUERIES

KPI’s
-- 1. TOTAL REVENUE
SELECT ROUND(SUM(total_price),2) AS Total_Revenue
FROM pizza_sales;
 
--2. AVERAGE ORDER VALUE
SELECT SUM(total_price)/COUNT(DISTINCT order_id) AS Average_order_value
FROM pizza_sales;
 
--3. TOTAL PIZZA SOLD
SELECT SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales;
 
--4. TOTAL ORDERS
SELECT COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales;
 
--5. AVERAGE PIZZA PER ORDER
SELECT CAST(CAST(SUM(quantity)AS DECIMAL(10,2)) /CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS Average_Pizzas_Per_Order
FROM pizza_sales;
 


CHARTS REQUIREMENT
--1 DAILY TREND OF TOTAL ORDERSORDER
SELECT 
	DATENAME(DW, Order_date) as Order_Day,
	COUNT(DISTINCT Order_id) AS Total_Orders
FROM pizza_sales
GROUP BY DATENAME(DW, Order_date);

 
--2 MONTHLY TREND OF TOTAL ORDERS
SELECT 
	DATENAME(MONTH, Order_date) as Month_Name,
	COUNT(DISTINCT Order_id) AS Total_Orders
FROM pizza_sales
GROUP BY DATENAME(MONTH, Order_date)
ORDER BY Total_Orders DESC;
 


--3. PERCENTAGE OF SALES BY PIZZA CATEGORY
SELECT 
	pizza_category, SUM(total_price) AS Total_Sales,
	SUM(total_price)*100/(SELECT SUM(total_price) FROM pizza_sales) AS Percentage_of_Sales
FROM pizza_sales
GROUP BY pizza_category;
 

--4. PERCENTAGE OF SALES BY PIZZA SIZE
SELECT 
	pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) AS Total_Sales,
	CAST(SUM(total_price)*100/(SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS Percentage_of_Sales
FROM pizza_sales
GROUP BY pizza_size
ORDER BY Percentage_of_Sales DESC;
 

--5. TOP 5 BEST SELLERS BY REVENUE, TOTAL QUANTITY AND TOTAL ORDERS

TOP 5 BEST SELLERS BY REVENUE
SELECT TOP 5 pizza_name, SUM(total_price ) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC;
 

TOP 5 BEST SELLERS BY TOTAL QUANTITY
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Quantity 
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Quantity DESC;
 
TOP 5 BEST SELLERS BY TOTAL ORDERS
SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id ) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC;
 

--5. TOP 5 WORST SELLERS BY REVENUE, TOTAL QUANTITY AND TOTAL ORDERS

TOP 5 WORST SELLERS BY TOTAL QUANTITY
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Quantity 
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Quantity ASC;



TOP 5 WORST SELLERS BY REVENUE
SELECT TOP 5 pizza_name, SUM(total_price ) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC;
 

TOP 5 WORST SELLERS BY TOTAL ORDERS
SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id ) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC;

 

--NOTE
/*If we want to apply the Month, Quarter, Week filters to the above queries we
can use*/ 
WHERE clause. Follow some of below examples
SELECT DATENAME(DW, order date) AS order day, COUNT(DISTINCT order_id) AS
total orders
FROM pizza sales
WHERE MONTH(order date) = 1
GROUP BY DATENAME(DW, order date);
/*Here MONTH(order date) = 1 indicates that the output is for the month of
January. MONTH(order date) = 4 indicates output for Month of April.*/

SELECT DATENAME(DW, order date) AS order day, COUNT(DISTINCT order id) AS
total orders
FROM pizza sales
WHERE DATEPART(QUARTER, order date) = 1
GROUP BY DATENAME(DW, order date)
/*Here DATEPART(QUARTER, order date) = 1 indicates that the output is for
the Quarter 1. MONTH(order date) = 3 indicates output for Quarter 3.
SELECT pizza_category, sum(total_price) as Total_Sales, sum(total_price) * 100 /
(SELECT sum(total_price) from pizza_sales WHERE MONTH(order_date) = 1) AS PCT
from pizza_sales
WHERE MONTH(order_date) = 1
GROUP BY pizza_category;
/*Here WHERE MONTH(order_date) = 1 filters the output for the Month of January. Also, if it is applied to the main query, it should also be used in the subquery to get an accurate result.

## Data Visualization
The Key performance indicators (KPIs) have been represented on a cards on power BI to aid the clients to quickly grasp the figures because of their significance.

To achieve this, measures have been created from the model view within the Data pane.
![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/b8398a88-3136-428c-880f-32207a6874e1)

For example, to create the Total Revenue measure, under the Table Tools, I selected New Measure and typed the following formula:
Total Revenue = SUM(pizza_sales[total_price])
I reapeated this step for the remaining four measures.
![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/e65f844f-d185-4266-8e33-9bf1aa5bc82f)









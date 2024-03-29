# Pizza Sales Analysis

![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/c5f4e6fd-2cb6-40ce-ba2e-932f3e9385ad)

# Introduction
This task involves the analysis of pizza sales for a local pizza outlet.

Peetzah is a local pizza company. The management of Peetzah wants to have a dashboard that shows their daily and monthly key performance indicators and trends in order to improve their pizza sales.
The dataset for this task was sourced from Swapnjeet S (Data Tutorials).

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
Create a line chart that illustrates the monthly trend of total orders throughout the year. This chart will allow us to identify peak month or months of high order activity.
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
I have utilized Microsoft SQL to first query the data and answer the questions from the client and further utilized Power BI for visualization.
The results from both analysis will be used for comparison.

![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/9dfdfee7-8b0c-4027-a6b4-c1e3d236ef80)


# Data Visualization
## The Key performance indicators (KPIs) Requirement:
The Key performance indicators (KPIs) have been represented on a cards on power BI to aid the clients to quickly grasp the figures because of their significance.

To achieve this, measures have been created from the model view within the Data pane.

![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/b8398a88-3136-428c-880f-32207a6874e1)

For example, to create the Total Revenue measure, under the Table Tools, I selected New Measure and typed the following formula:
Total Revenue = SUM(pizza_sales[total_price])
I reapeated this step for the remaining four measures.

![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/4b20697c-2328-4dc5-b28c-e9f292ffbabf)
As at 31st December 2015, the client's KPI's stood at:
- Total Revenue:		$817,680
- Average Order Value:		49,574
- Total Pizzas Sold:		38.31
- Total Orders:			21,350
- Average Pizzas Per Orders:	2.23

## Chart Requirements:

### Daily Trend of Total Orders:
This chart will help the client identify any patterns or fluctuations in order volumes on a daily basis.

![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/22bc8a13-c1e6-43d7-ae89-53d60a3ece09)

The line chart has been used to present the daily trends of pizza Total Orders
From the chart one can see that orders are highest on Fridays at 3,540 orders followed closely by Thursdays and Saturdays.
In order to simplify the day name, a calculated column was created using the formula: Order Day = UPPER(LEFT(pizza_sales[Day Name], 3))

### Monthly Trend of Total Orders:
This chart will allow the client to identify peak month or months of high order activity.

![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/50d5c6c0-47b9-493b-8d24-f736097e1c49)
The highest total orders occur inthe months of July and January.

### Percentage of Sales by Pizza Category & Pizza Size:
The donut charts are used to show percentages/proportions of the sales by pizza categories and pizza sizes.
The first donut chart will provide insights into the popularity of various pizza categories and their contribution to overall sales.
The second donut chart will help us understand customer preferences for pizza sizes and their impact on sales.
The funnel chart emphasizes the sales by pizza categoriy
![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/c8622506-a324-44b8-8d4b-a55a0d8145bd)
- CATEGORY: Classic category contributes to Maximum Sales and Total Orders
- SIZE: Large size Pizza contributes to Maximum Sales

### Top 5 Best Sellers by Revenue, Total Quantity and Total Orders:
![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/cd7c30a3-08cf-4db2-94c8-422631385142)

- REVENUE: The Thai Chicken Pizza Contributes to maximum Revenue
- QUANTITY: The Classic Deluxe Pizza Contributes to maximum Total Quantities
- TOTAL ORDERS: The Classic Deluxe Pizza Contributes to maximum Total Orders

###  Bottom 5 Worst Sellers by Revenue, Total Quantity and Total Orders:
![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/4984ba90-1906-4c7e-8b0a-78eca66cb825)

- REVENUE: The Brie Carre Pizza contributes to minimum Revenue
- QUANTITY: The Brie Carre Pizza contributes to minimum Total Quantities
- TOTAL ORDERS: The Brie Carrs Pizza contributes to minimum Total Orders

![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/af247367-f3ca-43e6-b33a-ebaefbe0b488)

![image](https://github.com/TochukwuPhilip/Pizza_Sales_Analysis/assets/108484860/c62a1674-4a28-4e7a-8b6f-86ea1f09bc66)




# Summary:
Key Trends:
- Orders peak on Fridays, Thursdays, and Saturdays.
- July and January are the busiest months for sales.
- Classic pizzas are the most popular category, generating the highest sales and orders.
- Large pizzas are the most preferred size.
- The Classic Deluxe pizza is the top-selling individual pizza by quantity and orders, while the Thai Chicken pizza generates the most revenue.
- The Brie Carre pizza is the least popular pizza across all metrics.
  
# Recommendations:
Client may carry out the following in order to maximize revenue:
- Focus marketing efforts on Fridays, Thursdays, and Saturdays to maximize order volume.
- Develop special promotions and campaigns during July and January to capitalize on peak sales periods.
- Continue promoting classic pizzas and large sizes, as they are clear customer favorites.
- Consider strategies to boost sales of less popular pizzas, such as the Brie Carre, potentially through menu adjustments or targeted discounts.
- Explore offering more customizable options for pizzas, as this could increase appeal to a wider range of customer preferences.
- Analyze sales trends by time of day to identify potential opportunities for targeted promotions or menu adjustments (e.g., lunch specials).
- Gather customer feedback to better understand preferences and inform future menu and marketing decisions.












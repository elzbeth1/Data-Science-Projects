# Pizza Sales Insights Data Analysis Project

This Data Analysis project aims to provide insights into pizza sales performance. By analysing various aspects of the pizza sales data, using a power bi dashboard, what we will get as an end product is this powerful dashboard where we can track revenue trends, sales quantity trends, most sales happening days and so on.


## Data Source

The primary data source for this project is csv file "pizza_sales.csv" containing detailed information about the sales made.
## 🛠 Tools
- SQL Server - Data Analysis
- PowerBI - Creating Reports


## Data Cleaning/Preparation (ETL)

In the ETL phase I performed the following tasks:

 1. Loaded data and analysed the data using SQL.
 2. Cleaned and transformed data by removing null and irrelevant values. 

## Exploratory Data Analysis

EDA involved exploring the sales data to answer key questions such as:

- What is overall sales trend?
- Which pizaa'a are the top sellers? 
- What are the peak sales period?
## Data Analysis
1.	Total Revenue

```
select sum(total_price) as Revenue from pizza_sales;

```

2.	Average Order Value
```
select sum(total_price) / count(distinct order_id) as average_order_value from pizza_sales;
```
3.	Total Pizza Sold
```
select sum(quantity) as total_quantity from pizza_sales;
```
4.	Total Order
```
select count(distinct order_id) from pizza_sales;
```
5.	Average Pizza’s per Order
```
select cast(cast(sum(quantity) as decimal(10,2)) / cast(count (distinct order_id) as decimal(10,2)) as decimal(10,2)) as avg_pizzas_per_order from pizza_sales;
```
6.	Daily Trend for orders
```
select DATENAME (DW, order_date) as order_day, count(distinct order_id) as total_orders from pizza_sales group by datename(DW, order_date);
```
7.	% of sales by pizza category
```
select pizza_category, sum(total_price)*100 / (select sum(total_price) from pizza_sales) AS PCT from pizza_sales group by pizza_category
```
8.	% Sales by pizza size
```
select pizza_size, sum(total_price)*100 / (select sum(total_price) from pizza_sales) AS PCT
from pizza_sales 
group by pizza_size
order by pizza_size;
```
9.	Top 5 Pizza’s
```
select top 5 pizza_name, sum(total_price)  as total_revenue from pizza_sales
group by pizza_name order by  total_revenue desc;

```
## Results and Findings

The Sales Insights Dashboard provides stakeholders with valuable insights into the sales activities of the pizza shop. Utilizing Power BI, key performance indicators (KPIs) such as revenue and sales quantity have been derived to offer a comprehensive understanding of the sales performance.

### Features
- Base Measures and KPIs: Key metrics including Total Revenue, % of sales by pizza category etc. calculated as base measures using DAX programming in Power BI.
- Visualizations: The dashboard includes various visualizations such as bar graphs and line charts to represent sales data effectively.
- Interactivity: Stakeholders can interact with the dashboard by selecting specific parameters such a particular time and pizza type, enabling dynamic exploration of sales details.
- Filtering: Users have the option to filter data based on different criteria, allowing them to focus on specific aspects of sales performance.

### Sales Analysis Observations
#### Overview
Upon analyzing the sales data using Power BI, several key insights have been uncovered, shedding light on the performance of different pizza types and their impact on profitability.

**Note:**
These observations are derived from the comprehensive sales analysis conducted using Power BI. For a detailed view of the sales analysis dashboard and further insights, the full dashboard can be accessed and explored from my repository.


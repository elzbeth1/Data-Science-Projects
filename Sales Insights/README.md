
# Sales Insights Data Analysis Project

This Data Analysis project aims to provide insights into sales performance of a hardware company dcalled Atliq Hardwares. By analysing various aspects of the sales data, using a power bi dashboard, what we will get as an end 
product is this powerful dashboard where we can track revenue trends, sales quantity numbers year over year, track the revenue breakdown by regions and so on.


## Data Source

The primary data source for this project is SQL database dump "db_dump_version_2.sql" containing detailed information about the sales made by the company.
## 🛠 Tools
- SQL Server - Data Analysis
- PowerBI - Creating Reports


## Data Cleaning/Preparation (ETL)

In the ETL phase I performed the following tasks:

 1. Loaded data and analysed the data using SQL.
 2. Using PowerBi, created a star scheme data model by establishing relationship between the tables.
 3. Cleaned and transformed data by removing null and irrelevant values. I removed-1 values sales quantity column, 0 vales in sales amount column. 
Also removed rows having market name "New York" and "Paris" as we are concerned about the business happened only in India.
4. In the transactions table currency column was having duplicate currency values.

```
select distinct(transactions.currency) from transactions;
```
<img width="145" alt="Screenshot 2024-04-04 182820" src="https://github.com/elzbeth1/Data-Science-Projects/assets/26567886/fe880353-f477-4b93-8d2c-969fe68acdfa">


INR and USD were in two different formats.
"INR", "INR\r","USD","USD\r".

```
select count(*) from transactions where transactions.currency='USD';
```
![Screenshot 2024-04-04 185414](https://github.com/elzbeth1/Data-Science-Projects/assets/26567886/8e544361-1e19-4a33-b57c-e82ec1884f10)

```
select count(*) from transactions where transactions.currency='USD\r';
```

![Screenshot 2024-04-04 185414](https://github.com/elzbeth1/Data-Science-Projects/assets/26567886/8e544361-1e19-4a33-b57c-e82ec1884f10)

```
select count(*) from transactions where transactions.currency='INR\r';
```
![Screenshot 2024-04-04 185939](https://github.com/elzbeth1/Data-Science-Projects/assets/26567886/141fb28f-db3c-461c-9f9e-ecfd20e84cf5)
```
select count(*) from transactions where transactions.currency='INR';
```
![Screenshot 2024-04-04 190050](https://github.com/elzbeth1/Data-Science-Projects/assets/26567886/224d86dc-8671-40e4-a95a-c101d6d690eb)

Based on the situation we removed rows with the values 'INR' and 'USD' as this format has the lowest count.
## Exploratory Data Analysis

EDA involved exploring the sales data to answer key questions such as:

- What is overall sales trend?
- Which customers are the top sellers? 
- What are the peak sales period?
## Data Analysis
Show all customer records

```
SELECT * FROM customers;
```

Show total number of customers
```
SELECT count(*) FROM customers;
```
Show transactions for Chennai market (market code for chennai is Mark001
```
SELECT * FROM transactions where market_code='Mark001';
```
Show distrinct product codes that were sold in chennai
```
SELECT distinct product_code FROM transactions where market_code='Mark001';
```
Show transactions where currency is US dollars
```
SELECT * from transactions where currency="USD"
```
Show transactions in 2020 join by date table
```
SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;
```
Show total revenue in year 2020,
```
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";
```
Show total revenue in year 2020, January Month,
```
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");
```
Show total revenue in year 2020 in Chennai
```
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";
```
## Results and Findings

The Sales Insights Dashboard provides stakeholders with valuable insights into the sales activities of AtliQ hardware company. Utilizing Power BI, key performance indicators (KPIs) such as revenue and sales quantity have been derived to offer a comprehensive understanding of the sales performance.

### Features
- Base Measures and KPIs: Key metrics including revenue, sales quantity, total profit margin and profit margin% have been calculated as base measures using DAX programming in Power BI.
- Visualizations: The dashboard includes various visualizations such as bar graphs and line charts to represent sales data effectively.
- Interactivity: Stakeholders can interact with the dashboard by selecting specific parameters such as year and market (cities), enabling dynamic exploration of sales details.
- Filtering: Users have the option to filter data based on different criteria, allowing them to focus on specific aspects of sales performance.
- Zone-wise and Market-wise Analysis: The dashboard facilitates zone-wise and market-wise analysis, providing insights into regional sales trends and customer behavior. 

### Sales Analysis Observations
#### Overview
Upon analyzing the sales data using Power BI, several key insights have been uncovered, shedding light on the performance of different regions and their impact on profitability.

#### Observations
- Revenue vs. Profit Margin%: Delhi emerges as the top revenue-generating region, while Bhubaneswar leads in terms of profit margin percentage. This indicates an opportunity to focus marketing and promotional efforts in Bhubaneswar to maximize profit returns.

- Profit Margin Contribution: Mumbai stands out as the top contributor to profit margin. Further exploration into Mumbai's strategies and practices can provide valuable insights to replicate success in other regions.

#### Implications
- Strategic Marketing Investments: Allocating resources towards marketing and promotions in high-profit margin regions like Bhubaneswar can optimize profitability.
- Strategy Replication: Understanding and implementing successful strategies from top-performing regions, such as Mumbai, can enhance overall profitability and business performance.
**Note:**
These observations are derived from the comprehensive sales analysis conducted using Power BI. For a detailed view of the sales analysis dashboard and further insights, the full dashboard can be accessed and explored from my repository.


# LITA-CAPSTONE Project 1

## Project Title: Sales Data
---

### INTRODUCTION
---
The dataset was provided by the institute to analyse the sales performance of a retail store, uncover key insights such as top-selling products, regional performance, and monthly sales trends.

### Data Source 
---
The data used is provided by Incubator Hub. The data was provided in Excel workbook format, making it accessible for analysis.

### Tool used 
-	Microsoft EXCEL was used for the initial exploration of this dataset, clean and summaries the total sales by product region and months 
- SQL- Structure Query Language was used for Querying of data
- Power BI was used for the visualization
- GitHub for Portfolio Building

### Data Cleaning and Preparation
---
  In the initial phase of Data cleaning and preparations, the following action were performened
  1. Data Inspection
  2. Data Cleaning and Formatting

### DATA STRUCTURE
---
The dataset contains:
- Order ID, 
- Customer ID, 
- Product, 
- Region, 
- Order Date, 
- Quantity, 
- Unit Price.

### Exploratory Data Analysis
  ---
#### Key Performing Indicators (KPIs) used for this analysis include:
1. Total sales by product, region, and month. 
2. Total sales for each product category. 
3. The number of sales transactions in each region.
4. The highest-selling product by total sales value.
5. Total revenue per product.
6. Monthly sales totals for the current year.
7. The top 5 customers by total purchase amount.
8. The percentage of total sales contributed by each region.
9. Identify products with no sales in the last quarter.
    
### Data Analysis
---
Some of the analyses and line of queries used includes;

- Microsoft Excel
Calculated the Total Sales (unit price by Quantity)
 =(F2*G2)
View Table content
Create Database
```SQL
create database Capston_project1
```
Import Table and View
```SQL
Select *from[dbo].[Capstone_Data_sql_project_1]
```
Retrieve the total sales for each product category. 
```SQL
select Product, SUM(Quantity) as Totalsale
from [dbo].[Capstone_Data_sql_project_1]
Group by Product;
```
Find the number of sales transactions in each region.
```SQL
SELECT Region, count(*) as NumberofTransaction
from [dbo].[Capstone_Data_sql_project_1]
group by Region;
```
find the highest-selling product by total sales value
```SQL
select Top 1 product, sum(quantity*unitprice) as Totalsale
from [dbo].[Capstone_Data_sql_project_1]
group by product
order by Totalsale desc;
```
Calculate total revenue per product
```SQL
select product, sum(quantity) as TotalRevenue
from [dbo].[Capstone_Data_sql_project_1]
group by product
order by TotalRevenue desc;
```
Calculate monthly sales totals for the current year. 
```SQL
select Month(orderdate) as Month,
sum(quantity*unitprice)as Monthly_sales
from [dbo].[Capstone_Data_sql_project_1]
where year(orderdate)=year(getdate())
group by Month(orderdate);
```
Find the top 5 customers by total purchase amount. 
```SQL
select top 5 Customer_ID,
SUM(QUANTITY*UNITPRICE) AS TOTAL_PURCHASE_AMOUNT
FROM[dbo].[Capstone_Data_sql_project_1]
GROUP BY CUSTOMER_ID ORDER BY TOTAL_PURCHASE_AMOUNT DESC;
```
calculate the percentage of total sales contributed by each region.
```SQL
select Region,
sum(Quantity*unitprice) as totalsales;
sum(totalsales)*1.0/(select sum(totalsales) from[dbo].[Capstone_Data_sql_project_1]) * 100
as Percentageoftotalsales;
```
Identify products with no sales in the last quarter. 
```SQL
SELECT PRODUCT,ORDERID FROM[dbo].[Capstone_Data_sql_project_1]
WHERE NOT EXISTS(SELECT 1 FROM[dbo].[Capstone_Data_sql_project_1]
WHERE ORDERID= ORDERID AND ORDERDATE>=DATEADD(QUARTER,-1,GETDATE()));
```
### Data Visualization
---
Some report created from the data set 


### Insights


### Recommendation

 
  
  

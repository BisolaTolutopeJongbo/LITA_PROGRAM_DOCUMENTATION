# LITA_SQLCLASS_DOCUMENTATION

### PROJECT TITLE: International Breweries Sales Performance and Profitability Analysis
### PROJECT OVERVIEW
This analysis focuses on evaluating international breweries sales performance and profitability across various dimensions,
such as sales representatives, brands, regions, and countries. 
The goal is to derive actionable insights that can help improve decision-making, optimize resource allocation, 
and boost overall business performance. By analyzing sales trends, profit margins, and geographic distribution,
we aim to identify high-performing products, representatives, and markets.


### DATA USED:([International Breweries.csv](https://github.com/user-attachments/files/17278315/International.Breweries.csv)])


### TOOLS USED
- Microsft Excel for Data Cleaning
- Structured Query Language for Query of Data
- Github for portofoilo building

### DATA CLEANING & PREPARATION
To ensure accuracy and reliability in our analysis, the following data cleaning and preparation steps were performed:
- Removal of Duplicates
- Checked for Missing Values
- 	Data Type Validation

### EXPLORATORY DATA ANALYSIS

The exploratory analysis provided preliminary insights into the sales performance and helped uncover trends and patterns in the data:
- Top 5 Performing Sales Representatives:
- Most Profitable Brand 
- Best Performing Region and Country by profit
- Year Sales Trends
- Cost vs Profit
- Sales and Profitability Evolved Over the Years

```SQL
SELECT *
FROM[dbo].[International Breweries]
--ANALYSIS--
--Top Sales Representatives by Profit--

 SELECT TOP 10  SALES_REP,SUM(PROFIT)AS TOTAL_PROFIT
FROM[dbo].[International Breweries]
GROUP BY SALES_REP
ORDER BY TOTAL_PROFIT DESC

--Most Profitable Brand--
SELECT BRANDS,SUM(PROFIT) AS PROFITABLE_BRANDS
FROM[dbo].[International Breweries]
GROUP BY BRANDS
ORDER BY  PROFITABLE_BRANDS desc


--Best Performing Country by  Profit--
SELECT COUNTRIES,SUM(PROFIT) AS CountryProfit
FROM [International Breweries]
GROUP BY COUNTRIES
ORDER BY CountryProfit desc

-- BRANDS PROFIT PER YEAR--
SELECT BRANDS,SUM(PROFIT) AS BrandProfitperYear
FROM [International Breweries]
WHERE YEARS IN ('2017','2018','2019') 
GROUP BY BRANDS

--Region by Sales and Profit--
SELECT REGION,SUM(QUANTITY) AS TOTAL_QUANTITY_SOLD,SUM(PROFIT) AS TOTAL_PROFIT
FROM [dbo].[International Breweries]
group by region
order by Total_profit Desc

---Cost vs Profit ---
SELECT BRANDS,Sum(COST)AS TOTAL_COST,SUM(PROFIT)AS TOTAL_PROFIT
FROM [dbo].[International Breweries]
GROUP BY BRANDS
ORDER BY  TOTAL_PROFIT DESC

--Sales and Profitability Evolved Over the Years--
SELECT BRANDS,SUM(PROFIT) AS BrandProfitperYear,SUM(QUANTITY) AS TOTAL_QUANTITY_SOLD
FROM [International Breweries]
WHERE YEARS IN ('2017','2018','2019') 
GROUP BY BRANDS
ORDER BY TOTAL_QUANTITY_SOLD DESC






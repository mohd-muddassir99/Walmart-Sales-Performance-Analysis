# Walmart-Sales-Performance-Analysis
<div align="center">
    <img src="https://preview.redd.it/lju1uyute9p51.jpg?auto=webp&s=bce4f624c4f71034738e2b4e7b7f2f6dada08905" width="600px" height="300px">
</div>

## Introduction:- 
The project consists of two dashboards (Sales & Customer) built using Tableau to help stakeholders, including sales managers and executives to analyze sales performance and customers.The objective of this project is to create a comprehensive dashboard for Walmart's sales performance. The dashboard aims to provide insights into sales, profit, and quantity metrics, allowing stakeholders to easily compare current year (CY) and previous year (PY) performance. Additionally, the dashboard offers detailed geographic sales analysis and customer performance metrics, facilitating data-driven decision-making. It will help marketing teams and management to understand customer segments and improve customer satisfaction.

## Sales Dashboard | Requirements 
**Dashboard Purpose**

The purpose of sales dashboard is to present an overview of the sales metrics and trends in order to analyze year-over-year sales performance and understand sales trends.

## **Key Requirements**
**KPI Overview** 

Display a summary of total sales, profits and quantity for the current year and the previous year.

**Sales Trends**
- ► Present the data for each KPI on a monthly basis for both the current year and the previous year.

- ► Identify months with highest and lowest sales and make them easy to recognize.

**Product Subcategory Comparison**
- ► Compare sales performance by different product subcategories for the current year and the previous year.

- ► Include a comparison of sales with profit.

**Weekly Trends for Sales & Profit**
- ► Present weekly sales and profit data for the current year.
- ► Display the average weekly values.
- ► Highlight weeks that are above and below the average to draw attention to sales & profit performance.



## Customer Dashboard | Requirements
**Dashboard Purpose**

The customer dashboard aims to provide an overview of customer data, trends and behaviors. It will help marketing teams and management to understand customer segments and improve customer satisfaction.

## **Key Requirements**
**KPI Overview** 

Display a summary of total number of customers , total sales per customer and total number of orders for the current year and the previous year.

**Customer Trends**
- ► Present the data for each KPI on a monthly basis for both the current year and the previous year.
- ► Identify months with highest and lowest sales and make them easy to recognize.

**Customer Distribution by Number of Orders**
- ► Represent the distribution of customers based on the number of orders they have placed to provide insights into customer behavior, loyalty and engagement.

**Top 10 Customers By Profit**
- ► Present the top 10 customers who have generated the highest profits for the company.
- ► Show additional information like rank, number of orders, current sales, current profit and the last order date.

## Design & Interactivity Requirements

**Dashboard Dynamic**
- ► The Dashboard should allow users to check historical data by offering them the flexibility to select any desired year.
- ► Provide users with the ability to navigate between the dashboards easily.
- ► Make the charts and graphs interactive, enabling users to filter data using the charts.

**Data Filters**

Allow users to filter data by product information like category and subcategory and by location information like region, state and city.

## Lets's Know how I fulfilled these requireements 
**Data Import and Relationship Creation** Imported four datasets: Customers, Location, Orders, and Products. Established relationships between these datasets to ensure seamless data integration and accurate analysis.

**Understanding Client Requirements** Collaborated with the client to understand their specific needs and requirements.

**Create Calculated fields and Parameters**

- Created a 'Select Year' parameter to enable dynamic filtering of data based on the selected year.

 Some Calculated fields like;
 
**1. CY Measures :-**

        ► CY Sales = IF YEAR([Order Date]) = [Select Year] THEN [Sales]
        ► CY Profit = IF YEAR([Order Date]) = [Select Year] THEN [Profit]
        ► CY Quantity = IF YEAR([Order Date]) = [Select Year] THEN [Quantity]
        ► CY Customers = IF YEAR([Order Date]) = [Select Year] THEN [Customer ID]
        ► CY Orders = IF YEAR([Order Date]) = [Select Year] THEN [Order ID]
        ► CY Sales Per Customer = SUM([CY Sales])/COUNTD([CY Customers])

**2. PY Measures :-**

       ► PY Sales = IF YEAR([Order Date]) = [Select Year]-1 THEN [Sales]
       ► PY Profit = IF YEAR([Order Date]) = [Select Year]-1 THEN [Profit]
       ► PY Quantity = IF YEAR([Order Date]) = [Select Year]-1 THEN [Quantity]
       ► PY Customers = IF YEAR([Order Date]) = [Select Year]-1 THEN [Customer ID]
       ► PY Orders = IF YEAR([Order Date]) = [Select Year]-1 THEN [Order ID]
       ► PY Sales Per Customer = SUM([PY Sales])/COUNTD([PY Customers])

**3. % Difference Calculation Compare to PY :-**

       ► % Difference Sales = (SUM([CY Sales]) - SUM([PY Sales ]))/SUM([PY Sales ])
       ► % Difference Profit = (SUM([CY Profit]) - SUM([PY Profit]))/SUM([PY Profit])
       ► % Difference Quantity = (SUM([CY Quantity]) - SUM([PY Quantity]))/SUM([PY Quantity])
       ► % Difference Customers = (COUNTD([CY Customers]) - COUNTD([PY Customers])) / COUNTD([PY Customers])
       ► % Difference Orders = (COUNTD([CY orders]) - COUNTD([PY orders])) / COUNTD([PY orders])
       ► % Difference Sales Per Customer = ([CY Sales per Customer] - [PY Sales per Customer]) / [PY Sales per Customer]

**4. Min/Max Calculation :-**

        ► Min/Max Sales = IF SUM([CY Sales]) = WINDOW_MAX(SUM([CY Sales]))
                          THEN SUM([CY Sales]) 
                          ELSEIF SUM([CY Sales]) = WINDOW_MIN(SUM([CY Sales])
                          THEN SUM([CY Sales]) END  

        ► Min/Max Profit = IF SUM([CY Profit]) = WINDOW_MAX(SUM([CY Profit]))
                           THEN SUM([CY Profit])
                           ELSEIF SUM([CY Profit]) = WINDOW_MIN(SUM([CY Profit]))
                           THEN SUM([CY Profit]) END

        ► Min/Max Quantity = IF SUM([CY Quantity]) = WINDOW_MAX(SUM([CY Quantity]))
                             THEN SUM([CY Quantity])
                             ELSEIF SUM([CY Quantity]) = WINDOW_MIN(SUM([CY Quantity]))
                             THEN SUM([CY Quantity]) END

        ► Min/Max Customers = IF COUNTD([CY Customers]) = WINDOW_MAX(COUNTD([CY Customers]))
                              THEN COUNTD([CY Customers])
                              ELSEIF COUNTD([CY Customers]) = WINDOW_MIN(COUNTD([CY Customers]))
                              THEN COUNTD([CY Customers]) END 

        ► Min/Max Orders = IF COUNTD([CY orders]) = WINDOW_MAX(COUNTD([CY orders]))
                           THEN COUNTD([CY orders])
                           ELSEIF COUNTD([CY orders]) = WINDOW_MIN(COUNTD([CY orders]))
                           THEN COUNTD([CY orders]) END

        ► Min/Max Sales Per Customer = IF [CY Sales per Customer] = WINDOW_MAX([CY Sales per Customer])
                                       THEN [CY Sales per Customer] 
                                       ELSEIF [CY Sales per Customer] = WINDOW_MIN([CY Sales per Customer])
                                       THEN [CY Sales per Customer] END



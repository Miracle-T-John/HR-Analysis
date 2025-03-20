# HR Analysis
## Table of Contents

- [Project Overview](#project-overview)
- [Tools](#tools)
- [Result](#result)
- [Recommendations](#recommendations)
### Project Overview

This analysis aims to evaluate employee performance and demographic
### Data Source
HR Data:  The primary dataset used for this analysis is the "sales_data.csv" file,made by the company.

### Tools 

- PowerBI(PowerQuery)- Data cleaning
- PowerBi- Visusalization

 ### Data Cleaning/Preparation

In the Initial data preparation I performed the fllowing  tasks:

  1. Data loading and inspecion
  2. Used DAX develop i

###  Exploratorry Data Analysis 

EDA involved exloring the  saales data to answer key questions, such as:
- What is the overall sales trend?
- Which productss are top sellers?
- What  are peak sales periods?

  ###Data Analysis

```sql

SELECT SUM(amount) AS total_sales
FROM sales_table;

SELECT product_id, SUM(amount) AS total_sales
FROM sales_table
GROUP BY product

SELECT product, SUM(amount) AS total_sales
FROM sales_table
GROUP BY product
ORDER BY total_sales DESC
```

### Result

The analysis results  are summarized as follows:
1. The compay's sales peak in Q4 due to holiday season demand
2.  No sales for Q4 in 2014 &  2016
3. 35-64 age group generated the highest revenue
4. Most profit made was in 2015
5. December is when we make the most sales
6. USA was the most profitable counter foi the business
 7. Least revenue generated is in july

### Recommendations
• Focus on High-Performing Markets: Allocate more resources to the top 5 countries.

• Target Key Demographics: Increase marketing efforts for the 35-64 age group.

• Optimize Product Portfolio: Discontinue or improve underperforming products.

• Leverage Seasonal Trends: Plan promotions during peak sales months.

• Improve Profit Margins: Negotiate better supplier terms for products.

• Expand Customer Base: Invest in customer acquisition strategies.

• Enhance Data Collection: Improve data quality for more accurate analvsis.

• Monitor KPIs Regularly: Establish a dashboard for real time performance tracking, in order to make data driven decisions

### Limitations
 I had to recalculte the revenue, profit columns due to wrong calculations.  There were missig columns that  could have helep understand each unique customer's purchase patterns.

# HR Analysis
## Table of Contents

- [Project Overview](#project-overview)
- [Tools](#tools)
- [Result](#result)
- [Recommendations](#recommendations)
### Project Overview

This project is designed to help HR professionals and analysst gain actionble insights into workforce data. The dashboard provides visualiztions and metrics for employee turnover, performance and more
### Data Source
HR Data:  The primary dataset used for this analysis is the "Employee_data" file,made by the company.

##Purpose
The goal of this project was to create a centralized, interactive dashboard for HR teams to:
- Track employee turnover and retention rates.
- Average training cost per employee
- Evaluate employee performance.
- Analyze workforce diversity and inclusion metrics.


## Development Process

### 1. Data Collection
- *Data Sources*: The project used two primary datasets:
  1. *Employee Data*: Contains employee details such as name, department, hire date, and job title, performance ratings and feedback.
  2. *Attendance Data*: Tracks employee attendance and leave records.

- *Data Format*: All datasets were provided in CSV format.

### Tools 

- PowerBI(PowerQuery)- Data cleaning
- Pyhon(Pandas)-Data cleaning
- PostgreeSQL
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

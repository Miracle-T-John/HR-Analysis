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
### **3. Data Transformation**
- **Tools Used**: SQL and Power Query in Power BI.
- **Steps**:
  1. Joined datasets using `Employee ID` as the primary key.
  2. Created calculated columns (e.g., tenure, turnover status).
  3. Aggregated data for key metrics (e.g., average attendance, turnover rate).

#### **SQL Code for Data Transformation**
```sql
-- Calculate employee tenure in years
SELECT 
    Employee_ID,
    DATEDIFF(year, Hire_Date, GETDATE()) AS Tenure
INTO 
    Employee_Tenure
FROM 
    Employee_Data;

-- Calculate turnover status
SELECT 
    Employee_ID,
    CASE 
        WHEN Termination_Date IS NOT NULL THEN 'Terminated'
        ELSE 'Active'
    END AS Turnover_Status
INTO 
    Turnover_Status
FROM 
    Employee_Data;

-- Aggregate attendance data
SELECT 
    Employee_ID,
    AVG(Days_Present) AS Avg_Attendance
INTO 
    Avg_Attendance
FROM 
    Attendance_Data
GROUP BY 
    Employee_ID;
```

---

### Limitations
 I had to recalculte the revenue, profit columns due to wrong calculations.  There were missig columns that  could have helep understand each unique customer's purchase patterns.

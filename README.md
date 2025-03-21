# HR Analysis
## Table of Contents

- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Purpose](#purpose)
- [Development Process](#development-process)
- [Key Features](#key-features)
- [Outcomes](#outcomes)
- [Lessons Learned](#lessons-learned)
### Project Overview

This project is designed to help HR professionals and analysst gain actionble insights into workforce data. The dashboard provides visualiztions and metrics for employee turnover, performance and more
### Data Source
HR Data:  The primary dataset used for this analysis is the "Employee_data" file,made by the company.

## Purpose
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

### *2. Data Cleaning*
- *Tools Used*: Python (Pandas) and SQL.
- *Steps*:
  1. Removed duplicate records.
  2. Handled missing values by imputing or removing them.
  3. Standardized data formats (e.g., date formats, categorical values).
  4. Anonymized sensitive employee information.

#### *Python Code for Data Cleaning*
```python
import pandas as pd

# Load raw data
employee_data = pd.read_csv("data/raw_data/employee_data.csv")
attendance_data = pd.read_csv("data/raw_data/attendance_data.csv")
performance_data = pd.read_csv("data/raw_data/performance_data.csv")

# Remove duplicates
employee_data.drop_duplicates(inplace=True)
attendance_data.drop_duplicates(inplace=True)
performance_data.drop_duplicates(inplace=True)

# Handle missing values
employee_data['Department'].fillna('Unknown', inplace=True)
attendance_data['Days Present'].fillna(0, inplace=True)
performance_data['Performance Rating'].fillna(0, inplace=True)

# Standardize date formats
employee_data['Hire Date'] = pd.to_datetime(employee_data['Hire Date'])
attendance_data['Date'] = pd.to_datetime(attendance_data['Date'])

# Save cleaned data

```
### **3. Data Transformation**
- **Tools Used**: Power Query in Power BI.
- **Steps**:
  1. Joined datasets using `Employee ID` as the primary key.
  2. Created calculated columns (e.g., tenure, turnover status).
  3. Aggregated data for key metrics (e.g., average attendance, turnover rate).

#### **PowerBI DAX Code for Data Transformation**
```DAX-- Calculate employee tenure in years

-- Average Training Cost
Average Training Cost = SUM (Cleaned_HR_Data_Analysis[Training Cost]) /[Number of Staff]

Exited Staffs = count('2nd part of the HR Dataset'[Employee ID])

Number of Staff = COUNT(Cleaned_HR_Data_Analysis[Employee ID])

Staffs Terminated = CALCULATE(COUNT(Cleaned_HR_Data_Analysis[Employee ID]), not(ISBLANK( '2nd part of the HR Dataset'[TerminationType])))

staffs terminated 2 = CALCULATE(COUNT(Cleaned_HR_Data_Analysis[Employee ID]), not(ISBLANK( '2nd part of the HR Dataset'[TerminationType])))/COUNT(Cleaned_HR_Data_Analysis[Employee ID])

Turnover Rate = divide([Exited Staffs],[Number of Staff])


Role Status = SWITCH( TRUE(), Cleaned_HR_Data_Analysis[Title] ="Area Sales Manager" , "Leadership",
Cleaned_HR_Data_Analysis[Title] = "Director of Operations", "Leadership", 
Cleaned_HR_Data_Analysis[Title] = "Director of Sales", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "IT Director", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "IT Manager -DB", "Leadership", 
Cleaned_HR_Data_Analysis[Title] = "IT Manager - Infra", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "IT Manager - Support", "Leadership", 
Cleaned_HR_Data_Analysis[Title] = "President & CEO", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "Production Manager", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "Sales Manager", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "Senior BI Manager", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "Shared Service Manager", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "Software Engineering Manager", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "Sr. Accountant", "Leadership",
Cleaned_HR_Data_Analysis[Title] = "Sr. Network Manager", "Leadership","Non Leadership")



```
### *4. Dashboard Design*
- *Tools Used*: Power BI Desktop.
- *Steps*:
  1. Designed a star schema data model with relationships between tables.
  2. Created interactive visuals, including bar charts, line charts, and KPIs.
  3. Added slicers and filters for dynamic data exploration.
  4. Applied a clean, professional theme for consistency.
---
---

### *5. Testing and Validation*
- *Steps*:
  1. Tested the dashboard with sample data to ensure accuracy.
  2. Validated key metrics (e.g., turnover rate, attendance trends) against manual calculations.
  3. Gathered feedback from HR stakeholders and made adjustments.

---

## *Key Features*
The final dashboard includes the following features:
1. *Employee Turnover Analysis*:
   - Visualizes turnover rates by department, tenure, and job role.
   - Identifies trends over time.
2. *Attendance & Leave Tracking*:
   - Tracks employee attendance and leave patterns.
   - Highlights absenteeism trends.
3. *Performance Evaluation*:
   - Displays performance ratings by employee and department.
   - Compares performance metrics over time.
4. *Diversity & Inclusion Insights*:
   - Analyzes workforce diversity across departments.
   - Tracks progress toward diversity goals.
  
5. *Training Metrics*
  - Identifies taining progress and outcome
  - Tracks training costs

---

## *Outcomes*
- *Improved Decision-Making*: HR teams can now make data-driven decisions using real-time insights.
- *Time Savings*: The dashboard reduces the time spent on manual data analysis and reporting.
- *Scalability*: The dashboard can be easily updated with new data or expanded to include additional metrics.

---

## *Lessons Learned*
- *Data Quality is Critical*: Cleaning and validating data upfront saved time during dashboard development.
- *Stakeholder Feedback is Valuable*: Regular feedback from HR stakeholders ensured the dashboard met their needs.
- *Power BI is Powerful*: Power BI’s flexibility and ease of use made it the perfect tool for this project.

---

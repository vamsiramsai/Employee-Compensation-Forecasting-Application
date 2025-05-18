# Employee-Compensation-Forecasting-Application using SQL
employee-compensation--- data -- Employee Raw Data.xlsx-- sql-- create_tables.sql-- insert_data.sql-- stored_procedures.sql--Sql Scripts


%%sql
CREATE TABLE EmployeeData (
    Name TEXT,
    Role TEXT,
    Location TEXT,
    Years_of_Experience REAL,
    Active TEXT,
    Compensation REAL,
    Last_Working_Day TEXT
)

Fix Misspelled Role: senir associate → senior associate
    %%sql
UPDATE EmployeeData
SET Role = 'senior associate'
WHERE LOWER(Role) = 'senir associate';

Replace NULL in Years_of_Experience with 0
    %%sql
UPDATE EmployeeData
SET Years_of_Experience = 0
WHERE Years_of_Experience IS NULL;

Replace NULL in Last_Working_Day with 'No'
    %%sql
UPDATE EmployeeData
SET Last_Working_Day = 'No'
WHERE Last_Working_Day IS NULL;

USER story 1: Filter Employees by Role and View Key Columns
    %%sql
SELECT 
    Name, 
    Role, 
    Location, 
    Compensation
FROM EmployeeData
WHERE Role = 'senior associate';

Toggle: Include/Exclude Inactive Employees
    %%sql
SELECT 
    Name, 
    Role, 
    Location, 
    Compensation
FROM EmployeeData
WHERE Role = 'senior associate'
  AND Active = 'Y';
    
Select a Location and View the Average Compensation
    %%sql
SELECT 
    Role,
    Location,
    AVG(Compensation) AS Avg_Compensation
FROM EmployeeData
WHERE Role = 'senior associate'
  AND Active = 'Y'
  AND Location = 'Jaipur' 
GROUP BY Location;

User Story 2: Group Employees by Years of Experience
    Step 1: Count of employess Group by Experience Ranges
        %%sql
SELECT
  '0-1' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '0-1'

UNION ALL

SELECT
  '1-2' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '1-2'

UNION ALL

SELECT
  '2-3' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '2-3'

UNION ALL

SELECT
  '3-4' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '3-4'

UNION ALL

SELECT
  '4-5' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '4-5'

UNION ALL

SELECT
  '5-6' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '5-6'

UNION ALL

SELECT
  '6-7' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '6-7'

UNION ALL

SELECT
  '7-8' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '7-8'

UNION ALL

SELECT
  '8-9' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '8-9'

UNION ALL

SELECT
  '9-10' AS Experience_Range,
  COUNT(*) AS Employee_Count
FROM EmployeeData
WHERE Years_of_Experience = '9-10'

User Story 3: Simulate Compensation Increments with SQL
    Apply a Global Fixed % Increment
    %%sql
SELECT
  Name,
  Location,
  Compensation,
  ROUND(Compensation * 1.10, 2) AS Updated_Compensation -- 10% increment
FROM EmployeeData;

Filtered Employee Data
    %%sql
SELECT
  Name,
  Role,
  Location,
  Years_of_Experience AS Experience,
  Compensation,
  ROUND(Compensation * 1.10, 2) AS Updated_Compensation,
  Active
FROM EmployeeData
WHERE Active = 'Y';

## Employee Compensation Forecasting Application

##  Overview
This application supports compensation analysis and forecasting by enabling filtering, grouping, simulation, and exporting of employee data.

---

##  Tools & Technologies Used

- SQL (Jupyter Notebook)
- SQL (Data cleaning)
- Git & GitHub

---

##   Setup Instructions

1. Clone the repository
2. Load `Employee Raw Data.csv` into your local SQL database
3. Run `create_tables.sql` to create the schema
4. Use `insert_data.sql` to populate the database
5. Use `stored_procedures.sql` to add business logic

---

##  User Stories

### 1. Filter Active Employees by Role
- Run `EmployeesData()` with Role, Location, and Active status
- View Name, Role, Location, Compensation

### 2. Group by Experience
- Run `CountByExperience()` for overall experience grouping

### 3. Simulate Increments
- Use `Updated_Compensation` column (already calculated from % increase)

### 4. Export Filtered Data
- Export results from SQL to CSV

---
# Same Employee-Compensation-Forecasting-Application using Excel in Employee Data_excel analysis.xlsx file
  1. Data Cleaning
  2. User story solving using Pivot Tables
  3. Visualizations

###  [Atchula Vamsi Ram Sai Phanindra] – Technical Assessment Project


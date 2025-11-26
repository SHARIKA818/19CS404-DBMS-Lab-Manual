# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- *MIN()* – Smallest value  
- *MAX()* – Largest value  
- *COUNT()* – Number of rows  
- *SUM()* – Total of values  
- *AVG()* – Average of values

*Syntax:*
sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;

### GROUP BY
Groups records with the same values in specified columns.
*Syntax:*
sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;

### HAVING
Filters the grouped records based on aggregate conditions.
*Syntax:*
sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;


*Question 1*

Write a SQL query to find the total amount of fruits with a unit type of 'LB'.
Note: Inventory attribute contains amount of fruits
Table: fruits

sql
SELECT
SUM(inventory) AS total
FROM fruits
WHERE unit LIKE '%LB%';


*Output:*

<img width="278" height="307" alt="image" src="https://github.com/user-attachments/assets/179db62b-e449-4b36-9e18-b57047918ffc" />


*Question 2*

Write a SQL query to find how many employees have an income greater than 50K?
Table: employee

sql
SELECT
COUNT(*) AS employees_count
FROM employee
WHERE income>50000;


*Output:*

<img width="347" height="311" alt="image" src="https://github.com/user-attachments/assets/334a0dec-26c4-447e-8019-72b4db866b5e" />

*Question 3*

Write a SQL query to find  how many employees work in California?
Table: employee

sql
SELECT
COUNT(*) AS employees_in_california
FROM employee
WHERE city='California';


*Output:*

<img width="463" height="314" alt="image" src="https://github.com/user-attachments/assets/7ae21abb-3da7-4f17-9114-8430910eb99a" />


*Question 4*

How many medical records does each doctor have?
Sample table:MedicalRecords Table

sql
SELECT
DoctorID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID
ORDER BY DoctorID ASC;


*Output:*

<img width="486" height="511" alt="image" src="https://github.com/user-attachments/assets/f85cf779-d81c-4cd5-8102-70dd47386df0" />


*Question 5*
What is the average duration of insurance coverage for patients covered by each insurance company?
Sample table:Insurance Table

sql
SELECT
InsuranceCompany,
ABS(AVG(StartDate-EndDate)) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;


*Output:*

<img width="743" height="547" alt="image" src="https://github.com/user-attachments/assets/000a4904-d248-40f7-aacc-18c4242bedb7" />


*Question 6*

How many medical records are there for each patient?
Sample table:MedicalRecords Table

sql
SELECT
PatientID,
COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID
ORDER BY PatientID;


*Output:*

<img width="448" height="557" alt="image" src="https://github.com/user-attachments/assets/d021ef01-ff72-4153-aae3-8a1e3f3eb1fd" />

*Question 7*

Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.
Sample table: employee

sql
SELECT
age,
MIN(income) AS Income
FROM employee
GROUP BY age
HAVING MIN(income)<1000000;


*Output:*

<img width="430" height="395" alt="image" src="https://github.com/user-attachments/assets/70f65d74-21a2-4dc6-b0f4-084ce0716542" />

*Question 8*

Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.
Sample table: employee1

sql
SELECT
jdate,
AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY jdate
HAVING AVG(workhour)<10;


*Output:*

<img width="465" height="309" alt="image" src="https://github.com/user-attachments/assets/9835280a-5531-4eca-aeac-31c2bfa5d38a" />


*Question 9*

Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.
Sample table: products

sql
SELECT
category_id,
product_name,
MAX(price) AS Price
FROM products
GROUP BY category_id 
HAVING MAX(price)>15;


*Output:*

<img width="646" height="353" alt="image" src="https://github.com/user-attachments/assets/1210a5a8-e28d-41eb-99d3-f8ee1acc7394" />


*Question 10*

Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.
Sample table: products

sql
SELECT
category_id,
AVG(price) AS 'AVG(Price)'
FROM products
GROUP BY category_id
HAVING AVG(price) BETWEEN 10 AND 15;


*Output:*

<img width="439" height="306" alt="image" src="https://github.com/user-attachments/assets/442cb0ad-20bb-4d95-8d43-7a4e840e4924" />

## Grade:

<img width="707" height="25" alt="image" src="https://github.com/user-attachments/assets/c5e55359-be1f-4314-9c19-1c1b05b3444b" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

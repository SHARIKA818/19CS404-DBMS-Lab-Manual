# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**

Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4.
Sample table: Surgeries

```sql
DELETE FROM Surgeries
WHERE surgery_id= 3 OR surgery_id= 4;
```

**Output:**

<img width="773" height="611" alt="image" src="https://github.com/user-attachments/assets/5b286feb-c1d6-4b06-9bb8-26399d45c9f7" />

**Question 2**

Write a SQL query to Retrieve the department name and location concatenated with a comma
Table name: dept

```sql
SELECT
dname||', '||loc AS dept_location
FROM dept;
```

**Output:**

<img width="665" height="482" alt="image" src="https://github.com/user-attachments/assets/4846bffd-5373-4b4a-9253-0333e595b6d8" />


**Question 3**

Write a query to fetch 5 to 9 records from EmployeeInfo table.

```sql
SELECT *
FROM EmployeeInfo
ORDER BY EmpID
LIMIT 5 OFFSET 4;
```

**Output:**

<img width="783" height="139" alt="image" src="https://github.com/user-attachments/assets/4d1f0bab-2596-4934-bf34-604909cbcb94" />

**Question 4**

Write a SQL query to find customers who are from the city 'London' who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.
Sample table: customer

```sql
SELECT 
customer_id,
cust_name,
city,
grade,
salesman_id
FROM customer
WHERE city IN ('London') AND grade>200;
```

**Output:**

<img width="788" height="243" alt="image" src="https://github.com/user-attachments/assets/d5e870e4-0518-4dcc-9b58-7ac748eb9fef" />


**Question 5**

Write a SQL query to Delete a Specific Surgery whose ID is 3
Sample table: Surgeries

```sql
DELETE FROM Surgeries
WHERE surgery_id=3;
```

**Output:**

<img width="780" height="263" alt="image" src="https://github.com/user-attachments/assets/9f9a4bf0-168e-4e09-a8bd-5409477c932c" />


**Question 6**

Write a SQL query to retrieve the year, month, and day from the hiredate column in the emp table.

```sql
SELECT
strftime('%Y',hiredate) AS Year,
strftime('%m',hiredate) AS Month,
strftime('%d',hiredate) AS Day
FROM emp;
```

**Output:**

<img width="629" height="360" alt="image" src="https://github.com/user-attachments/assets/f6ae6e78-219a-4dc0-b534-ed00b1987104" />


**Question 7**

Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.
Sample table: Customer

```sql
DELETE FROM Customer
WHERE WORKING_AREA IN ("New York");
```

**Output:**

<img width="794" height="401" alt="image" src="https://github.com/user-attachments/assets/5310ffd8-acfc-4d74-87ea-8cd41d46cd5e" />

**Question 8**

For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.
PRODUCTS TABLE

```sql
UPDATE sales
SET sell_price=sell_price+3
WHERE product_id IN(
SELECT product_id
FROM products
WHERE Supplier_id=4
);
```

**Output:**

<img width="794" height="207" alt="image" src="https://github.com/user-attachments/assets/92e94f71-9e6f-4a26-a62f-e2b7c9737156" />


**Question 9**

Write a SQL query to remove rows from the table 'customer' with the following condition -
1. 'cust_country' must be 'India',
2. 'cus_city' must not be 'Chennai',
Sample table: Customer

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY IN ('India') AND CUST_CITY NOT IN ('Chennai');
```

**Output:**

<img width="785" height="449" alt="image" src="https://github.com/user-attachments/assets/daa16af8-27dd-48c2-b682-77271c7a48fe" />


**Question 10**

Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.
sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```sql
UPDATE sales
SET sell_price=sell_price+(0.05*sell_price)
WHERE product_id=15 AND sale_date='2023-01-31';
```

**Output:**

<img width="795" height="238" alt="image" src="https://github.com/user-attachments/assets/de026c2d-c4d2-4d42-bc55-9080ff949b52" />

## GRADE:

<img width="896" height="40" alt="image" src="https://github.com/user-attachments/assets/0a1d3998-07a9-4c1d-bb6a-c23a73a1a724" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

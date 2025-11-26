# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

*Syntax:*
sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;


### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

*Syntax:*

sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;

### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

*Syntax:*

sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;

### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

*Syntax:*

sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;


*Question 1*

<img width="803" height="354" alt="image" src="https://github.com/user-attachments/assets/681d55fc-23b3-47f2-ab64-e53528f0c88a" />


sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;


*Output:*

<img width="795" height="409" alt="image" src="https://github.com/user-attachments/assets/eb3d8b74-3812-4dc9-945e-4917a1ca36af" />


*Question 2*

<img width="790" height="382" alt="image" src="https://github.com/user-attachments/assets/869e4098-8b4d-46e4-9f95-3e4bcf175424" />


sql
SELECT DISTINCT c.cust_name
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id AND o.purch_amt < 100
WHERE o.purch_amt IS NOT NULL;


*Output:*

<img width="389" height="492" alt="image" src="https://github.com/user-attachments/assets/2d0b5607-e3e0-456a-afdf-afda645e8790" />

*Question 3*

<img width="513" height="442" alt="image" src="https://github.com/user-attachments/assets/af4baa7d-1798-47ee-a571-56f7e61a563c" />


sql
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM 
    salesman AS s
INNER JOIN 
    customer AS c
ON 
    s.city = c.city;


*Output:*

<img width="790" height="507" alt="image" src="https://github.com/user-attachments/assets/b57a307a-312a-4205-8d1b-31e34747dcb1" />


*Question 4*

<img width="806" height="390" alt="image" src="https://github.com/user-attachments/assets/21169a62-781f-41f3-b78d-98730080691d" />

sql
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c
ON 
    s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';


*Output:*

<img width="380" height="490" alt="image" src="https://github.com/user-attachments/assets/3eb5b1fd-69b8-475c-b69f-fbd6042a1bd4" />

*Question 5*

<img width="808" height="368" alt="image" src="https://github.com/user-attachments/assets/02c1753d-1239-4de8-a4cd-6106589c2dc7" />

sql
SELECT 
    p.first_name AS patient_name, 
    d.first_name AS doctor_name
FROM 
    patients AS p
INNER JOIN 
    doctors AS d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.date_of_birth > '1990-01-01';


*Output:*

<img width="677" height="429" alt="image" src="https://github.com/user-attachments/assets/bb55a619-d4c2-445a-80ee-1a02f1d6f048" />

*Question 6*

<img width="801" height="414" alt="image" src="https://github.com/user-attachments/assets/e1fbac84-c6a6-4cb1-97dc-a9e36a73c9f1" />


sql
SELECT 
    c.cust_name, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt
FROM 
    customer AS c
LEFT JOIN 
    orders AS o
ON 
    c.customer_id = o.customer_id
WHERE 
    o.purch_amt > 1000;


*Output:*

<img width="800" height="454" alt="image" src="https://github.com/user-attachments/assets/5b397d9f-9402-427c-ba50-8ac387d3edd7" />


*Question 7*

<img width="800" height="435" alt="image" src="https://github.com/user-attachments/assets/31614e98-1b84-4f75-95c0-7190f0a2cfac" />

sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    o.ord_date > '2012-08-17';


*Output:*

<img width="803" height="470" alt="image" src="https://github.com/user-attachments/assets/2d227427-2530-4c09-9164-6670b04d9907" />


*Question 8*

<img width="809" height="297" alt="image" src="https://github.com/user-attachments/assets/3aef2e6a-ae97-4772-bc72-c0a453f8e8ce" />


sql
SELECT 
    p.date_of_birth, 
    a.*
FROM 
    patients AS p
INNER JOIN 
    appointments AS a
ON 
    p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';


*Output:*

<img width="805" height="244" alt="image" src="https://github.com/user-attachments/assets/e961ec9c-317d-4239-84dd-e62ec06f2c1b" />


*Question 9*

<img width="810" height="305" alt="image" src="https://github.com/user-attachments/assets/4e7ea5b1-a0f8-4a27-9834-3b4879b3426d" />


sql
SELECT p.*
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'X-Ray' AND t.result = 'Normal';


*Output:*

<img width="807" height="241" alt="image" src="https://github.com/user-attachments/assets/ad642d38-becf-42b9-9153-3de643b72803" />

*Question 10*

<img width="802" height="314" alt="image" src="https://github.com/user-attachments/assets/113bb238-63f6-4b6b-8c06-18737715e5f4" />


sql
SELECT 
    patients.first_name AS patient_name,
    doctors.first_name AS doctor_name
FROM 
    patients
INNER JOIN 
    doctors ON patients.doctor_id = doctors.doctor_id
WHERE 
    patients.discharge_date IS NULL;


*Output:*

<img width="586" height="440" alt="image" src="https://github.com/user-attachments/assets/dbee8b69-eb3c-4187-990a-b68d7a85d3ef" />


## Grade:
<img width="695" height="28" alt="image" src="https://github.com/user-attachments/assets/2e2a97b2-081e-44a7-9a1c-971fcf003a91" />

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

*Types:*
- *Single-row subquery*:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- *Multiple-row subquery*:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- *Correlated subquery*:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

*Example:*
sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

### Views
A view is a virtual table based on the result of an SQL SELECT query.
*Create View:*
sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;

*Drop View:*
sql
DROP VIEW view_name;


*Question 1*

<img width="753" height="399" alt="image" src="https://github.com/user-attachments/assets/d96e841e-3dee-42f5-b13b-a0ccfe11c614" />


sql
SELECT 
medication_id AS medic,
medication_name,
dosage
FROM Medications
WHERE CAST(REPLACE(dosage,'mg','') AS INTEGER)=(SELECT MAX(CAST(REPLACE(dosage,'mg','') AS INTEGER))
FROM Medications);


*Output:*

<img width="776" height="402" alt="image" src="https://github.com/user-attachments/assets/ecfa3806-a5c2-4be2-abd5-54f16db2c1b6" />

*Question 2*

<img width="798" height="414" alt="image" src="https://github.com/user-attachments/assets/3eca9eb1-bbf1-4ba9-a6cb-6827ebd4d23b" />


sql
SELECT
o.ord_no,
o.purch_amt,
o.ord_date,
o.customer_id,
o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id=s.salesman_id
WHERE s.city='New York';


*Output:*

<img width="799" height="330" alt="image" src="https://github.com/user-attachments/assets/4b291a3b-35d0-4d16-81f2-afd6fd0225a7" />


*Question 3*

<img width="807" height="366" alt="image" src="https://github.com/user-attachments/assets/e7868803-c5a5-4d8a-a031-95a7971be471" />

sql
SELECT student_name,grade
FROM GRADES
WHERE grade IN(SELECT MIN(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);


*Output:*

<img width="683" height="459" alt="image" src="https://github.com/user-attachments/assets/b0707a3a-777c-42d8-9d2d-b156cebe4926" />


*Question 4*

<img width="800" height="407" alt="image" src="https://github.com/user-attachments/assets/80845ae1-5189-4bb8-b3dc-24fd27319189" />


sql
SELECT *
FROM customer
WHERE city <>(
SELECT
city
FROM customer
WHERE id=(SELECT MAX(id) FROM customer));


*Output:*

<img width="804" height="327" alt="image" src="https://github.com/user-attachments/assets/a9662e03-25f7-410c-8301-33a8d0611a2e" />


*Question 5*

<img width="794" height="408" alt="image" src="https://github.com/user-attachments/assets/1fec29fe-8c65-4ee4-b89c-5dc80bcf51f6" />


sql
SELECT 
name
FROM customer
WHERE phone IN(
SELECT phone
FROM customer
GROUP BY phone
HAVING COUNT(*)=1)


*Output:*
<img width="391" height="483" alt="image" src="https://github.com/user-attachments/assets/7a8611b6-9221-470b-97d2-f977e1fdf4de" />


*Question 6*

<img width="804" height="396" alt="image" src="https://github.com/user-attachments/assets/474eed34-beb3-43c8-8f1b-f1ea2e4cf269" />

sql
SELECT *
FROM GRADES
WHERE grade IN(SELECT MAX(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);


*Output:*

<img width="798" height="280" alt="image" src="https://github.com/user-attachments/assets/861b03d4-8552-4f39-8615-82c84d848807" />


*Question 7*

<img width="801" height="465" alt="image" src="https://github.com/user-attachments/assets/82431dd1-7941-41bd-8838-e2d49ec28497" />


sql
SELECT
o.ord_no,
o.purch_amt,
o.ord_date,
o.customer_id,
o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id=s.salesman_id
WHERE s.city='New York';


*Output:*

<img width="799" height="346" alt="image" src="https://github.com/user-attachments/assets/7697ffbd-77b9-48f4-8b06-8ac18020c7ee" />


*Question 8*

<img width="808" height="387" alt="image" src="https://github.com/user-attachments/assets/ac97cf81-e62a-49c1-8e49-041304e8db48" />

sql
SELECT *
FROM GRADES
WHERE grade IN(SELECT MIN(grade) FROM GRADES AS g WHERE g.subject=GRADES.subject);


*Output:*

<img width="801" height="292" alt="image" src="https://github.com/user-attachments/assets/c7190031-d313-437a-9ad6-f3188d120636" />

*Question 9*

<img width="796" height="304" alt="image" src="https://github.com/user-attachments/assets/8c9defb7-edbc-44b9-8355-457e7152377d" />

sql
SELECT * 
FROM Orders
WHERE salesman_id IN(
SELECT
salesman_id
FROM Orders
WHERE customer_id='3007');


*Output:*

<img width="795" height="313" alt="image" src="https://github.com/user-attachments/assets/dca2dd74-7e1c-4b08-a838-8b71d8b296d4" />

*Question 10*

<img width="807" height="472" alt="image" src="https://github.com/user-attachments/assets/ae64836d-12a4-4d78-92f1-f46503f0e5d7" />


sql
SELECT *
FROM Employee
WHERE age<(SELECT AVG(age) FROM Employee WHERE income>250000);


*Output:*

<img width="803" height="328" alt="image" src="https://github.com/user-attachments/assets/2391d5c4-34f1-4079-addc-2b7a389d9882" />

## Grade:
<img width="686" height="31" alt="image" src="https://github.com/user-attachments/assets/9a373985-b2a7-4d35-b472-4553ff6777e8" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

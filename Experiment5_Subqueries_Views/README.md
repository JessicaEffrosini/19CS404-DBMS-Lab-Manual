# Experiment 5: Subqueries and Views



## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```
## Question 1
From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count.
```
SELECT grade, COUNT(*) 
FROM customer
WHERE grade > (
    SELECT AVG(grade)
    FROM customer
    WHERE city = 'New York'
)
GROUP BY grade;
```

## Output
![Screenshot 2025-05-12 190916](https://github.com/user-attachments/assets/ab421b77-c81c-4794-88ba-8437b0f95716)

## Question 2
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

```
SELECT * 
FROM CUSTOMERS
WHERE SALARY < 2500;
```
## Output
![Screenshot 2025-05-12 191104](https://github.com/user-attachments/assets/92fee322-12f6-417c-a608-61157a58b9f0)

## Question 3
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table
```
SELECT ord_no, purch_amt, ord_date, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM salesman
    WHERE commission = (
        SELECT MAX(commission)
        FROM salesman
    )
);
```
## Output
![Screenshot 2025-05-12 191237](https://github.com/user-attachments/assets/4ae0979c-f355-4e25-a71c-be064e8062fd)

## Question 4
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

Employee Table
```
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 1000000
);
```
## Output
![Screenshot 2025-05-12 191358](https://github.com/user-attachments/assets/65dd5aa5-9edd-45d8-8850-6da422e359f3)

## Question 5
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS
```
SELECT * 
FROM CUSTOMERS
WHERE AGE < 30;
```
## Output
![Screenshot 2025-05-12 191600](https://github.com/user-attachments/assets/aa902554-e3ef-47ed-9cdd-1b2097b63621)

## Question 6
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)
```
SELECT student_name, grade
FROM GRADES
WHERE (subject, grade) IN (
    SELECT subject, MIN(grade)
    FROM GRADES
    GROUP BY subject
);
```
## Output
![Screenshot 2025-05-12 191744](https://github.com/user-attachments/assets/2186585a-bf6a-453a-be8f-57590216ee2d)

## Question 7
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

Sample table: CUSTOMERS
```
SELECT * 
FROM CUSTOMERS
WHERE SALARY > 1500;
```
## Output
![image](https://github.com/user-attachments/assets/125d7f6b-7b73-4821-9d31-01e44991ac47)

## Question 8
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)
```
select *
from Medications
where dosage=(select max(dosage) from medications);
```
## Output
![Screenshot 2025-05-12 192711](https://github.com/user-attachments/assets/baf003d5-f186-4d9f-9e74-e343200fec95)

## Question 9
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS
```
select * 
from customers
where salary >4500;
```
## Output
![image](https://github.com/user-attachments/assets/5d2f1d94-986b-4ba8-92c8-6a4a6a65b6e8)

## Question 10
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)
```
select *
from GRADES t1
where grade=(select max(grade) from GRADES t2
where t2.subject=t1.subject);
```
## Output
![image](https://github.com/user-attachments/assets/23037c8e-2ed1-4165-b5f7-9bf482dd1594)

## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

# Experiment 6: Joins


## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

## Question 1
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer
```
SELECT
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM
    customer c
JOIN
    salesman s ON c.salesman_id = s.salesman_id
ORDER BY
    c.customer_id ASC;
```
## Output
![image](https://github.com/user-attachments/assets/c2d6c9cf-5b9a-4ea5-b6f0-38cdfb9a0569)

## Question 2
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-02-01' and '2024-02-28'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id
```SELECT
    p.*
FROM
    patients p
INNER JOIN
    appointments a ON p.patient_id = a.patient_id
WHERE
    a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28';
```
## Output
![Screenshot 2025-05-12 210707](https://github.com/user-attachments/assets/2b79f4fa-0793-44e6-9d72-4ceef46d7ee1)

## Question 3
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount greater than 1000.
```
SELECT
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM
    customer c
LEFT JOIN
    orders o ON c.customer_id = o.customer_id
WHERE
    o.purch_amt > 1000;
```
## Output
![image](https://github.com/user-attachments/assets/aee84ce0-ee23-4dcb-932b-c5dd5f580cc0)

## Question 4
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman
```
SELECT
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM
    salesman s
JOIN
    customer c ON s.city = c.city;
```
## Output
![Screenshot 2025-05-12 211228](https://github.com/user-attachments/assets/658802da-22f0-46b9-b523-514e1da4bb64)

## Question 5
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a null discharge date.
```
SELECT
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM
    patients p
INNER JOIN
    doctors d ON p.doctor_id = d.doctor_id
WHERE
    p.discharge_date IS NULL;
```
## Output
![Screenshot 2025-05-12 211359](https://github.com/user-attachments/assets/7aabc971-bb97-4d09-bbc2-ac0ec50b24dc)

## Question 6
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

Sample table: customer
```
SELECT
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS Salesman,
    s.commission
FROM
    customer c
JOIN
    salesman s ON c.salesman_id = s.salesman_id;
```
## Output
![image](https://github.com/user-attachments/assets/7db4163a-ebf0-4ded-bc2f-8952c5e43467)

## Question 7
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.
```
SELECT
    p.*,
    d.specialization AS doctor_specialization
FROM
    patients p
INNER JOIN
    doctors d ON p.doctor_id = d.doctor_id;
```
## Output
![Screenshot 2025-05-12 211838](https://github.com/user-attachments/assets/a8dbc8b4-0c79-496b-9aaf-7f8d6ade6be3)

## Question 8
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.
```
SELECT
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM
    customer c
LEFT JOIN
    orders o ON c.customer_id = o.customer_id;
```
## Output
![Screenshot 2025-05-12 212023](https://github.com/user-attachments/assets/9f9a760d-780a-42d1-bbf1-93a7af746d69)

## Question 9
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.
```
SELECT
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM
    orders o
JOIN
    customer c ON o.customer_id = c.customer_id
WHERE
    o.purch_amt BETWEEN 500 AND 2000;
```
## Output
![Screenshot 2025-05-12 212238](https://github.com/user-attachments/assets/153dc430-81f1-40ea-9e2c-e6819cf8b890)

## Question 10
Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.
```
SELECT 
    n.nurse_id,
    d.department_name
FROM 
    nurses n
INNER JOIN 
    departments d ON n.department_id = d.department_id
WHERE 
    n.first_name = 'David'
    AND n.last_name = 'Moore';
```
## Output
![Screenshot 2025-05-12 212522](https://github.com/user-attachments/assets/e1b10b91-6842-4849-b401-495403b6bca0)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

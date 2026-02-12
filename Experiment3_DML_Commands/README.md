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
--
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT           
For example:

Test	Result
select changes();
changes()
----------
4


```sql
UPDATE products
SET sell_price=sell_price*1.15
WHERE quantity<50 AND supplier_id=10;
```

**Output:**

<img width="1915" height="1102" alt="image" src="https://github.com/user-attachments/assets/3b90c802-c4b0-468c-bbf1-181ac042850b" />


**Question 2**
---
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
For example:

Test	Result
SELECT EMPLOYEE_ID, FIRST_NAME, HIRE_DATE FROM EMPLOYEES 
WHERE DEPARTMENT_ID=50 LIMIT 3;
EMPLOYEE_ID  FIRST_NAME  HIRE_DATE
-----------  ----------  ----------
120          Matthew     2024-01-24
121          Adam        2024-01-24
122          Payam       2024-01-24


```sql
UPDATE Employees
SET hire_date='2024-01-24'
WHERE department_id=50;
```

**Output:**

<img width="1919" height="1034" alt="image" src="https://github.com/user-attachments/assets/4b84da3c-5b11-4fa1-83c5-0a056fee25c6" />


**Question 3**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE products
SET sell_price=sell_price*1.10
WHERE category='Bakery';
```

**Output:**
 <img width="1917" height="1038" alt="image" src="https://github.com/user-attachments/assets/871e2029-73b2-4edb-9f16-85cd5bc49a70" />


**Question 4**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE products
SET product_name='Premium Bread'
WHERE product_id=5;
```

**Output:**

<img width="1917" height="1035" alt="image" src="https://github.com/user-attachments/assets/5a00feb6-7363-4aab-871e-c0c6a82e858f" />


**Question 5**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select distinct(grade)from customer;
GRADE
----------
2
3
1
0
GRADE
----------
1
0


```sql
DELETE FROM customer 
WHERE grade>=2
```

**Output:**

<img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/4995037c-fb47-49ec-bd03-9ad23b3f86a7" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select distinct(grade)from customer;
GRADE
----------
2
3
1
0
GRADE
----------
3
1
0


```sql
DELETE FROM customer
WHERE GRADE =2;
```

**Output:**

<img width="1912" height="1037" alt="image" src="https://github.com/user-attachments/assets/d5f740f8-0cd5-4b86-86f8-4fed462f4a42" />


**Question 7**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin       Jones
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics


```sql
DELETE FROM Doctors
WHERE specialization is NULL
```

**Output:**

<img width="1919" height="1032" alt="image" src="https://github.com/user-attachments/assets/86445e95-cecb-483c-b027-22a814d7f467" />


**Question 8**
---
 Write a query to fetch details of all employees excluding the employees with first names, “Sanjay” and “Sonia” from the EmployeeInfo table.
EmpID

EmpFname

EmpLname

Department

Project

Address

DOB

Gender

1

Sanjay

Mehra

HR

P1

Hyderabad(HYD)

01/12/1976

M

2

Ananya

Mishra

Admin

P2

Delhi(DEL)

02/05/1968

F



For example:

Result
EmpID       EmpFname    EmpLname    Department  Project     Address     DOB         Gender
----------  ----------  ----------  ----------  ----------  ----------  ----------  ----------
2           Ananya      Mishra      Admin       P2          Delhi(DEL)  1968-05-02  F
3           Rohan       Diwan       Account     P3          Mumbai(BOM  1980-01-01  M
5           Ankit       Kapoor      Admin       P2          Delhi(DEL)  1994-07-03  M


```sql
SELECT * FROM EmployeeInfo
WHERE EmpFname NOT IN ('Sanjay','Sonia');
```

**Output:**
<img width="1919" height="1032" alt="image" src="https://github.com/user-attachments/assets/d33c9838-ebe0-4ac9-9503-4a2f9b7cb7fa" />


**Question 9**
---
Write a query to fetch the number of employees working in the department ‘HR’.

EmployeeInfo

EmpID

EmpFname

EmpLname

Department

Project

Address

DOB

Gender

1

Sanjay

Mehra

HR

P1

Hyderabad(HYD)

01/12/1976

M

2

Ananya

Mishra

Admin

P2

Delhi(DEL)

02/05/1968

F

 

For example:

Result
COUNT(*)
----------
2


```sql
SELECT COUNT(*) FROM EmployeeInfo
WHERE Department='HR';
```

**Output:**

<img width="1919" height="1036" alt="image" src="https://github.com/user-attachments/assets/4c9dbc00-9243-463a-b6f5-28890351fd75" />


**Question 10**
---
Write a SQL query to evaluate the status of rows in the Calculations table based on whether value1 is positive, negative, or zero.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
 

For example:

Result
id          value1      value_status
----------  ----------  ------------
1           -87.65      Negative
2           45.78       Positive
3           89.99       Positive
4           -0.005      Negative


```sql
SELECT id,value1,
CASE WHEN value1>0 THEN 'Positive'
     WHEN value1<0 THEN 'Negative'
     ELSE 'Zero'
END AS value_status
FROM calculations;
```

**Output:**

<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/07f2e518-5d5b-4635-bf4a-7119501bfa0c" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

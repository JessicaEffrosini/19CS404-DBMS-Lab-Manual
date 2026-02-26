<img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/22207c8b-0a7f-4b27-ace3-4ae4728bed8d" /># Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many patients have expired insurance coverage for each insurance company?

Sample table:Insurance Table



For example:

Result
InsuranceCompany  TotalExpiredPatients
----------------  --------------------
ABC Insurance     1
DEF Insurance     1
GHI Insurance     1
JKL Insurance     1
MNO Insurance     1
PQR Insurance     1
STU Insurance     1
VWX Insurance     1
XYZ Insurance     1
YZA Insurance     1


```sql
SELECT InsuranceCompany,
COUNT(*) AS TotalExpiredPatients
FROM Insurance
GROUP BY InsuranceCompany
```

**Output:**

<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/99be22ca-f7f1-440c-95fe-89fc7ed8eeb6" />


**Question 2**
---
Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table



For example:

Result
PatientID   AvgMedications
----------  --------------
4           5
6           1
7           1
8           3


```sql
SELECT PatientID,
COUNT(Medications) AS AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

<img width="1919" height="1026" alt="image" src="https://github.com/user-attachments/assets/abf7bd9d-6781-440e-b67c-f29c4eb155d4" />


**Question 3**
---
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table



For example:

Result
Frequency      TotalPrescriptions
-------------  ------------------
Every 3 weeks  1
Every 6 hours  1
Once           1
Once daily     4
Once daily at  1
Pending        1
Twice daily    1


```sql
SELECT Frequency,
COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Frequency
```

**Output:**

<img width="1919" height="1029" alt="image" src="https://github.com/user-attachments/assets/35f9aa6a-2519-4cd7-b585-c2214b8fc014" />


**Question 4**
---
Write a SQL query to find the youngest employee in the company?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 

For example:

Result
Employee_Name  Age
-------------  ----------
Peter          32


```sql
SELECT name AS Employee_Name,
MIN(Age) AS Age
FROM employee
ORDER BY Age DESC
LIMIT 1;
```

**Output:**

<img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/55596693-3e45-41c8-9973-77ba7d39eae3" />


**Question 5**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

 

For example:

Result
COUNT
----------
8


```sql
SELECT COUNT(*) AS COUNT
FROM customer
```

**Output:**

<img width="1918" height="1033" alt="image" src="https://github.com/user-attachments/assets/51a540fc-71de-44fc-a7dd-242cf8ce260a" />


**Question 6**
---
Write a SQL query to calculate the total number of working hours of all employees

Sample table: employee1


 

For example:

Result
Total working hours
-------------------
111


```sql
SELECT SUM(workhour) AS "Total working hours"
FROM employee1
```

**Output:**

<img width="1919" height="1033" alt="image" src="https://github.com/user-attachments/assets/19b11648-5ce4-4202-b967-1cbc2a91a25d" />


**Question 7**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

For example:

Result
TOTAL
----------
17541.18


```sql
SELECT SUM(purch_amt) AS TOTAL
FROM orders
```

**Output:**

<img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/21149502-1d7d-4593-993e-69e875f39124" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

Sample table: customer1



For example:

Result
age_group   SUM(salary)
----------  -----------
20          16500
25          16500


```sql
SELECT (age/5)*5 AS age_group,SUM(salary)
FROM customer1

GROUP BY age_group
HAVING SUM(salary) > 5000;


```

**Output:**

<img width="1918" height="1032" alt="image" src="https://github.com/user-attachments/assets/8a48fe37-3c98-43f5-815a-d434b16dba31" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1



For example:

Result
jdate       SUM(workhour)
----------  -------------
2004.0      46
2006.0      46


```sql
SELECT ROUND(jdate,1) AS jdate,SUM(workhour)
FROM employee1
GROUP BY jdate
HAVING SUM(workhour)>40;
```

**Output:**
<img width="1919" height="1029" alt="image" src="https://github.com/user-attachments/assets/97efc400-0f1d-427b-87be-07a8a2e59475" />


**Question 10**
---
Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.

Sample table: customer1



For example:

Result
address     AVG(salary)
----------  -----------
Bhopal      8500.0
Indore      10000.0
Mumbai      6500.0


```sql
SELECT address,AVG(salary)
FROM customer1
GROUP BY address
HAVING AVG(salary) > 5000;
```

**Output:**

<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/4c4ce1d3-b973-4314-96a5-c2917b46224b" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

For example:

Test	Result
select * from Books;
ISBN            Title           Author              Publisher      YearPublished
--------------  --------------  ------------------  -------------  -------------
978-1234567890  The Lost World  Arthur Conan Doyle  Vintage Books  1912
978-0987654321  Gone with the   Margaret Mitchell   Macmillan      1936
978-1122334455  Moby Dick       Herman Melville     Harper & Brot  1851

```sql
INSERT INTO books(ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM Out_of_print_books;

```

**Output:**

<img width="1245" height="950" alt="image" src="https://github.com/user-attachments/assets/801ff1ae-ac7b-4189-9bcc-78d0e2a74c6c" />


**Question 2**
---
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
For example:

Test	Result
pragma table_info('Student_details');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      int         0                       1
1           Name        VARCHAR(10  1                       0
2           Gender      TEXT        1                       0
3           Subject     VARCHAR(30  0                       0
4           MARKS       INT (3)     0                       0
5           mobilenumb  number      0                       0

```sql
ALTER TABLE Student_details ADD mobilenumb number;
```

**Output:**

<img width="1245" height="961" alt="image" src="https://github.com/user-attachments/assets/c122d551-95ce-4d21-9276-ba3af4755069" />


**Question 3**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
For example:

Test	Result
INSERT INTO Shipments (ShipmentID, ShipmentDate, SupplierID, OrderID) VALUES (2, '2024-08-03', 99, 1);
Error: FOREIGN KEY constraint failed


```sql
CREATE TABLE Shipments (
ShipmentID INTEGER,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
PRIMARY KEY(ShipmentID)
);
```

**Output:**

<img width="1237" height="932" alt="image" src="https://github.com/user-attachments/assets/a1f20c6c-8aec-4533-b294-6d78a37cc589" />


**Question 4**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0
For example:

Test	Result
INSERT INTO products (product_id, product_name, list_price) VALUES (2, 'Product B', 50.00);
SELECT * FROM products;
product_id  product_name  list_price  discount
----------  ------------  ----------  ----------
2           Product B     50          0

```sql
CREATE TABLE products(
product_id INTEGER PRIMARY KEY,
product_name TEXT NOT NULL,
list_price DECIMAL(10,2) NOT NULL,
discount DECIMAL(10,2) NOT NULL DEFAULT 0,
CHECK (list_price >= discount AND discount >=0 AND list_price >= 0)
);
```

**Output:**

<img width="1230" height="960" alt="image" src="https://github.com/user-attachments/assets/aa6bc9f6-b931-412e-95b9-9505bb4fb94c" />


**Question 5**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.
For example:

Test	Result
INSERT INTO Bonuses (BonusID, EmployeeID, BonusAmount, BonusDate, Reason) VALUES (1, 6, 1000.0, '2024-08-01', 'Outstanding performance');
SELECT * FROM Bonuses;
BonusID     EmployeeID  BonusAmount  BonusDate   Reason
----------  ----------  -----------  ----------  -----------------------
1           6           1000.0       2024-08-01  Outstanding performance


```sql
CREATE TABLE Bonuses(
BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
BonusAmount REAL CHECK (BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1235" height="958" alt="image" src="https://github.com/user-attachments/assets/46842d65-1f18-410d-be35-3aa4b91e1ef8" />


**Question 6**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).
For example:

Test	Result
INSERT INTO Customers (CustomerID, FirstName, LastName, Email) VALUES (1, 'Alice', 'Johnson', 'alice.johnson@example.com');
INSERT INTO Orders (OrderID, OrderDate, CustomerID) VALUES (1, '2024-08-01', 1);
select * from orders;
OrderID     OrderDate   CustomerID
----------  ----------  ----------
1           2024-08-01  1

```sql
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1241" height="964" alt="image" src="https://github.com/user-attachments/assets/bc88dbb7-762c-4f79-9ca0-94a8371fed8d" />


**Question 7**
---
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.
 
For example:

Test	Result
SELECT CustomerID, Name, Address
FROM Customers;
CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St


```sql
INSERT INTO Customers (CustomerID,Name,Address)
VALUES (304,'Peter Parker','Spider St');
```

**Output:**

<img width="1244" height="966" alt="image" src="https://github.com/user-attachments/assets/a48ceba3-b9fb-4088-aa66-08a3424f46ca" />


**Question 8**
---
Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

 

 

For example:

Test	Result
pragma table_info('books');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           book_id     INT         0                       1
1           title       VARCHAR(15  0                       0
2           author      VARCHAR(10  0                       0
3           genre       VARCHAR(50  0                       0
4           publicatio  INT         0                       0
5           ISBN        varchar(30  0                       0
6           domain_dep  varchar(30  0                       0

```sql
ALTER TABLE books ADD ISBN varchar(30);
ALTER TABLE books ADD domain_dept varchar(30);
```

**Output:**

<img width="1239" height="966" alt="image" src="https://github.com/user-attachments/assets/e6880e4d-d6a2-4ba2-a356-1b1f7a3eccda" />


**Question 9**
---
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
For example:

Test	Result
SELECT Name, Category, Price, Stock FROM Products;

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300


```sql
INSERT INTO Products(Name, Category, Price, Stock )
VALUES ('Smartphone','Electronics',800,150);

INSERT INTO Products(Name, Category, Price, Stock )
VALUES ('Headphones','Accessories',200,300); 
```

**Output:**

<img width="1234" height="970" alt="image" src="https://github.com/user-attachments/assets/addfea87-23d9-4780-a6e4-9543b04260ce" />


**Question 10**
---
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME
For example:

Test	Result
pragma table_info('Customers');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           CustomerID  INTEGER     0                       0
1           Name        TEXT        0                       0
2           Email       TEXT        0                       0
3           JoinDate    DATETIME    0                       0


```sql
CREATE TABLE Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME
);
```

**Output:**

<img width="1239" height="965" alt="image" src="https://github.com/user-attachments/assets/05114b02-8e03-44c4-84df-a75e8c2daa20" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

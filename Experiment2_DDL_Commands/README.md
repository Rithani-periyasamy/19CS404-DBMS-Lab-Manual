
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

<img width="713" height="318" alt="image" src="https://github.com/user-attachments/assets/8436235d-4630-4049-bbb1-7c08c8a6e62f" />


**Question 2**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
For example:

Test	Result
-- Attempt to insert a record with NULL FirstName
INSERT INTO Employees (EmployeeID, FirstName, LastName, Email, Salary, DepartmentID)
VALUES (1, NULL, 'Doe', 'john.doe@example.com', 50000, 1);
Error: NOT NULL constraint failed: Employees.FirstName



```sql
CREATE TABLE Employees(
EmployeeID INTEGER PRIMARY KEY,
FirstName Varchar(50) NOT NULL,
LastName Varchar(50) NOT NULL,
Email TEXT UNIQUE,
Salary DECIMAL(10,2)CHECK(Salary>0),
DepartmentID TEXT,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);

```

**Output:**
<img width="546" height="290" alt="image" src="https://github.com/user-attachments/assets/b433fa36-627d-4010-8d10-d46ad3d085c8" />




**Question 3**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
For example:

Test	Result
INSERT INTO contacts (contact_id, first_name, last_name, email, phone) VALUES (1, 'John', 'Doe', 'john.doe@example.com', '1234567890');
SELECT * FROM contacts;


```sql
CREATE TABLE contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL CHECK(length(phone)>=10)
);

```

**Output:**
<img width="680" height="232" alt="image" src="https://github.com/user-attachments/assets/2d7be3a3-8042-474d-8d22-338d93aae955" />




**Question 4**
---
nsert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

For example:

Test	Result
SELECT * FROM Books;
ISBN            Title                    Author      Publisher   Year
--------------  -----------------------  ----------  ----------  ----------
978-1234567890  Data Science Essentials  Jane Doe    TechBooks   2024


```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
VALUES('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
-
```

**Output:**
<img width="665" height="87" alt="image" src="https://github.com/user-attachments/assets/b3d35445-86df-4c87-90c9-cb775f37be7a" />



**Question 5**
---
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

For example:

Test	Result
select * from Employee;
EmployeeID  Name        Department  Salary
----------  ----------  ----------  ----------
201         John Doe    HR          50000
202         Jane Smith  Engineerin  75000
203         Emily Davi  Marketing   60000



```sql
INSERT INTO Employee
select *from Former_employees;

```

**Output:**
<img width="432" height="157" alt="image" src="https://github.com/user-attachments/assets/d9efaa44-aed5-46e8-9e98-a4ecd76a0e00" />




**Question 6**
---
Write a SQL query to add a column named Date_of_birth as Date in the Student_details table.

For example:

Test	Result
pragma table_info('Student_details');
cid    name             type             notnu  dflt_value  pk
-----  ---------------  ---------------  -----  ----------  ----------
0      RollNo           int              0                  1
1      Name             VARCHAR(100)     1                  0
2      Gender           TEXT             1                  0
3      Subject          VARCHAR(30)      0                  0
4      MARKS            INT (3)          0                  0
5      Date_of_birth    Date             0                  0


```sql
ALTER TABLE Student_details
ADD Date_of_birth Date;

```

**Output:**

<img width="662" height="222" alt="image" src="https://github.com/user-attachments/assets/39e1199a-c859-4a58-b1be-9aa722cd4640" />



**Question 7**
---
Insert the following students into the Student_details table:
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
202            Ella King         F           Chemistry   87
203            James Bond   M          Literature    78

 

 

For example:

Test	Result
SELECT * FROM Student_details;
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
202         Ella King   F           Chemistry   87
203         James Bond  M           Literature  78



```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(202,'Ella King','F','Chemistry',87),
      (203,'James Bond','M','Literature',78);

```

**Output:**
<img width="526" height="115" alt="image" src="https://github.com/user-attachments/assets/b257b514-25fa-4f37-bd72-af5aabce44f4" />




**Question 8**
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
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY(SupplierID)REFERENCES Suppliers(SupplierID),
FOREIGN KEY(OrderID)REFERENCES Orders(Orderid)
);
```

**Output:**
<img width="337" height="97" alt="image" src="https://github.com/user-attachments/assets/2308ce02-af49-4888-99ac-749816123911" />




**Question 9**
---

Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

 

 

 

 

For example:

Test	Result
PRAGMA table_info(employee);
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          integer     0                       0
1           salary      number      0                       0
2           department  INTEGER     0                       0
3           manager_id  INTEGER     0           NULL        0




```sql
ALTER TABLE employee
ADD COLUMN department_id INTEGER;

ALTER TABLE employee
ADD COLUMN manager_id INTEGER DEFAULT
NULL;

```

**Output:**

<img width="673" height="183" alt="image" src="https://github.com/user-attachments/assets/6de703f7-4dad-4aaa-b77e-8db7803d7f41" />




**Question 10**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.
For example:

Test	Result
INSERT INTO Products (ProductID, ProductName, Price, StockQuantity) VALUES (1, 'Laptop', 999.99, 10);
select * from Products;
ProductID   ProductName  Price       StockQuantity
----------  -----------  ----------  -------------
1           Laptop       999.99      10



```sql
CREATE TABLE Products(
ProductID INTEGER PRIMARY KEY,
ProductName TEXT UNIQUE NOT NULL,
Price REAL CHECK(price>0),
StockQuantity INTEGER CHECK(StockQuantity>0)
);

```

**Output:**

<img width="502" height="147" alt="image" src="https://github.com/user-attachments/assets/efc9ecdb-37a8-4b07-baa0-3ee0141cb6f3" />




## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

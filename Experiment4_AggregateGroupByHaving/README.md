# Experiment 4: Aggregate Functions, Group By and Having Clause

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
--What is the average age of doctors in each medical specialty?

Sample table:Doctors Table



For example:

Result
Specialty          AvgAge
-----------------  ----------
Endocrinology      44.0
Gastroenterology   39.0
Neurology          41.0
Obstetrics         53.0
Pediatrics         48.0
Urology            44.0


```sql
SELECT Specialty, AVGAge AS AvgAge
FROM Doctors
GROUP BY Specialty;
```

**Output:**
<img width="265" height="210" alt="image" src="https://github.com/user-attachments/assets/33106d4b-4a1a-4e55-a354-35f640de4f09" />




**Question 2**
---
What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table



For example:

Result
PatientID   TotalMedications
----------  ----------------
1           1
2           1
3           1
4           1
5           1
6           1
7           1
8           1
9           1
10          1



```sql
SELECT PatientID, COUNT(*) AS TotalMedications
FROM Prescriptions
GROUP BY PatientID
ORDER BY PatientID;

```

**Output:**
<img width="266" height="717" alt="image" src="https://github.com/user-attachments/assets/1b362a6c-4e03-4893-aa22-f9c863744136" />




**Question 3**
---
What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table



For example:

Result
DoctorID    TotalAppointments
----------  -----------------
1           1
2           3
5           3
9           2
10          1



```sql
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;

```

**Output:**
<img width="272" height="502" alt="image" src="https://github.com/user-attachments/assets/9965e055-daa3-497f-b93f-38b6b8456679" />




**Question 4**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 

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
avg_income
----------
5000000.0


```sql
SELECT AVG(income) AS avg_income
FROM employee
WHERE name LIKE 'A%';

```

**Output:**
<img width="111" height="187" alt="image" src="https://github.com/user-attachments/assets/f2948e82-ceac-4020-85ed-360b83540505" />



**Question 5**
---
Write a SQL query to  find the average salary of all employees?

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
Average_Salary
--------------
1568750.0



```sql
SELECT AVG(income) AS Average_Salary
FROM employee;

```

**Output:**
<img width="160" height="167" alt="image" src="https://github.com/user-attachments/assets/b7130ea2-b0cb-4be0-a170-5ec8791e7fa0" />




**Question 6**
---
Write a SQL query to find the Fruit with the lowest available quantity.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

For example:

Result
fruit_name  lowest_quantity
----------  ---------------
Watermelon  15



```sql
SELECT name AS fruit_name, inventory AS lowest_quantity
FROM fruits
WHERE inventory = (SELECT MIN(inventory) FROM fruits);

```

**Output:**
<img width="265" height="267" alt="image" src="https://github.com/user-attachments/assets/d4011d69-fcd0-4e98-b2ee-b9bcd012a1ec" />




**Question 7**
---
Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
avg_email_length
----------------
15.0



```sql

SELECT AVG(LENGTH(email)) AS avg_email_length
FROM customer;
```

**Output:**
<img width="183" height="230" alt="image" src="https://github.com/user-attachments/assets/af4bfcd0-ee59-4256-8a44-9e242223f88c" />




**Question 8**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

Sample table: products



For example:

Result
category_id  Total_Cost
-----------  ----------
2            63



```sql
SELECT category_id, SUM(price) AS Total_Cost
FROM products
GROUP BY category_id
HAVING SUM(price) > 50;

```

**Output:**
<img width="210" height="216" alt="image" src="https://github.com/user-attachments/assets/9f857c0b-cdb4-4c01-837e-4330997fdc07" />




**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

Sample table: employee



For example:

Result
city        AVG(income)
----------  -----------
Arizona     1000000.0
California  2650000.0
Florida     2675000.0



```sql
SELECT city, AVG(income) AS "AVG(income)"
FROM employee
GROUP BY city
HAVING AVG(income) > 500000;

```

**Output:**
<img width="226" height="297" alt="image" src="https://github.com/user-attachments/assets/24980c23-360e-4f0c-81c4-84d3c62ba2be" />




**Question 10**
---
Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.

Sample table: products



For example:

Result
category_id  Price
-----------  ----------
3            7.5



```sql
SELECT category_id, MIN(price) AS Price
FROM products
GROUP BY category_id
HAVING MIN(price) < 10;

```

**Output:**
<img width="278" height="240" alt="image" src="https://github.com/user-attachments/assets/4d360345-a929-4407-89c1-c14da9bb5837" />





## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

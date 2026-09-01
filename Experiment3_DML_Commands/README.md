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
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

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
SELECT EMPLOYEE_ID,FIRST_NAME,EMAIL,COMMISSION_PCT FROM EMPLOYEES 
WHERE DEPARTMENT_ID=110 LIMIT 1;
EMPLOYEE_ID  FIRST_NAME  EMAIL          COMMISSION_PCT
-----------  ----------  -------------  --------------
205          Shelley     not available  0.55


```sql
UPDATE EMPLOYEES
SET EMAIL = 'not available',
    COMMISSION_PCT = 0.55
WHERE DEPARTMENT_ID = 110;

```

**Output:**
<img width="502" height="230" alt="image" src="https://github.com/user-attachments/assets/80949d4c-9779-49fa-ab08-ba5e5f2926fd" />




**Question 2**
--
Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

Customer table (customer_id,cust_name,city,grade,salesman_id)

```sql
UPDATE customer
SET grade = 5
WHERE city = 'Chennai';

```

**Output:**
<img width="555" height="315" alt="image" src="https://github.com/user-attachments/assets/d9399df4-98bf-49e2-8b49-db68e6a4bc5b" />




**Question 3**
---
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

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
SELECT EMPLOYEE_ID,FIRST_NAME,EMAIL FROM EMPLOYEES LIMIT 2;
EMPLOYEE_ID  FIRST_NAME  EMAIL
-----------  ----------  -----------
100          Steven      Unavailable
101          Neena       Unavailable



```sql
UPDATE employees
SET email='Unavailable';

```

**Output:**
<img width="362" height="302" alt="image" src="https://github.com/user-attachments/assets/b1ce1ef7-cd98-423c-90c8-cefe0eba10be" />




**Question 4**
---
Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
For example:

Test	Result
select changes();
changes()
----------
4



```sql

-UPDATE Products
SET sell_price = sell_price + (sell_price * 10 / 100)
WHERE supplier_id = 6;
```

**Output:**
<img width="945" height="397" alt="image" src="https://github.com/user-attachments/assets/6b60c54c-9400-4bba-806a-fceb2e5e4935" />




**Question 5**
---
Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability



```sql
UPDATE products
SET availability = availability*2
WHERE product_id=1;

```

**Output:**
<img width="491" height="90" alt="image" src="https://github.com/user-attachments/assets/f792eef8-e6e4-4a94-be6b-950b57a65f37" />





**Question 6**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
For example:

Test	Result
SELECT * FROM surgeries;
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28
3           3           3           2024-03-25
surgery_id  patient_id  surgeon_id  surgery_date
----------  ----------  ----------  ------------
1           1           1           2024-01-15
2           2           2           2024-02-28



```sql
DELETE FROM surgeries
WHERE surgery_id=3;

```

**Output:**
<img width="438" height="248" alt="image" src="https://github.com/user-attachments/assets/e1691cfe-182d-4b74-a1b9-4e43adf61b6f" />




**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

 
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
2
3


```sql
DELETE FROM Customer
WHERE GRADE<2;


```

**Output:**
<img width="197" height="432" alt="image" src="https://github.com/user-attachments/assets/10d5da90-13f5-4d8c-9086-f8b7bc68533b" />




**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00001      Micheal     New York    New York      USA           2           3000         5000         2000         6000             CCCCCCC     A008
C00020      Albert      New York    New York      USA           3           5000         7000         6000         6000             BBBBSBB     A008
C00002      Bolt        New York    New York      USA           3           5000         7000         9000         3000             DDNRDRH     A008
changes()
----------
3

```sql
DELETE FROM Customer
WHERE WORKING_AREA = 'New York';

```

**Output:**
<img width="1102" height="610" alt="image" src="https://github.com/user-attachments/assets/b56ba0e6-833d-4e02-8373-b3870d1327da" />
<img width="1092" height="587" alt="image" src="https://github.com/user-attachments/assets/f126de82-54cd-4790-8912-5f0fcf47e997" />




**Question 9**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
SELECT * FROM customer WHERE cust_country='India';
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00025      Ravindran   Bangalore   Bangalore     India         2           5000         7000         4000         8000             AVAVAVA     A011
C00019      Yearannaid  Chennai     Chennai       India         1           8000         7000         7000         8000             ZZZZBFV     A010
C00005      Sasikant    Mumbai      Mumbai        India         1           7000         11000        7000         11000            147-258963  A002
C00007      Ramanathan  Chennai     Chennai       India         1           7000         11000        9000         9000             GHRDWSD     A010
C00022      Avinash     Mumbai      Mumbai        India         2           7000         11000        9000         9000             113-123456  A002
C00017      Srinivas    Bangalore   Bangalore     India         2           8000         4000         3000         9000             AAAAAAB     A007
C00009      Ramesh      Mumbai      Mumbai        India         3           8000         7000         3000         12000            Phone No    A002
C00014      Rangarappa  Bangalore   Bangalore     India         2           8000         11000        7000         12000            AAAATGF     A001
C00016      Venkatpati  Bangalore   Bangalore     India         2           8000         11000        7000         12000            JRTVFDD     A007
C00011      Sundariya   Chennai     Chennai       India         3           7000         11000        7000         11000            PPHGRTS     A010
CUST_CODE   CUST_NAME    CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  -----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00019      Yearannaidu  Chennai     Chennai       India         1           8000         7000         7000         8000             ZZZZBFV     A010
C00007      Ramanathan   Chennai     Chennai       India         1           7000         11000        9000         9000             GHRDWSD     A010
C00011      Sundariya    Chennai     Chennai       India         3           7000         11000        7000         11000            PPHGRTS     A010




```sql
DELETE FROM customer
WHERE cust_country = 'India'
  AND cust_city <> 'Chennai';
-
```

**Output:**
<img width="430" height="345" alt="image" src="https://github.com/user-attachments/assets/ba4633e6-8cfd-494c-a0d2-b350f0623a19" />








**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
SELECT * FROM customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;
CUST_CODE   CUST_NAME   CUST_CITY   WORKING_AREA  CUST_COUNTRY  GRADE       OPENING_AMT  RECEIVE_AMT  PAYMENT_AMT  OUTSTANDING_AMT  PHONE_NO    AGENT_CODE
----------  ----------  ----------  ------------  ------------  ----------  -----------  -----------  -----------  ---------------  ----------  ----------
C00013      Holmes      London      London        UK            2           6000         5000         7000         4000             BBBBBBB     A003
C00020      Albert      New York    New York      USA           3           5000         7000         6000         6000             BBBBSBB     A008
C00025      Ravindran   Bangalore   Bangalore     India         2           5000         7000         4000         8000             AVAVAVA     A011
C00024      Cook        London      London        UK            2           4000         9000         7000         6000             FSDDSDF     A006
C00015      Stuart      London      London        UK            1           6000         8000         3000         11000            GFSGERS     A003
C00002      Bolt        New York    New York      USA           3           5000         7000         9000         3000             DDNRDRH     A008
C00004      Winston     Brisban     Brisban       Australia     1           5000         8000         7000         6000             AAAAAAA     A005
C00023      Karl        London      London        UK            0           4000         6000         7000         3000             AAAABAA     A006
C00010      Charles     Hampshair   Hampshair     UK            3           6000         4000         5000         5000             MMMMMMM     A009
C00012      Steven      San Jose    San Jose      USA           1           5000         7000         9000         3000             KRFYGJK     A012



```sql
DELETE FROM customer
WHERE opening_amt BETWEEN 4000 AND 6000;

```

**Output:**
<img width="680" height="452" alt="image" src="https://github.com/user-attachments/assets/779613cf-b750-4faf-9597-3b1ed6e108b5" />



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

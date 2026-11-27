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
--
-- Paste Question 1 here

<img width="811" height="670" alt="image" src="https://github.com/user-attachments/assets/59efd7a7-33e3-494e-b0cd-c583669d55d5" />

```sql
SELECT 
  DATE(AppointmentDateTime) AS AppointmentDate,
  COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime)
ORDER BY AppointmentDate;
```

**Output:**

<img width="856" height="764" alt="image" src="https://github.com/user-attachments/assets/afa7396f-72f8-41b3-b1f6-457a0f33ef95" />


**Question 2**
---
<img width="702" height="635" alt="image" src="https://github.com/user-attachments/assets/381e60a8-42e5-4804-9bcb-86648dc4f39e" />


```sql
SELECT
   strftime('%H',AppointmentDateTime) AS HourOfDay,
   COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY HourOfDay
ORDER BY HourOfDay;
```

**Output:**

<img width="727" height="619" alt="image" src="https://github.com/user-attachments/assets/139a1a98-05bd-4b67-9173-68d9c9b3850a" />


**Question 3**
---
<img width="887" height="469" alt="image" src="https://github.com/user-attachments/assets/1b5112b2-ca06-4823-857e-0e17928129af" />


```sql
SELECT AVG(LENGTH(name)) AS avg_name_length
FROM customer
WHERE city = 'Chennai';
```

**Output:**

<img width="497" height="397" alt="image" src="https://github.com/user-attachments/assets/4f30a533-1f40-4d4c-b6de-0f0793762be5" />


**Question 4**
---
<img width="758" height="553" alt="image" src="https://github.com/user-attachments/assets/95b4704f-eecf-4fcf-9f07-9aeace61e873" />


```sql
SELECT name as Employee_Name , age AS Age
FROM employee
ORDER BY age ASC
LIMIT 1;
```

**Output:**




**Question 5**
---



```sql
SELECT MIN(purch_amt) AS MINIMUM
FROM orders;
```

**Output:**

<img width="457" height="389" alt="image" src="https://github.com/user-attachments/assets/88ba5019-000a-4adf-8f15-603d05cd6523" />


**Question 6**

<img width="1237" height="510" alt="image" src="https://github.com/user-attachments/assets/1dbeff7d-0de4-41e1-832a-cad8714bf830" />


```sql
SELECT jdate , AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY jdate
HAVING AVG(workhour) < 10;
```

**Output:**

<img width="656" height="425" alt="image" src="https://github.com/user-attachments/assets/2e68541f-3628-463f-acc0-aa2dbeaafb62" />


**Question 7**
---
<img width="1205" height="521" alt="image" src="https://github.com/user-attachments/assets/179ee717-a0d1-4916-b2f9-dca082c6fca5" />


```sql
SELECT age , SUM(income) AS "SUM(income)"
FROM employee
GROUP BY age
HAVING SUM(income) > 1000000;
```

**Output:**

<img width="655" height="493" alt="image" src="https://github.com/user-attachments/assets/d9f1c391-5552-48cf-a947-133c2ed6b203" />


**Question 8**
---
<img width="1211" height="544" alt="image" src="https://github.com/user-attachments/assets/2329e0af-2af5-402b-a8d0-715c5b491d1f" />


```sql
SELECT age , MIN(income) AS "MIN(income)"
FROM employee
GROUP BY age
HAVING MIN(income)<400000;
```

**Output:**

<img width="686" height="524" alt="image" src="https://github.com/user-attachments/assets/8c58a604-3cd9-4eda-8314-508b7eda2484" />


**Question 9**
---
<img width="1085" height="634" alt="image" src="https://github.com/user-attachments/assets/4cdf1aea-a3fa-4a7e-8f73-45edb8414615" />


```sql
SELECT Specialty,COUNT(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty
ORDER BY Specialty;
```

**Output:**

<img width="830" height="727" alt="image" src="https://github.com/user-attachments/assets/4ddf54b0-6a46-41d8-9e44-a2ed1d833ec9" />


**Question 10**
<img width="853" height="689" alt="image" src="https://github.com/user-attachments/assets/cc06dbff-06c7-4695-95e1-3336270fe9b5" />


```sql
SELECT strftime('%H',AppointmentDateTime) AS HourOfDay,
    COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY HourOfDay
ORDER BY HourOfDay;
```

**Output:**

<img width="741" height="636" alt="image" src="https://github.com/user-attachments/assets/39f03090-eb95-420a-8113-883ee157fa39" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

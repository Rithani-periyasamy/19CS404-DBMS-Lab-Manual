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
<img width="705" height="632" alt="image" src="https://github.com/user-attachments/assets/234199c7-8225-4533-a6e9-5c95dedfeade" />


```sql
SELECT 
  DATE(AppointmentDateTime) AS AppointmentDate,
  COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime)
ORDER BY AppointmentDate;
```

**Output:**

<img width="960" height="607" alt="image" src="https://github.com/user-attachments/assets/c88e1b38-52b6-465a-919c-2d98087adf13" />


**Question 2**
---
<img width="711" height="612" alt="image" src="https://github.com/user-attachments/assets/295c1da5-7c10-42d0-910e-a3cbf22ea3cb" />


```sql
SELECT
   strftime('%H',AppointmentDateTime) AS HourOfDay,
   COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY HourOfDay
ORDER BY HourOfDay;
```

**Output:**

<img width="810" height="500" alt="image" src="https://github.com/user-attachments/assets/d1b6c637-a5a3-46ee-a6d9-442854f93475" />


**Question 3**
---
<img width="831" height="447" alt="image" src="https://github.com/user-attachments/assets/2ee00c86-b37f-473a-b7ce-75f3e19c5a49" />




```sql
SELECT AVG(LENGTH(name)) AS avg_name_length
FROM customer
WHERE city = 'Chennai';
```

**Output:**

<img width="505" height="287" alt="image" src="https://github.com/user-attachments/assets/3557de13-b747-4705-9f7c-dd53938931fd" />


**Question 4**
---
<img width="738" height="510" alt="image" src="https://github.com/user-attachments/assets/a5598160-3dd7-463f-a169-d0190677ab69" />


```sql
SELECT name as Employee_Name , age AS Age
FROM employee
ORDER BY age ASC
LIMIT 1;
```

**Output:**

<img width="702" height="322" alt="image" src="https://github.com/user-attachments/assets/3fe31ca4-4074-40a6-aad5-cfa2a9b291a8" />


**Question 5**
---
<img width="652" height="488" alt="image" src="https://github.com/user-attachments/assets/e1c446a5-3547-4627-8b08-6ff193432c7d" />


```sql
SELECT MIN(purch_amt) AS MINIMUM
FROM orders;
```

**Output:**
<img width="392" height="293" alt="image" src="https://github.com/user-attachments/assets/87395d93-4eb7-456b-aee6-3935fffdef9a" />


**Question 6**
---
<img width="1205" height="478" alt="image" src="https://github.com/user-attachments/assets/4b9697ab-bcfd-4574-a7ac-4e71e7023556" />


```sql
SELECT jdate , AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY jdate
HAVING AVG(workhour) < 10;
```

**Output:**

<img width="665" height="326" alt="image" src="https://github.com/user-attachments/assets/4968ef6b-3a69-406e-8a53-6c7f9c296102" />


**Question 7**
---
<img width="1197" height="480" alt="image" src="https://github.com/user-attachments/assets/da9d9467-4348-46cb-9ccf-bc19a126d0e4" />


```sql
SELECT age , SUM(income) AS "SUM(income)"
FROM employee
GROUP BY age
HAVING SUM(income) > 1000000;
```

**Output:**

<img width="657" height="425" alt="image" src="https://github.com/user-attachments/assets/d65cd5fd-d3c0-4d57-8fb2-62054c42628b" />


**Question 8**
---
<img width="1192" height="522" alt="image" src="https://github.com/user-attachments/assets/0fdd4a65-d206-481d-af9b-35d3281675cf" />


```sql
SELECT age , MIN(income) AS "MIN(income)"
FROM employee
GROUP BY age
HAVING MIN(income)<400000;
```

**Output:**

<img width="697" height="395" alt="image" src="https://github.com/user-attachments/assets/03ef03cd-e3e0-4a32-be6c-a23663da1547" />


**Question 9**
---
<img width="1077" height="577" alt="image" src="https://github.com/user-attachments/assets/127e9603-a135-48bb-91ef-58dc9628c961" />



```sql
SELECT Specialty,COUNT(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty
ORDER BY Specialty;
```

**Output:**
<img width="748" height="622" alt="image" src="https://github.com/user-attachments/assets/8b839cae-5d20-426e-a068-711372a87f96" />




**Question 10**
---
<img width="892" height="600" alt="image" src="https://github.com/user-attachments/assets/af95e1bf-ada0-438c-84d9-7144cb7067c4" />



```sql
SELECT strftime('%H',AppointmentDateTime) AS HourOfDay,
    COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY HourOfDay
ORDER BY HourOfDay;

```

**Output:**

<img width="842" height="526" alt="image" src="https://github.com/user-attachments/assets/c5217c5a-1b68-485a-8f00-6e30cecb6db5" />




## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

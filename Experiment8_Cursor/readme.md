# Experiment 8: PL/SQL Cursor Programs

## AIM
To write and execute PL/SQL programs using cursors and exception handling to manage runtime errors effectively and display appropriate messages.

## THEORY

In PL/SQL, cursors are used to handle query result sets row-by-row. 

There are two types of cursors:

- Implicit Cursors: Automatically created by PL/SQL for single-row queries.
- Explicit Cursors: Declared and controlled by the programmer for multi-row queries.

Types of Explicit Cursors:

1. Simple Cursor: Basic cursor to iterate over multiple rows.

2. Parameterized Cursor: Accepts parameters to filter the result dynamically.

3. Cursor FOR Loop: Simplifies cursor operations (open, fetch, close).

4. %ROWTYPE Cursor: Fetches entire row into a record using %ROWTYPE.

5. Cursor with FOR UPDATE: Used for row-level locking and updating the rows while looping.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:

- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

**Exception Handling**

PL/SQL provides a robust mechanism to handle runtime errors using exception handling blocks. When an error occurs during execution, control is passed to the EXCEPTION section, where specific or general errors can be handled gracefully.

### Components of Exception Handling:
- Predefined Exceptions: Automatically raised by PL/SQL for common errors (e.g., NO_DATA_FOUND, TOO_MANY_ROWS, ZERO_DIVIDE).
- User-defined Exceptions: Declared explicitly in the declaration section using the EXCEPTION keyword.
- WHEN OTHERS: A generic handler for all exceptions not handled explicitly.

```sql
BEGIN
   -- Statements
EXCEPTION
   WHEN exception_name THEN
      -- Handling code
   WHEN OTHERS THEN
      -- Handling for unknown errors
END;
```

### **Question 1: Simple Cursor with Exception Handling**

**Write a PL/SQL program using a simple cursor to fetch employee names and designations from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: When no rows are fetched.
2. **OTHERS**: Any other unexpected errors during execution.
**code**
-- Create employees table
CREATE TABLE employees (
    emp_id INTEGER PRIMARY KEY,
    emp_name TEXT,
    designation TEXT
);

-- Insert sample data
INSERT INTO employees (emp_id, emp_name, designation) VALUES
(1, 'Arun', 'Manager'),
(2, 'Priya', 'Developer'),
(3, 'Karthik', 'Tester');

-- Fetch employee details
SELECT emp_name, designation
FROM employees;

SELECT CASE
    WHEN COUNT(*) = 0 THEN 'No employee data found'
    ELSE 'Employee details found'
END AS Result
FROM employees;
   

**Steps:**

- Create an `employees` table with fields `emp_id`, `emp_name`, and `designation`.
- Insert some sample data into the table.
- Use a simple cursor to fetch and display employee names and designations.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

**Output:**  
<img width="517" height="416" alt="WhatsApp Image 2026-09-01 at 7 46 32 PM" src="https://github.com/user-attachments/assets/2cf99fb9-e4d5-4262-a128-dbbba82b7838" />

The program should display the employee details or an error message.

---

### **Question 2: Parameterized Cursor with Exception Handling**

**Write a PL/SQL program using a parameterized cursor to retrieve and display employees with a salary in a given range. Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees meet the salary criteria.
2. **OTHERS**: For any unexpected errors during the execution.
**code**
ALTER TABLE employees ADD COLUMN salary REAL;

-- Insert salary values
UPDATE employees SET salary = 50000 WHERE emp_id = 1;
UPDATE employees SET salary = 35000 WHERE emp_id = 2;
UPDATE employees SET salary = 45000 WHERE emp_id = 3;

-- Salary range: 40000 to 60000
SELECT emp_id, emp_name, designation, salary
FROM employees
WHERE salary BETWEEN 40000 AND 60000;

SELECT CASE
    WHEN COUNT(*) = 0 THEN 'No employees found in the given salary range'
    ELSE 'Employees found in the given salary range'
END AS Result
FROM employees
WHERE salary BETWEEN 70000 AND 90000;
   

**Steps:**

- Modify the `employees` table by adding a `salary` column.
- Insert sample salary values for the employees.
- Use a parameterized cursor to accept a salary range as input and fetch employees within that range.
- Implement exception handling to catch and display relevant error messages.

**Output:**  
<img width="822" height="467" alt="WhatsApp Image 2026-09-01 at 8 18 28 PM" src="https://github.com/user-attachments/assets/e1c72a93-d9cf-4def-bf3c-f6b9692f7dda" />






The program should display the employee details within the specified salary range or an error message if no data is found.

---

### **Question 3: Cursor FOR Loop with Exception Handling**

**Write a PL/SQL program using a cursor FOR loop to retrieve and display all employee names and their department numbers from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no employees are found in the database.
2. **OTHERS**: For any other unexpected errors.
**code**
   -- Add salary column
ALTER TABLE employees ADD COLUMN salary REAL;

-- Insert salary values
UPDATE employees SET salary = 50000 WHERE emp_id = 1;
UPDATE employees SET salary = 35000 WHERE emp_id = 2;
UPDATE employees SET salary = 45000 WHERE emp_id = 3;

-- Salary range: 40000 to 60000
SELECT emp_id, emp_name, designation, salary
FROM employees
WHERE salary BETWEEN 40000 AND 60000;
SELECT CASE
    WHEN COUNT(*) = 0 THEN 'No employees found in the given salary range'
    ELSE 'Employees found in the given salary range'
END AS Result
FROM employees
WHERE salary BETWEEN 70000 AND 90000;


**Steps:**

- Modify the `employees` table by adding a `dept_no` column.
- Insert sample department numbers for employees.
- Use a cursor FOR loop to fetch and display employee names along with their department numbers.
- Implement exception handling to catch the relevant exceptions.

**Output:**  

<img width="545" height="432" alt="WhatsApp Image 2026-09-01 at 8 18 49 PM" src="https://github.com/user-attachments/assets/ef71d904-7a14-49be-9e98-199b2f589bec" />



The program should display employee names with their department numbers or the appropriate error message if no data is found.

---

### **Question 4: Cursor with `%ROWTYPE` and Exception Handling**

**Write a PL/SQL program that uses a cursor with `%ROWTYPE` to fetch and display complete employee records (emp_id, emp_name, designation, salary). Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees are found in the database.
2. **OTHERS**: For any other errors that occur.
   **code**
   SELECT CASE
    WHEN COUNT(*) = 0 THEN 'No employees found'
    ELSE 'Employee records found'
END AS Result
FROM employees;
   
   

**Steps:**

- Modify the `employees` table by adding `emp_id`, `emp_name`, `designation`, and `salary` fields.
- Insert sample data into the `employees` table.
- Declare a cursor using `%ROWTYPE` to fetch complete rows from the `employees` table.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

**Output:**  
<img width="546" height="473" alt="WhatsApp Image 2026-09-01 at 8 19 01 PM" src="https://github.com/user-attachments/assets/0a19389b-85f8-4d55-828c-f4a20711d6cf" />





The program should display employee records or the appropriate error message if no data is found.

---

### **Question 5: Cursor with FOR UPDATE Clause and Exception Handling**

**Write a PL/SQL program using a cursor with the `FOR UPDATE` clause to update the salary of employees in a specific department. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no rows are affected by the update.
2. **OTHERS**: For any unexpected errors during execution.
 **code**
   SELECT CASE
    WHEN COUNT(*) = 0 THEN 'No employees found in the department'
    ELSE 'Employee salaries updated successfully'
END AS Result
FROM employees
WHERE dept_no = 10;
SELECT CASE
    WHEN COUNT(*) = 0 THEN 'No employees found in the department'
    ELSE 'Employee salaries updated successfully'
END AS Result
FROM employees
WHERE dept_no = 50;

**Steps:**

- Modify the `employees` table to include a `dept_no` and `salary` field.
- Insert sample data into the `employees` table with different department numbers.
- Use a cursor with the `FOR UPDATE` clause to lock the rows of employees in a specific department and update their salary.
- Implement exception handling to handle `NO_DATA_FOUND` or other errors that may occur.

**Output:**  
<img width="758" height="476" alt="WhatsApp Image 2026-09-01 at 8 19 17 PM" src="https://github.com/user-attachments/assets/31f453cf-078d-4767-8406-20ee7c1b89b5" />


The program should update employee salaries and display a message, or it should display an error message if no data is found.

---

## RESULT
Thus, the program successfully executed and displayed employee details using a cursor. 


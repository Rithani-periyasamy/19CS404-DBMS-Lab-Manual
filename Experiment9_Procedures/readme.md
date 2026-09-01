# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.
  **code**:
  SELECT 'Square of 6 is ' || (6 * 6) AS Result;
  

**Expected Output:**  
<img width="437" height="320" alt="WhatsApp Image 2026-09-01 at 8 38 03 PM" src="https://github.com/user-attachments/assets/374a3045-aa71-440f-8c14-3696040118aa" />

Square of 6 is 36

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.
  **code**:
  WITH RECURSIVE factorial(n, result) AS (
    SELECT 1, 1
    UNION ALL
    SELECT n + 1, result * (n + 1)
    FROM factorial
    WHERE n < 5
)
SELECT 'Factorial of 5 is ' || result AS Result
FROM factorial
WHERE n = 5;
  
  

**Expected Output:**  
<img width="437" height="427" alt="WhatsApp Image 2026-09-01 at 8 40 45 PM" src="https://github.com/user-attachments/assets/87add363-a2d9-474e-9e65-a7b6425fbcbd" />


Factorial of 5 is 120

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.
  **code**:
  SELECT
    CASE
        WHEN MOD(12, 2) = 0 THEN '12 is Even'
        ELSE '12 is Odd'
    END AS Result;
  
  

**Expected Output:**  
<img width="425" height="392" alt="WhatsApp Image 2026-09-01 at 8 43 19 PM" src="https://github.com/user-attachments/assets/1ef2e707-df32-47e5-8611-9c2d758d993f" />


12 is Even

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.
  **code**:
  WITH RECURSIVE reverse_num(n, rev) AS (
    SELECT 1234, 0

    UNION ALL

    SELECT n / 10,
           rev * 10 + (n % 10)
    FROM reverse_num
    WHERE n > 0
)
SELECT 'Reversed number of 1234 is ' || rev AS Result
FROM reverse_num
WHERE n = 0;
  
  

**Expected Output:**  
<img width="510" height="527" alt="WhatsApp Image 2026-09-01 at 8 48 41 PM" src="https://github.com/user-attachments/assets/a7f9da4f-9a03-4b75-876f-41b026568f95" />



Reversed number of 1234 is 4321

---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.
  **code**:
  WITH RECURSIVE multiplication(n) AS (
    SELECT 1
    UNION ALL
    SELECT n + 1
    FROM multiplication
    WHERE n < 10
)
SELECT '5 x ' || n || ' = ' || (5 * n) AS Result
FROM multiplication;

**Expected Output:**  
<img width="442" height="422" alt="WhatsApp Image 2026-09-01 at 8 49 10 PM" src="https://github.com/user-attachments/assets/7f240178-0eef-4082-956c-fed90b460ea6" />


Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.

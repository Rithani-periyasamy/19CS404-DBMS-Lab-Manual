# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

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

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.
  ### Code:
  SET SERVEROUTPUT ON;

DECLARE
    -- Declare two variables to hold the input numbers
    num1 NUMBER := 45; 
    num2 NUMBER := 82;
BEGIN
    -- Compare the two numbers
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('The greatest number is: ' || num1);
    ELSIF num2 > num1 THEN
        DBMS_OUTPUT.PUT_LINE('The greatest number is: ' || num2);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Both numbers are equal: ' || num1);
    END IF;
END;
/


**Expected Output:**  
<img width="572" height="262" alt="image" src="https://github.com/user-attachments/assets/14b5e8c2-6a1a-45ea-8eb1-0c4b4a627bac" />


---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.
### code:
SET SERVEROUTPUT ON;

DECLARE
    -- Define the total elements (N)
    v_n       NUMBER := 10; 
    -- Variable to store the final cumulative sum
    v_sum     NUMBER := 0;   
    -- Counter variable for the loop
    v_counter NUMBER;        
BEGIN
    -- Loop from 1 to N to add each natural number
    FOR v_counter IN 1..v_n LOOP
        v_sum := v_sum + v_counter;
    -- End of execution loop
    END LOOP;

    -- Output the calculated results
    DBMS_OUTPUT.PUT_LINE('The value of N is: ' || v_n);
    DBMS_OUTPUT.PUT_LINE('The sum of the first ' || v_n || ' natural numbers is: ' || v_sum);
END;
/


**Expected Output:**  
<img width="542" height="280" alt="image" src="https://github.com/user-attachments/assets/07b666bd-a278-41d5-8c38-d80f7d0cea06" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.
### code:
DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');

    FOR i IN 1..n LOOP
        DBMS_OUTPUT.PUT(a || ', ');
        c := a + b;
        a := b;
        b := c;
    END LOOP;

    DBMS_OUTPUT.NEW_LINE;
END;
/
  

**Expected Output:**  
<img width="448" height="278" alt="image" src="https://github.com/user-attachments/assets/083a95a2-bab0-477a-a921-ebf069b3b60a" />


---

## 4. Write a PL/SQL Program to display the number in Reverse Order


### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.
 ### code:
 DECLARE
   num       NUMBER := 12345; -- Input number to reverse
   orig_num  NUMBER;          -- Variable to store the original number
   rem       NUMBER;          -- Variable to store the remainder
   rev_num   NUMBER := 0;     -- Variable to store the reversed number
BEGIN
   orig_num := num; -- Save original value for the output message
   
   -- Loop to reverse the number mathematically
   WHILE num > 0 LOOP
      rem := MOD(num, 10);          -- Extract the last digit
      rev_num := (rev_num * 10) + rem; -- Append digit to the reversed number
      num := TRUNC(num / 10);       -- Remove the last digit from original
   END LOOP;
   
   -- Display the result
   DBMS_OUTPUT.PUT_LINE('Original Number: ' || orig_num);
   DBMS_OUTPUT.PUT_LINE('Reversed Number: ' || rev_num);
END;
/

 
  

**Expected Output:**  
<img width="663" height="273" alt="image" src="https://github.com/user-attachments/assets/ebb2eb44-6609-4f39-b40b-5840e6d76a63" />



---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.
 ### code:
 SET SERVEROUTPUT ON;

DECLARE
    -- Declare and initialize three test numbers
    num1 NUMBER := 45;
    num2 NUMBER := 89;
    num3 NUMBER := 21;
    largest NUMBER;
BEGIN
    -- Check if num1 is the greatest
    IF (num1 >= num2 AND num1 >= num3) THEN
        largest := num1;
    -- Check if num2 is the greatest
    ELSIF (num2 >= num1 AND num2 >= num3) THEN
        largest := num2;
    -- If neither, num3 must be the greatest
    ELSE
        largest := num3;
    END IF;

    -- Print the final result
    DBMS_OUTPUT.PUT_LINE('The numbers are: ' || num1 || ', ' || num2 || ', ' || num3);
    DBMS_OUTPUT.PUT_LINE('The largest number is: ' || largest);
END;
/


**Expected Output:**  
<img width="589" height="307" alt="image" src="https://github.com/user-attachments/assets/d65c2cda-7dbe-4c9c-8c6d-43b59919f254" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

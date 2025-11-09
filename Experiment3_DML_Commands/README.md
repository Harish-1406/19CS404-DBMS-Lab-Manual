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
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.
```
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
```
```sql
update products
set reorder_lvl='40'
where category='Grocery'
```

**Output:**

<img width="1254" height="365" alt="image" src="https://github.com/user-attachments/assets/c127ad18-08ff-4267-94a0-aa2b7e2bf0fa" />


**Question 2**
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.
```
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

```
```sql
update products
set reorder_lvl = reorder_lvl * 0.70
where product_name LIKE '%cream%' AND quantity > reorder_lvl
```

**Output:**

<img width="1290" height="476" alt="image" src="https://github.com/user-attachments/assets/dfbe503d-2643-4f43-89d0-41cb97e8d1d5" />


**Question 3**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.
```
products table

---------------
product_id
product_name
category_id
availability
```
```sql
update products
set product_name='Grapefruit'
where product_id=4
```

**Output:**

<img width="1050" height="234" alt="image" src="https://github.com/user-attachments/assets/463d53fc-8d32-4cea-8778-d933878c0834" />

**Question 4**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.
```
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
```

```sql
update employees
set first_name='John'
where department_id=80 and commission_pct < 0.35
```

**Output:**

<img width="1281" height="520" alt="image" src="https://github.com/user-attachments/assets/1b9abd4d-8360-46a2-ac76-92994f5a9d9d" />


**Question 5**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.
```
name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
```
```sql
update suppliers
set supplier_name=UPPER(supplier_name)
where contact_person like '%Singh%'
```

**Output:**

<img width="1268" height="349" alt="image" src="https://github.com/user-attachments/assets/dcd6d062-63ec-4678-b738-d945e65e4870" />


**Question 6**
---Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
delete from customer
where GRADE <> 3
```

**Output:**

<img width="586" height="478" alt="image" src="https://github.com/user-attachments/assets/dccbdff4-8de9-4393-b1be-42aaed296a1f" />


**Question 7**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
delete from doctors
where specialization is NULL
```

**Output:**

<img width="1043" height="854" alt="image" src="https://github.com/user-attachments/assets/f7441dc1-d65e-47bd-afb5-26e5d3776f84" />


**Question 8**
---
Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```sql
delete from doctors
where doctor_id between 2 and 4
```

**Output:**

<img width="1014" height="722" alt="image" src="https://github.com/user-attachments/assets/8140b152-8d3b-420c-b695-7395b2ec30a3" />

**Question 9**
---
Write a SQL query to Select all patients who were admitted during the year 2023.
```
Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT
```
```sql
select patient_id,first_name,admission_date
from patients
where admission_date >= '2023-01-01' AND admission_date <= '2023-12-31';
```

**Output:**

<img width="700" height="322" alt="image" src="https://github.com/user-attachments/assets/c5c7f87f-1d28-48f2-a000-f78309f52ca1" />


**Question 10**
---
Write a SQL query to label rows in the Calculations table as 'Even' if value1 is even, otherwise 'Odd'.
```
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
```

```sql
select id,value1,
case
when value1%2 = 0 then 'Even'
else 'Odd'
end as parity
from Calculations
```

**Output:**

<img width="694" height="433" alt="image" src="https://github.com/user-attachments/assets/c75bf439-c166-4dd3-87f8-92e475d8b6f6" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

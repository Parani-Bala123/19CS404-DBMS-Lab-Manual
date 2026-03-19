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
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
DELETE FROM customer
WHERE cust_city LIKE 'L%';

```

**Output:**

<img width="1204" height="917" alt="image" src="https://github.com/user-attachments/assets/085bc2f2-148c-475c-84c3-2b799caa32f6" />


**Question 2**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'


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


```sql
UPDATE employees
SET salary = salary * 2
WHERE department_id = 20
AND job_id LIKE '%MAN';

```

**Output:**

<img width="826" height="423" alt="image" src="https://github.com/user-attachments/assets/ddcdad12-f9ff-47b6-bc94-bbcd192139b6" />


**Question 3**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

```sql
UPDATE suppliers
SET supplier_name = 'A1 Suppliers'
WHERE supplier_id = 8;

```

**Output:**

<img width="830" height="462" alt="image" src="https://github.com/user-attachments/assets/58981bfc-adfc-44e1-adca-b82e89c2296c" />


**Question 4**
---
Write a SQL query to find all employees who were hired in the last 6 months from the emp table. 

Note: Assume current date as '01-09-2024'

emp table

cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT         

```sql
SELECT *
FROM emp
WHERE hiredate BETWEEN '2024-03-01' AND '2024-09-01';

```

**Output:**

<img width="834" height="425" alt="image" src="https://github.com/user-attachments/assets/5aa85bc1-a2b4-46ac-9436-a55819fcad14" />


**Question 5**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id


```sql
UPDATE products
SET product_name = 'Premium Bread'
WHERE product_id = 5;

```

**Output:**

<img width="834" height="480" alt="image" src="https://github.com/user-attachments/assets/550a778f-0986-431a-9437-6b5c984990b9" />


**Question 6**
---
Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE city = 'New York'
OR grade <= 100;

```

**Output:**

<img width="831" height="492" alt="image" src="https://github.com/user-attachments/assets/e23a990d-e8d7-434e-b7fa-877ff7ac2305" />


**Question 7**
---
Write a SQL query to calculate the original price using the discount percentage and the given discounted price. Return product_id, discounted_price, discount_percentage, and original_price.

Sample table: Products

product_id | discounted_price | discount_percentage

 ------------+------------------+---------------------

 101 | 45.00 | 0.10 

102 | 63.75 | 0.15 

103 | 80.00 | 0.20

```sql
SELECT 
    product_id,
    discounted_price,
    discount_percentage,
    discounted_price / (1 - discount_percentage) AS original_price
FROM Products;

```

**Output:**

<img width="840" height="367" alt="image" src="https://github.com/user-attachments/assets/9721936f-0340-4888-90f9-e70e3cbbf685" />


**Question 8**
---
For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

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

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)

```sql
UPDATE sales
SET sell_price = sell_price + 3
WHERE product_id IN (
    SELECT product_id
    FROM products
    WHERE supplier_id = 4
);

```

**Output:**

<img width="827" height="453" alt="image" src="https://github.com/user-attachments/assets/acb22fbd-242e-4e82-bde8-3c2545145b24" />


**Question 9**
---
Write a SQL query to find the details of those salespeople who live in cities other than Paris and Rome. Return salesman_id, name, city, commission.

Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11

```sql
SELECT salesman_id, name, city, commission
FROM salesman
WHERE city NOT IN ('Paris', 'Rome');

```

**Output:**

<img width="835" height="482" alt="image" src="https://github.com/user-attachments/assets/22bb78a3-ff5d-4801-a307-62dbd0a1d76f" />


**Question 10**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM doctors
WHERE specialization IN ('Pediatrics', 'Cardiology')
AND last_name = 'Brown';

```

**Output:**

<img width="843" height="916" alt="image" src="https://github.com/user-attachments/assets/c4856c9e-e12e-4f4a-88ca-afa2ffb8fedf" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

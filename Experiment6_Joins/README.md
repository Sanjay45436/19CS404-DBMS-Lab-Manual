# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--

<img width="1331" height="429" alt="image" src="https://github.com/user-attachments/assets/39e81098-4ea5-4ec0-b6df-bdf149204cbf" />


```sql

SELECT
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM customer AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id;

```

**Output:**

<img width="912" height="851" alt="image" src="https://github.com/user-attachments/assets/ec2db646-29cb-4a1a-979d-f01521b106bd" />


**Question 2**
---

<img width="1299" height="484" alt="image" src="https://github.com/user-attachments/assets/bb6fc5e8-44e9-4362-93e2-830353179a7a" />


```sql

SELECT
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM patients AS p
INNER JOIN doctors AS d
    ON p.doctor_id = d.doctor_id
WHERE p.discharge_date IS NULL;

```

**Output:**

<img width="494" height="370" alt="image" src="https://github.com/user-attachments/assets/22d40055-2702-4f1c-aaf1-b674679e6fef" />


**Question 3**
---

<img width="1337" height="593" alt="image" src="https://github.com/user-attachments/assets/9d0a2c44-f697-42f2-9ca9-ae9439f71f7d" />


```sql

SELECT
    c.cust_name AS "Customer Name",
    c.city AS city,
    s.name AS Salesman,
    s.city AS city,
    s.commission
FROM customer AS c
JOIN salesman AS s
    ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city
  AND s.commission > 0.12;

```

**Output:**

<img width="1063" height="459" alt="image" src="https://github.com/user-attachments/assets/a5b20f7c-32b5-41b7-8b3a-0ec7d7734c49" />


**Question 4**
---

<img width="1337" height="459" alt="image" src="https://github.com/user-attachments/assets/33160c81-2e2c-447d-b70d-b7db73e5bd61" />


```sql

SELECT p.*
FROM patients AS p
INNER JOIN test_results AS t
    ON p.patient_id = t.patient_id
WHERE t.test_name = 'X-Ray'
  AND t.result = 'Normal';

```

**Output:**

<img width="1326" height="335" alt="image" src="https://github.com/user-attachments/assets/32f58990-3414-4ead-bd54-04a59d4f3d19" />


**Question 5**
---

<img width="1237" height="614" alt="image" src="https://github.com/user-attachments/assets/48ca7a16-42be-4fae-889a-285b6d914e3a" />


```sql

SELECT
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM customer AS c
INNER JOIN salesman AS s
    ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;

```

**Output:**

<img width="1052" height="568" alt="image" src="https://github.com/user-attachments/assets/dd46f014-24cc-4b27-952e-2d0d2737e77d" />

**Question 6**
---

<img width="846" height="910" alt="image" src="https://github.com/user-attachments/assets/8213dc41-4d1b-4cf3-abde-4cfb0413b312" />


```sql

SELECT
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS Salesman,
    s.commission
FROM orders AS o
INNER JOIN customer AS c
    ON o.customer_id = c.customer_id
INNER JOIN salesman AS s
    ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1262" height="755" alt="image" src="https://github.com/user-attachments/assets/53eceb98-c3a7-447b-a63d-030be20fc001" />


**Question 7**
---

<img width="1020" height="645" alt="image" src="https://github.com/user-attachments/assets/1ef83010-5ddf-4a6b-8058-1bb9fd9491e1" />


```sql

SELECT
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM customer AS c
INNER JOIN salesman AS s
    ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;

```

**Output:**

<img width="1043" height="663" alt="image" src="https://github.com/user-attachments/assets/7b436ab8-6b0d-4369-8b84-7fd09eac4255" />


**Question 8**
---

<img width="1323" height="465" alt="image" src="https://github.com/user-attachments/assets/fff08399-8bf8-4cbb-ba42-1ea004d46c50" />


```sql

SELECT p.*
FROM patients AS p
INNER JOIN appointments AS a
    ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="1348" height="335" alt="image" src="https://github.com/user-attachments/assets/c65510f2-245e-44d0-bcd6-baa4d29edc91" />


**Question 9**
---

<img width="1115" height="613" alt="image" src="https://github.com/user-attachments/assets/5955542d-f4e3-4a7a-b6af-d0ce5e8a6a01" />



```sql

SELECT
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS Salesman,
    s.commission
FROM customer AS c
INNER JOIN salesman AS s
    ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

**Output:**

<img width="907" height="562" alt="image" src="https://github.com/user-attachments/assets/42a08c7c-1660-41f3-9507-2b3f5d4405df" />


**Question 10**
---

<img width="1349" height="378" alt="image" src="https://github.com/user-attachments/assets/52456e2e-c2e3-4f78-87d8-b33bcf192e4e" />


```sql

SELECT
    s.name AS salesman_name,
    c.cust_name AS customer_name
FROM salesman AS s
LEFT JOIN customer AS c
    ON s.salesman_id = c.salesman_id;

```

**Output:**

<img width="509" height="663" alt="image" src="https://github.com/user-attachments/assets/a6328e78-8501-4a9f-89dd-916e2d5d568e" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

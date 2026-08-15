# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--

<img width="948" height="495" alt="image" src="https://github.com/user-attachments/assets/115311ae-f6c2-494f-944a-c2971b888805" />


```sql

SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM orders o
JOIN salesman s
    ON o.salesman_id = s.salesman_id
WHERE s.city = 'London';

```

**Output:**

<img width="836" height="322" alt="image" src="https://github.com/user-attachments/assets/7360f7d8-509f-4a95-9425-55ba52363bba" />

**Question 2**
---

<img width="967" height="514" alt="image" src="https://github.com/user-attachments/assets/f496a0df-17da-4c32-8f94-fb0837c33517" />


```sql

SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM orders o
JOIN salesman s
    ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**

<img width="853" height="363" alt="image" src="https://github.com/user-attachments/assets/3350cac4-cbe8-451f-8487-137ee85a3b2d" />


**Question 3**
---
<img width="661" height="452" alt="image" src="https://github.com/user-attachments/assets/03585d6e-1672-4cfa-9e7a-085b7b954390" />


```sql

SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;

```

**Output:**

<img width="800" height="338" alt="image" src="https://github.com/user-attachments/assets/15e89eb3-020c-49b2-9a3c-6a1e38de7f7c" />


**Question 4**
---
<img width="839" height="422" alt="image" src="https://github.com/user-attachments/assets/e1568187-515c-4035-8cb4-1c39ff3b80ed" />


```sql

SELECT *
FROM Grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="896" height="328" alt="image" src="https://github.com/user-attachments/assets/86a0e2d6-7e86-4009-a2fb-d214bef9f8c6" />

**Question 5**
---
<img width="823" height="424" alt="image" src="https://github.com/user-attachments/assets/142afd5b-af2a-4a65-8826-249729bba6a4" />


```sql

SELECT *
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="909" height="342" alt="image" src="https://github.com/user-attachments/assets/f91c7630-6769-4583-b2dc-b6bfa44de764" />

**Question 6**
---

<img width="655" height="416" alt="image" src="https://github.com/user-attachments/assets/787b5630-7892-4252-aaf2-188928552a66" />

```sql

SELECT *
FROM CUSTOMERS
WHERE SALARY = 1500;

```

**Output:**

<img width="828" height="279" alt="image" src="https://github.com/user-attachments/assets/d0fae8f4-3996-40d3-aa17-2d193897245a" />

**Question 7**
---

<img width="657" height="498" alt="image" src="https://github.com/user-attachments/assets/385ae226-cbd1-4812-b0ed-94a4d23a7bf3" />

```sql

SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;

```

**Output:**

<img width="808" height="453" alt="image" src="https://github.com/user-attachments/assets/5df52984-faff-48a1-9147-cc2e110caec7" />

**Question 8**
---

<img width="699" height="457" alt="image" src="https://github.com/user-attachments/assets/3004acbd-16ec-49b7-907c-2962bccf9fd8" />


```sql

SELECT commission
FROM salesman
WHERE salesman_id IN (
    SELECT salesman_id
    FROM customer
    WHERE city = 'Paris'
);

```

**Output:**

<img width="287" height="278" alt="image" src="https://github.com/user-attachments/assets/b40df5f7-7bdd-4288-9fda-babc9744a581" />


**Question 9**
---

<img width="768" height="310" alt="image" src="https://github.com/user-attachments/assets/23fe8762-5fbc-4d59-bcc9-9e2ae2077348" />


```sql

SELECT
    department_id AS depar,
    department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);

```

**Output:**

<img width="400" height="318" alt="image" src="https://github.com/user-attachments/assets/a7c2e219-3296-4a6f-9ff9-db9e70b39695" />

**Question 10**
---

<img width="702" height="369" alt="image" src="https://github.com/user-attachments/assets/86106798-a229-42aa-b5ab-8b888d321144" />


```sql

SELECT *
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (SELECT MAX(id) FROM customer)
);

```

**Output:**

<img width="947" height="378" alt="image" src="https://github.com/user-attachments/assets/b20f52db-9187-44a1-94bc-7936e855fb4a" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

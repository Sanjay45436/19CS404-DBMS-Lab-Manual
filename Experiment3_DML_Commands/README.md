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
<img width="1054" height="387" alt="image" src="https://github.com/user-attachments/assets/7873edf2-5be7-4fe0-a096-fb9fbc169575" />

```sql
UPDATE Products
SET reorder_lvl = 20
WHERE quantity < 10
AND category = 'Snacks';

```

**Output:**

<img width="1259" height="524" alt="image" src="https://github.com/user-attachments/assets/a2bf58cb-a0a9-4934-ac79-460cb0364b37" />

**Question 2**
---

<img width="877" height="436" alt="image" src="https://github.com/user-attachments/assets/5dda0e8e-cda2-44e1-9321-234302c142a1" />

```sql
UPDATE Products
SET category = 'Household'
WHERE product_name LIKE '%Detergent%';

```

**Output:**

<img width="1262" height="460" alt="image" src="https://github.com/user-attachments/assets/9b4d2202-7fd9-4ae4-969b-66a41deaf4e4" />

**Question 3**
---

<img width="993" height="498" alt="image" src="https://github.com/user-attachments/assets/5f911d78-68c2-465f-b4da-28f5e09a9d6c" />

```sql
UPDATE Employees
SET salary = salary * 2
WHERE department_id = 20
  AND job_id LIKE '%MAN';

```

**Output:**

<img width="1276" height="353" alt="image" src="https://github.com/user-attachments/assets/23970890-569a-416d-b7ec-5defdf44ada9" />

**Question 4**
---
<img width="861" height="232" alt="image" src="https://github.com/user-attachments/assets/1cd39606-2edc-4aaa-9738-dbbe21509205" />

```sql
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15
  AND sale_date = '2023-01-31';

```

**Output:**

<img width="1270" height="430" alt="image" src="https://github.com/user-attachments/assets/b619b35a-efe3-4f02-8356-e2635444d90a" />

**Question 5**
---

<img width="808" height="402" alt="image" src="https://github.com/user-attachments/assets/30891afb-be77-4c60-b450-1f7f8438544c" />

```sql
UPDATE Suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;

```

**Output:**

<img width="1276" height="386" alt="image" src="https://github.com/user-attachments/assets/ea591c85-6587-4e41-ab3e-44b34f45121d" />

**Question 6**
---
<img width="1281" height="370" alt="image" src="https://github.com/user-attachments/assets/c3407b6a-db6c-443d-ba3d-328e3e499e10" />

```sql

DELETE FROM customer
WHERE CUST_CITY <> 'New York'
  AND OUTSTANDING_AMT > 5000;
```

**Output:**

<img width="1245" height="524" alt="image" src="https://github.com/user-attachments/assets/4500a82e-6ee7-4e90-bdd9-d3abb56335e4" />

**Question 7**
---
<img width="1278" height="375" alt="image" src="https://github.com/user-attachments/assets/71ffe81d-adcb-4dfd-8f2f-b91b1d4d422b" />

```sql
DELETE FROM customer
WHERE GRADE % 2 <> 0;
```

**Output:**

<img width="1253" height="405" alt="image" src="https://github.com/user-attachments/assets/4eb384da-7243-420d-b186-2326462cc631" />

**Question 8**
---
<img width="1286" height="516" alt="image" src="https://github.com/user-attachments/assets/7819aef6-cf32-4482-b321-803ff60e36ca" />

```sql
DELETE FROM customer
WHERE LENGTH(CUST_NAME) = 6;
```

**Output:**

<img width="1258" height="655" alt="image" src="https://github.com/user-attachments/assets/280bc626-76f6-40d5-911c-b1d45acc1012" />

**Question 9**
---
<img width="1274" height="374" alt="image" src="https://github.com/user-attachments/assets/5c9cc05d-ec12-42db-adc4-aa89e80a6568" />

```sql

DELETE FROM customer
WHERE (GRADE = 3 OR AGENT_CODE = 'A008')
  AND OUTSTANDING_AMT < 5000;

```

**Output:**

<img width="1258" height="386" alt="image" src="https://github.com/user-attachments/assets/1939cef7-a7fe-4793-bbf4-d2c24b1a3174" />

**Question 10**
---
<img width="1264" height="374" alt="image" src="https://github.com/user-attachments/assets/19c1efe9-c935-42f7-aa08-3320b9de4cd9" />

```sql

DELETE FROM customer
WHERE GRADE = 2
  AND CUST_NAME LIKE 'M%'
  AND PAYMENT_AMT < 3000;

```

**Output:**

<img width="1277" height="391" alt="image" src="https://github.com/user-attachments/assets/a24a4fd1-9bc0-4d71-8b00-b74da15b53d5" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

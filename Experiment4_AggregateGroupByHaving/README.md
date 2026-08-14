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

<img width="821" height="514" alt="image" src="https://github.com/user-attachments/assets/160d6441-9852-48a6-920d-ecf0be0aa680" />


```sql
SELECT 
    Medication,
    COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication
ORDER BY Medication;

```

**Output:**

<img width="735" height="593" alt="image" src="https://github.com/user-attachments/assets/1a72a16a-91fc-4dd2-9872-fba09727015f" />

**Question 2**
---
-- 
<img width="813" height="439" alt="image" src="https://github.com/user-attachments/assets/63a72de7-89b4-466a-a5a4-15305a5cfbf8" />


```sql

SELECT 
    DoctorID,
    COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;

```

**Output:**

<img width="600" height="550" alt="image" src="https://github.com/user-attachments/assets/3eae4784-253e-40e2-8cb9-e646551f6e1f" />

**Question 3**
---
-- 

<img width="804" height="392" alt="image" src="https://github.com/user-attachments/assets/ada1d7a6-26d5-4b8b-a7e6-b9e48cd849c6" />


```sql
SELECT
    CASE
        WHEN 2025 - CAST(strftime('%Y', DateOfBirth) AS INTEGER) BETWEEN 20 AND 30
            THEN '20-30'
        WHEN 2025 - CAST(strftime('%Y', DateOfBirth) AS INTEGER) BETWEEN 31 AND 40
            THEN '31-40'
        WHEN 2025 - CAST(strftime('%Y', DateOfBirth) AS INTEGER) BETWEEN 41 AND 50
            THEN '41-50'
        ELSE 'Above 50'
    END AS AgeGroup,
    COUNT(*) AS TotalPatients
FROM Patients
GROUP BY AgeGroup
ORDER BY
    CASE AgeGroup
        WHEN '20-30' THEN 1
        WHEN '31-40' THEN 2
        WHEN '41-50' THEN 3
        WHEN 'Above 50' THEN 4
    END;
```

**Output:**

<img width="508" height="430" alt="image" src="https://github.com/user-attachments/assets/8160602f-0d2b-405e-a871-21243cf528f4" />

**Question 4**
---

<img width="785" height="381" alt="image" src="https://github.com/user-attachments/assets/f7a8eaed-8ede-4dff-8140-4adb5859d2c2" />


```sql

SELECT COUNT(*) AS COUNT
FROM employee
WHERE age > 32;

```

**Output:**

<img width="306" height="322" alt="image" src="https://github.com/user-attachments/assets/ed6a867f-be0b-4f20-b2cc-d5f26cce2b89" />

**Question 5**
---
<img width="678" height="377" alt="image" src="https://github.com/user-attachments/assets/9413fc2b-bbe8-40ea-9c5c-ce25b7bf9763" />

```sql
SELECT AVG(income) AS avg_income
FROM employee
WHERE name LIKE 'A%';

```

**Output:**

<img width="408" height="314" alt="image" src="https://github.com/user-attachments/assets/28cd5cdd-22d4-4673-ba85-cf58d484745f" />

**Question 6**
---

<img width="574" height="380" alt="image" src="https://github.com/user-attachments/assets/075fcdc6-d211-4af9-a221-7d1f17adfdf2" />

```sql
SELECT AVG(LENGTH(email)) AS avg_email_length
FROM customer;

```

**Output:**

<img width="369" height="307" alt="image" src="https://github.com/user-attachments/assets/633d3404-66af-41c5-96b9-2331e212adcc" />


**Question 7**
---

<img width="549" height="434" alt="image" src="https://github.com/user-attachments/assets/7fc55efb-6a06-4412-b135-fb326d21e313" />


```sql
SELECT 
    name AS fruit_name,
    inventory AS lowest_quantity
FROM fruits
WHERE inventory = (SELECT MIN(inventory) FROM fruits);

```

**Output:**

<img width="570" height="308" alt="image" src="https://github.com/user-attachments/assets/750aef99-a38c-49eb-a27c-6c25191fd5f0" />

**Question 8**
---

<img width="1238" height="380" alt="image" src="https://github.com/user-attachments/assets/675853a6-541f-4b69-889e-21cd1c58261f" />

```sql

SELECT
    (age / 5) * 5 AS age_group,
    SUM(salary)
FROM customer1
GROUP BY (age / 5) * 5
HAVING SUM(salary) > 5000;

```

**Output:**

<img width="470" height="343" alt="image" src="https://github.com/user-attachments/assets/656b0366-f3a5-444f-baed-242b61807ee1" />

**Question 9**
---

<img width="1247" height="381" alt="image" src="https://github.com/user-attachments/assets/f51c4829-38e0-4b6b-a22d-1675a0d51157" />


```sql

SELECT
    category_id,
    SUM(price) AS Total_Cost
FROM products
GROUP BY category_id
HAVING SUM(price) > 50;

```

**Output:**

<img width="484" height="319" alt="image" src="https://github.com/user-attachments/assets/8618420c-1c6c-42d8-86f7-b1c7e08dc15f" />

**Question 10**
---

<img width="1215" height="398" alt="image" src="https://github.com/user-attachments/assets/82f2c63b-5a12-4d8e-b3f0-598d375416bb" />

```sql

SELECT
    category_id,
    count(product_name)
FROM products
GROUP BY category_id
HAVING MIN(category_id) < 3;

```

**Output:**

<img width="640" height="335" alt="image" src="https://github.com/user-attachments/assets/527f4fef-eac7-46af-9ca0-0ec53c54d441" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

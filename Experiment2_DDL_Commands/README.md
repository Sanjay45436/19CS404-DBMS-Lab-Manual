# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
---
<img width="1197" height="319" alt="image" src="https://github.com/user-attachments/assets/c126dce7-e23c-4d5f-b9db-c44371aeba2c" />



```
ALTER TABLE Companies RENAME COLUMN name TO first_name;

ALTER TABLE Companies ADD COLUMN mobilenumb number;

ALTER TABLE Companies ADD COLUMN DOB Date;

ALTER TABLE Companies ADD COLUMN State varchar(30);

```

**Output:**

<img width="1265" height="374" alt="image" src="https://github.com/user-attachments/assets/0cae2f90-431b-4dc2-8afe-c2193e2aa7df" />


**Question 2**
---
<img width="902" height="438" alt="image" src="https://github.com/user-attachments/assets/af0b5b8e-a395-4b37-bb98-5c18e1de3606" />


```

ALTER TABLE Student_details
ADD COLUMN mobilenumb number;

```

**Output:**

<img width="1278" height="329" alt="image" src="https://github.com/user-attachments/assets/0c86b30d-b258-4daf-9e67-7e094f7f8e7d" />


**Question 3**
---
<img width="974" height="243" alt="image" src="https://github.com/user-attachments/assets/27f6ab9a-2ac7-4155-a121-484245be5754" />


```

CREATE TABLE Shipments (
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);

```

**Output:**

<img width="1262" height="233" alt="image" src="https://github.com/user-attachments/assets/afa7b811-8b67-4db0-ad31-b1cd1cea5150" />


**Question 4**
---
<img width="1170" height="254" alt="image" src="https://github.com/user-attachments/assets/7baa3790-6706-44ee-b7ef-958f0c331973" />


```

CREATE TABLE Department (
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);

```

**Output:**

<img width="1259" height="277" alt="image" src="https://github.com/user-attachments/assets/aefc4c4d-9833-42f2-b82d-8bc32ef2e842" />


**Question 5**
---
<img width="1248" height="262" alt="image" src="https://github.com/user-attachments/assets/63a85383-e727-4e3f-bae6-0bec295a8e86" />


```
CREATE TABLE Orders (
    OrderID INTEGER PRIMARY KEY,
    OrderDate DATE NOT NULL,
    CustomerID INTEGER,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);

```

**Output:**

<img width="1266" height="265" alt="image" src="https://github.com/user-attachments/assets/a18426bd-a855-46bb-9abb-9d3273907db0" />

**Question 6**
---
<img width="868" height="350" alt="image" src="https://github.com/user-attachments/assets/2f5b5668-cf89-4b70-b918-c3e972f0ee7f" />


```
CREATE TABLE Reviews (
    ReviewID INTEGER,
    ProductID INTEGER,
    Rating REAL,
    ReviewText TEXT
);

```

**Output:**

<img width="1258" height="359" alt="image" src="https://github.com/user-attachments/assets/6f128077-1a0e-4569-b311-252fe6fffbdd" />


**Question 7**
---
<img width="862" height="285" alt="image" src="https://github.com/user-attachments/assets/9c9e91e8-ecd6-481d-b819-6fd2a4c90a79" />

```
INSERT INTO Books (ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM Out_of_print_books;

```

**Output:**

<img width="1271" height="274" alt="image" src="https://github.com/user-attachments/assets/44b1bfc6-fe0b-427e-90f4-84abe9b75c71" />


**Question 8**
---
<img width="1096" height="199" alt="image" src="https://github.com/user-attachments/assets/300e72e4-8ea6-45d8-8ade-bf7a81d66aea" />

```
INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES ('978-1234567890', 'Data Science Essentials', 'Jane Doe', 'TechBooks', 2024);

```

**Output:**

<img width="1281" height="234" alt="image" src="https://github.com/user-attachments/assets/27106696-fa25-434d-a15c-f873db09e16c" />


**Question 9**
---
<img width="1420" height="379" alt="image" src="https://github.com/user-attachments/assets/e39783f2-8ef6-4f00-bb7f-676f4c63ca88" />

```
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (5, 'George Clark', 'Consultant', NULL, NULL);

INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (7, 'Noah Davis', 'Manager', 'HR', 60000);

INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (8, 'Ava Miller', 'Consultant', 'IT', NULL);

```

**Output:**

<img width="1103" height="255" alt="image" src="https://github.com/user-attachments/assets/13e8a54e-faa4-465d-a7f3-8f3124a6e749" />


**Question 10**
---
<img width="1305" height="279" alt="image" src="https://github.com/user-attachments/assets/312ee585-f691-424a-924d-6f74d6354b87" />


```
CREATE TABLE Attendance (
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);

```

**Output:**

<img width="1264" height="270" alt="image" src="https://github.com/user-attachments/assets/be1b5c00-fc27-4906-8d85-021349bcf28c" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

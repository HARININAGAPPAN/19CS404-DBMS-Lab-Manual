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
--
<img width="725" height="213" alt="image" src="https://github.com/user-attachments/assets/783099ee-999f-4d74-afb8-d9b7f0f4d518" />


```sql

ALTER TABLE employee ADD COLUMN designation varchar(50);
```

**Output:**

<img width="828" height="138" alt="image" src="https://github.com/user-attachments/assets/0556ba91-ca53-4e5f-b8b4-d2fe15105fe5" />



**Question 2**
---
<img width="653" height="300" alt="image" src="https://github.com/user-attachments/assets/d450e1a5-b959-4fdb-a29c-71485edf2939" />


```sql
CREATE TABLE Employees(EmployeeID INTEGER,FirstName TEXT,LastName TEXT,HireDate DATE);
```

**Output:**

<img width="813" height="131" alt="image" src="https://github.com/user-attachments/assets/b6aaae22-8950-4803-b618-5c02b386c5a1" />

**Question 3**
---
<img width="658" height="249" alt="image" src="https://github.com/user-attachments/assets/960e9d37-bdf2-4894-96bf-c8fde8148855" />


```sql
CREATE TABLE Locations(LocationID INTEGER,LocationName TEXT,Address TEXT);
```

**Output:**

<img width="820" height="161" alt="image" src="https://github.com/user-attachments/assets/1b0a0950-d662-425d-903c-310d4c93ecc0" />


**Question 4**
---
<img width="661" height="236" alt="image" src="https://github.com/user-attachments/assets/3c2ea4e3-1bcb-4407-a385-02d1da6a665d" />


```sql
CREATE TABLE Members(MemberID INTEGER,MemberName TEXT,JoinDate DATE);
```

**Output:**

<img width="830" height="169" alt="image" src="https://github.com/user-attachments/assets/4060de78-b337-42a2-9bce-2045e49e92bc" />


**Question 5**
---
<img width="807" height="148" alt="image" src="https://github.com/user-attachments/assets/e8e15120-b75d-4265-ae8a-11de05c68f6b" />


```sql

INSERT INTO Products(ProductID,Name,Category,Price,Stock) VALUES (101,'Laptop','Electronics',1500,50);
```

**Output:**

<img width="819" height="137" alt="image" src="https://github.com/user-attachments/assets/603a6958-d9ab-4968-ad6d-695cfcb6c843" />


**Question 6**
---
<img width="694" height="222" alt="image" src="https://github.com/user-attachments/assets/2d0c7ae8-8848-4cfe-84f7-9a5b21da0aed" />


```sql
ALTER TABLE Student_details ADD COLUMN Date_of_birth Date;
```

**Output:**

<img width="816" height="162" alt="image" src="https://github.com/user-attachments/assets/df00234e-3e6c-4241-807f-441f9cea9e6d" />


**Question 7**
---
<img width="560" height="238" alt="image" src="https://github.com/user-attachments/assets/5e260eaf-ad41-4a66-a434-db89a9357b04" />


```sql

CREATE TABLE Products(
    ProductID PRIMARY KEY,
    ProductName NOT NULL,
    Price REAL CHECK(Price>0),
    Stock INTEGER CHECK(Stock>=0)
);
```

**Output:**

<img width="817" height="132" alt="image" src="https://github.com/user-attachments/assets/55201aa7-e2b4-4b9b-b47c-042d0a7ee0ce" />


**Question 8**
---
<img width="796" height="182" alt="image" src="https://github.com/user-attachments/assets/a60fe5ab-7b84-4390-8c75-63663aadb539" />


```sql
CREATE TABLE Attendance(
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT CHECK (Status IN ('Present','Absent','Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
    );
```

**Output:**

<img width="834" height="140" alt="image" src="https://github.com/user-attachments/assets/b75dbf6b-d236-42c7-8371-2f42dcce4070" />


**Question 9**
---
<img width="683" height="245" alt="image" src="https://github.com/user-attachments/assets/3b5524a5-c254-4fd7-aed8-ad6a7f17fb75" />


```sql
INSERT INTO Products(Name,Category,Price,Stock) VALUES ('Smartphone','Electronics',800,150),('Headphones','Accessories',200,300);
```

**Output:**

<img width="839" height="197" alt="image" src="https://github.com/user-attachments/assets/e62c68c0-73f6-43b4-b348-8b0809038c11" />


**Question 10**
---
<img width="1069" height="315" alt="image" src="https://github.com/user-attachments/assets/d08b8529-0d08-4322-a0af-e3a8684358ca" />


```sql
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES (101,'Laptop','Electronics',1500,50);
```

**Output:**

<img width="1167" height="211" alt="image" src="https://github.com/user-attachments/assets/1354977c-6f3e-4039-a913-3af1a59c2f6a" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

<img width="1344" height="63" alt="image" src="https://github.com/user-attachments/assets/2dd12973-7be9-4327-b874-b526c0580f85" />

<img width="1060" height="70" alt="image" src="https://github.com/user-attachments/assets/ab6257c3-de75-4857-b3fd-03976543969a" />



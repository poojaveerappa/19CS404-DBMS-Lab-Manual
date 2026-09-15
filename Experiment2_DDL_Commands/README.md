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
-- Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default values.

For example:
Test 	Result

SELECT ProductID, Name, Category, Price, Stock 
FROM Products 
WHERE ProductID = 104;

	

ProductID   Name        Category     Price       Stock
----------  ----------  -----------  ----------  ----------
104         Tablet      Electronics  100         50


```sql
-- INSERT INTO Products (ProductID, Name, Category)
VALUES (104, 'Tablet', 'Electronics');
```

**Output:**

<img width="1311" height="208" alt="image" src="https://github.com/user-attachments/assets/1b5f2a99-a9d6-4b6b-9651-766e0424695e" />


**Question 2**
---
-- Paste Question 2 here

```sql
-- Paste your SQL code below for Question 2
```

**Output:**

![Output2](output.png)

**Question 3**
---
-- Create a table named Products with the following constraints:

    ProductID as INTEGER should be the primary key.
    ProductName as TEXT should be unique and not NULL.
    Price as REAL should be greater than 0.
    StockQuantity as INTEGER should be non-negative.

For example:
Test 	Result

INSERT INTO Products (ProductID, ProductName, Price, StockQuantity) VALUES (1, 'Laptop', 999.99, 10);
select * from Products;

	

ProductID   ProductName  Price       StockQuantity
----------  -----------  ----------  -------------
1           Laptop       999.99      10


```sql
-- CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT NOT NULL UNIQUE,
    Price REAL CHECK (Price > 0),
    StockQuantity INTEGER CHECK (StockQuantity >= 0)
);
```

**Output:**

<img width="1303" height="235" alt="image" src="https://github.com/user-attachments/assets/518221cb-6d09-4c79-94fd-97d59c6e899a" />


**Question 4**
---
-- Create a new table named item with the following specifications and constraints:

    item_id as TEXT and as primary key.
    item_desc as TEXT.
    rate as INTEGER.
    icom_id as TEXT with a length of 4.
    icom_id is a foreign key referencing com_id in the company table.
    The foreign key should set NULL on updates and deletes.
    item_desc and rate should not accept NULL.

For example:
Test 	Result

INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;

	

item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700


```sql
-- Create a new table named item with the following specifications and constraints:

    item_id as TEXT and as primary key.
    item_desc as TEXT.
    rate as INTEGER.
    icom_id as TEXT with a length of 4.
    icom_id is a foreign key referencing com_id in the company table.
    The foreign key should set NULL on updates and deletes.
    item_desc and rate should not accept NULL.

For example:
Test 	Result

INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;

	

item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700

```

**Output:**

<img width="1127" height="283" alt="image" src="https://github.com/user-attachments/assets/3a2dcd3e-9e86-43f3-a2ed-0e5350399bcc" />


**Question 5**
---
-- Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

For example:
Test 	Result

select * from Employee;

	

EmployeeID  Name        Department  Salary
----------  ----------  ----------  ----------
201         John Doe    HR          50000
202         Jane Smith  Engineerin  75000
203         Emily Davi  Marketing   60000


```sql
-- Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

For example:
Test 	Result

select * from Employee;

	

EmployeeID  Name        Department  Salary
----------  ----------  ----------  ----------
201         John Doe    HR          50000
202         Jane Smith  Engineerin  75000
203         Emily Davi  Marketing   60000

```

**Output:**

<img width="882" height="222" alt="image" src="https://github.com/user-attachments/assets/54f0e7a2-9157-4ca5-a0fb-ae81d127b5d8" />


**Question 6**
---
-- Create a table named Invoices with the following constraints:

    InvoiceID as INTEGER should be the primary key.
    InvoiceDate as DATE.
    Amount as REAL should be greater than 0.
    DueDate as DATE should be greater than the InvoiceDate.
    OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

For example:
Test 	Result

INSERT INTO Orders (OrderID, OrderDate, CustomerID) VALUES (1, '2024-08-01', 1);
INSERT INTO Invoices (InvoiceID, InvoiceDate, Amount, DueDate, OrderID) VALUES (1, '2024-08-01', 100.0, '2024-09-01', 1);
SELECT * FROM Invoices;

	

InvoiceID   InvoiceDate  Amount      DueDate     OrderID
----------  -----------  ----------  ----------  ----------
1           2024-08-01   100.0       2024-09-01  1


```sql
-- CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    Amount REAL CHECK (Amount > 0),
    DueDate DATE CHECK (DueDate > InvoiceDate),
    OrderID INTEGER,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1312" height="235" alt="image" src="https://github.com/user-attachments/assets/a42cdc45-8b51-4b07-816c-63a226e9c95c" />


**Question 7**
---
-- Create a table named Locations with the following columns:

    LocationID as INTEGER
    LocationName as TEXT
    Address as TEXT

For example:
Test 	Result

pragma table_info('Locations');

	

cid       name             type        notnull     dflt_value  pk
--------  ---------------  ----------  ----------  ----------  ----------
0         LocationID       INTEGER     0                       0
1         LocationName     TEXT        0                       0
2         Address          TEXT        0                       0


```sql
-- CREATE TABLE Locations (
    LocationID INTEGER,
    LocationName TEXT,
    Address TEXT
);
```

**Output:**

<img width="1321" height="312" alt="image" src="https://github.com/user-attachments/assets/10ca96ed-8d69-4b58-99f6-c05cda14223f" />


**Question 8**
---
-- Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).

For example:
Test 	Result

pragma table_info('employee');

	

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          integer     0                       0
1           salary      number      0                       0
2           designatio  varchar(50  0                       0


```sql
-- ALTER TABLE employee
ADD COLUMN designation varchar(50);
```

**Output:**

<img width="1210" height="245" alt="image" src="https://github.com/user-attachments/assets/352bca57-bdb3-42a0-b8e9-a391ba1a2a60" />


**Question 9**
---
-- Create a table named Invoices with the following constraints:

    InvoiceID as INTEGER should be the primary key.
    InvoiceDate as DATE.
    DueDate as DATE should be greater than the InvoiceDate.
    Amount as REAL should be greater than 0.

For example:
Test 	Result

INSERT INTO Invoices (InvoiceID, InvoiceDate)
VALUES (1, '2024-08-08'),(1,'2024-09-08');

	

Error: UNIQUE constraint failed: Invoices.InvoiceID


```sql
-- CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    DueDate DATE CHECK (DueDate > InvoiceDate),
    Amount REAL CHECK (Amount > 0)
);
```

**Output:**

<img width="1065" height="228" alt="image" src="https://github.com/user-attachments/assets/e7eb60af-e5bb-4db7-b594-d32eec2b6df9" />


**Question 10**
---
-- In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

ProductID   Name              Category    Price       Stock
----------  ---------------   ----------  ----------  ----------
106         Fitness Tracker   Wearables
107         Laptop            Electronics  999.99      50
108         Wireless Earbuds  Accessories              100

 

For example:
Test 	Result

SELECT * FROM Products;

	

ProductID   Name             Category    Price       Stock
----------  ---------------  ----------  ----------  ----------
106         Fitness Tracker  Wearables
107         Laptop           Electronic  999.99      50
108         Wireless Earbud  Accessorie              100


```sql
-- INSERT INTO Products (ProductID, Name, Category, Price, Stock)
VALUES (106, 'Fitness Tracker', 'Wearables', NULL, NULL);

INSERT INTO Products (ProductID, Name, Category, Price, Stock)
VALUES (107, 'Laptop', 'Electronics', 999.99, 50);

INSERT INTO Products (ProductID, Name, Category, Price, Stock)
VALUES (108, 'Wireless Earbuds', 'Accessories', NULL, 100);
```

**Output:**

<img width="1191" height="242" alt="image" src="https://github.com/user-attachments/assets/9e8b6b81-1bae-45f1-b190-a0b64304706e" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

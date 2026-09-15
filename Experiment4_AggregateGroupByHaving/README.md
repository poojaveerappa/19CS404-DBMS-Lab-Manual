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
-- How many medical records are there for each patient?

Sample table:MedicalRecords Table

For example:
Result

PatientID   TotalRecords
----------  ------------
4           4
5           1
6           1
7           1
8           1
10          2


```sql
-- SELECT PatientID,
       COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

<img width="613" height="731" alt="image" src="https://github.com/user-attachments/assets/a7549ffb-2ac5-4134-96d0-401b733c297c" />

**Question 2**
---
-- What is the most common diagnosis among patients?

Sample table:MedicalRecords Table

For example:
Result

Diagnosis              DiagnosisCount
---------------------  --------------
Childhood vaccination  3


```sql
-- SELECT Diagnosis,
       COUNT(*) AS DiagnosisCount
FROM MedicalRecords
GROUP BY Diagnosis
ORDER BY DiagnosisCount DESC
LIMIT 1;
```

**Output:**

<img width="847" height="382" alt="image" src="https://github.com/user-attachments/assets/cd0b8e57-2cb3-40e5-b4a2-8aaed16e4e32" />


**Question 3**
---
-- How many prescriptions were written by each doctor?

Sample tablePrescriptions Table

For example:
Result

DoctorID    TotalPrescriptions
----------  ------------------
1           1
2           1
3           1
4           1
5           1
6           1
7           1
8           1
9           1
10          1


```sql
-- SELECT DoctorID,
       COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY DoctorID;
```

**Output:**

<img width="686" height="817" alt="image" src="https://github.com/user-attachments/assets/5161f338-5db8-490d-95da-b72afe95539f" />


**Question 4**
---
--Write a SQL query to Calculate the average income of the employees with names starting with 'A': 

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

For example:
Result

avg_income
----------
5000000.0


```sql
-- SELECT AVG(income) AS avg_income
FROM employee
WHERE name LIKE 'A%';
```

**Output:**

<img width="415" height="388" alt="image" src="https://github.com/user-attachments/assets/eea0c342-856c-4c42-9f95-1fe4058cf2db" />


**Question 5**
---
-- Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

For example:
Result

avg_name_length
---------------
10.0


```sql
-- SELECT AVG(LENGTH(name)) AS avg_name_length
FROM customer
WHERE city = 'Chennai';
```

**Output:**

<img width="515" height="381" alt="image" src="https://github.com/user-attachments/assets/56165a92-09c4-472e-9023-600e062069f7" />


**Question 6**
---
--Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

For example:
Result

employees_count
---------------
8


```sql
-- SELECT COUNT(*) AS employees_count
FROM employee
WHERE income > 50000;
```

**Output:**

<img width="493" height="370" alt="image" src="https://github.com/user-attachments/assets/b4cb021a-fbaa-4a27-aaec-7725e121f88d" />


**Question 7**
---
-- Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

For example:
Result

age_difference
--------------
13


```sql
-- SELECT MAX(age) - MIN(age) AS age_difference
FROM employee;
```

**Output:**

<img width="450" height="375" alt="image" src="https://github.com/user-attachments/assets/f3c7daef-b8e6-4c9d-9657-aa333a203b31" />


**Question 8**
---
-- Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee

For example:
Result

age         Income
----------  ----------
32          200000
40          350000
45          450000


```sql
-- SELECT age,
       MIN(income) AS Income
FROM employee
GROUP BY age
HAVING MIN(income) < 1000000;
```

**Output:**

<img width="550" height="498" alt="image" src="https://github.com/user-attachments/assets/2d1df1f5-49c7-4734-890e-9dcd5f922f7f" />


**Question 9**
---
-- Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1

For example:
Result

jdate       MAX(workhour)
----------  -------------
2004.0      15
2006.0      15


```sql
-- SELECT jdate,
       MAX(workhour)
FROM employee1
GROUP BY jdate
HAVING MAX(workhour) > 12;
```

**Output:**

<img width="618" height="442" alt="image" src="https://github.com/user-attachments/assets/9c177164-5c4d-4708-874b-76e351b3c49a" />


**Question 10**
---
-- Write the SQL query that performs grouping by age groups and displays the maximum salary for each group, excluding groups where the maximum salary is not greater than 8000. 

Note: Calculate the age group as multiples of 5.

Eg., 20,22,23 comes in age group 20. 

25,27,29 comes in age group 25.

Sample table: customer1

For example:
Result

age_group   MAX(salary)
----------  -----------
20          10000
25          8500


```sql
-- SELECT (age/5)*5 AS age_group,
       MAX(salary)
FROM customer1
GROUP BY (age/5)*5
HAVING MAX(salary) > 8000;
```

**Output:**

<img width="581" height="427" alt="image" src="https://github.com/user-attachments/assets/a9ce33af-a937-4b3d-8254-6729564e5f3d" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

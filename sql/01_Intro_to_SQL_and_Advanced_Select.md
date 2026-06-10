# Intro to SQL and Advance Select

SQL (Structured Query Language) is the standard language used to interact with relational databases. 
It helps you:
- Store data
- Retrieve data
- Update data
- Delete data
- Manage database structures
Common databases that use SQL include MySQL, PostgreSQL, Microsoft SQL Server, and Oracle Database.

# Basic Database Example:

| StudentID | Name  | Age | City    |
| --------- | ----- | --- | ------- |
| 1         | Ravi  | 20  | Chennai |
| 2         | Priya | 21  | Mumbai  |
| 3         | Arun  | 19  | Chennai |


## Basic SELECT Statement:
The `SELECT` statement is used to retrieve data from a table.

```
SELECT Name, Age
FROM Students;
```

## SELECT All Columns

```
SELECT *
FROM Students;
```

`*` means all columns

## Advanced SELECT Concepts

1. `WHERE` Clause
Filters records based on a condition.

```
SELECT *
FROM Students
WHERE City = 'Chennai';
```

2. Comparison Operators

| Operator | Meaning               |
| -------- | --------------------- |
| =        | Equal                 |
| <> or != | Not Equal             |
| >        | Greater Than          |
| <        | Less Than             |
| >=       | Greater Than or Equal |
| <=       | Less Than or Equal    |

```
SELECT *
FROM Students
WHERE Age > 20;
```

3. AND, OR, NOT

```
SELECT *
FROM Students
WHERE City = 'Chennai'
AND Age > 19;
```

```
SELECT *
FROM Students
WHERE City = 'Chennai'
OR Age > 20;
```

```
SELECT *
FROM Students
WHERE NOT City = 'Mumbai';
```

4. ORDER BY
Sorts the result.

```
SELECT *
FROM Students
ORDER BY Age ASC;
```

```
SELECT *
FROM Students
ORDER BY Age DESC;
```

5. DISTINCT
Removes duplicate values.

```
SELECT DISTINCT City
FROM Students;
```

6. LIMIT / TOP
Returns a specific number of rows.

MySQL/PostgreSQL
```
SELECT *
FROM Students
LIMIT 2;
```

SQL Server
```
SELECT TOP 2 *
FROM Students;
```

7. IN Operator
Checks multiple values.

```
SELECT *
FROM Students
WHERE City IN ('Chennai', 'Mumbai');
```

8. BETWEEN
Range search.

```
SELECT *
FROM Students
WHERE Age BETWEEN 18 AND 21;
```

9. LIKE Operator
Pattern matching.

- Starts with A
```
SELECT *
FROM Students
WHERE Name LIKE 'A%';
```

- Ends with i
```
SELECT *
FROM Students
WHERE Name LIKE '%i';
```

- Contains ru
```
SELECT *
FROM Students
WHERE Name LIKE '%ru%';
```

| Symbol | Meaning                  |
| ------ | ------------------------ |
| %      | Any number of characters |
| _      | One character            |

10. Aliases (AS)
Rename columns temporarily.
```
SELECT Name AS StudentName,
       Age AS StudentAge
FROM Students;
```

11. Aggregate Functions

- COUNT
```
SELECT COUNT(*) AS TotalStudents
FROM Students;
```

- SUM
```
SELECT SUM(Age)
FROM Students;
```

- AVG
```
SELECT AVG(Age)
FROM Students;
```

- MAX
```
SELECT MAX(Age)
FROM Students;
```

- MIN
```
SELECT MIN(Age)
FROM Students;
```

12. GROUP BY
Groups records.
```
SELECT City,
       COUNT(*) AS TotalStudents
FROM Students
GROUP BY City;
```

13. HAVING
Filters grouped results.
```
SELECT City,
       COUNT(*) AS TotalStudents
FROM Students
GROUP BY City
HAVING COUNT(*) > 1;
```

14. Subqueries
Query inside another query.
```
SELECT *
FROM Students
WHERE Age >
(
    SELECT AVG(Age)
    FROM Students
);
```

15. JOIN with SELECT

students 
| StudentID | Name  |
| --------- | ----- |
| 1         | Ravi  |
| 2         | Priya |

marks
| StudentID | Marks |
| --------- | ----- |
| 1         | 85    |
| 2         | 90    |

```
SELECT S.Name,
       M.Marks
FROM Students S
INNER JOIN Marks M
ON S.StudentID = M.StudentID;
```

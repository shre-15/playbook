## Subqueries in SQL

A Subquery (also called a Nested Query or Inner Query) is a query written inside another SQL query.

The inner query executes first, and its result is used by the outer query.

Why Use Subqueries?

Subqueries are useful when:
- You need the result of one query to build another query.
- You want to compare values against aggregated data.
- You need filtering based on another table.
- You want to avoid complex joins in some cases.

Basic Syntax
```
SELECT column_name
FROM table_name
WHERE column_name OPERATOR
(
    SELECT column_name
    FROM table_name
);
```
Execution Flow:
- Inner Query Executes
- Result Returned
- Outer Query Uses Result

Students:
| StudentID | Name  | Age |
| --------- | ----- | --- |
| 1         | Ravi  | 20  |
| 2         | Priya | 21  |
| 3         | Arun  | 19  |
| 4         | Kiran | 22  |

Types of Subqueries
1. Single Row Subquery

Returns exactly one value.

Example: Find Students Older Than Average Age
```
SELECT *
FROM Students
WHERE Age >
(
    SELECT AVG(Age)
    FROM Students
);
```
Step 1: Inner Query
```
SELECT AVG(Age)
FROM Students;
```
Output:
| AVG(Age) |
| -------- |
| 20.5     |

Step 2: Outer Query
```
SELECT *
FROM Students
WHERE Age > 20.5;
```
Output:
| StudentID | Name  | Age |
| --------- | ----- | --- |
| 2         | Priya | 21  |
| 4         | Kiran | 22  |

2. Multiple Row Subquery

Returns multiple rows.

Students:
| StudentID | Name  | City    |
| --------- | ----- | ------- |
| 1         | Ravi  | Chennai |
| 2         | Priya | Mumbai  |
| 3         | Arun  | Chennai |
| 4         | Kiran | Delhi   |

Find students from Chennai or Mumbai.
```
SELECT *
FROM Students
WHERE City IN
(
    SELECT City
    FROM Students
    WHERE City IN ('Chennai','Mumbai')
);
```
Output:
| Name  | City    |
| ----- | ------- |
| Ravi  | Chennai |
| Priya | Mumbai  |
| Arun  | Chennai |

3. Subquery with IN

Used when the inner query returns multiple values.

Employees:
| EmpID | DepartmentID |
| ----- | ------------ |
| 1     | 101          |
| 2     | 102          |
| 3     | 101          |

Department:
| DepartmentID | DepartmentName |
| ------------ | -------------- |
| 101          | HR             |
| 102          | IT             |

Find employees belonging to HR.
```
SELECT *
FROM Employees
WHERE DepartmentID IN
(
    SELECT DepartmentID
    FROM Departments
    WHERE DepartmentName = 'HR'
);
```
Output:
| EmpID | DepartmentID |
| ----- | ------------ |
| 1     | 101          |
| 3     | 101          |

4. Subquery with EXISTS

`EXISTS` checks whether the subquery returns any rows.

Orders:
| OrderID | CustomerID |
| ------- | ---------- |
| 1       | 101        |
| 2       | 102        |

Customers:
| CustomerID | Name  |
| ---------- | ----- |
| 101        | Ravi  |
| 102        | Priya |
| 103        | Arun  |

Find customers who have placed orders.

```
SELECT *
FROM Customers C
WHERE EXISTS
(
    SELECT 1
    FROM Orders O
    WHERE O.CustomerID = C.CustomerID
);
```
Output:
| CustomerID | Name  |
| ---------- | ----- |
| 101        | Ravi  |
| 102        | Priya |

5. Correlated Subquery

A correlated subquery depends on the outer query.

Employees:
| EmpID | Name  | Salary | Department |
| ----- | ----- | ------ | ---------- |
| 1     | Ravi  | 50000  | HR         |
| 2     | Priya | 70000  | HR         |
| 3     | Arun  | 60000  | IT         |
| 4     | Kiran | 80000  | IT         |

Find employees earning above their department average.
```
SELECT *
FROM Employees E
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
    WHERE Department = E.Department
);
```
Output:
| EmpID | Name  | Salary | Department |
| ----- | ----- | ------ | ---------- |
| 2     | Priya | 70000  | HR         |
| 4     | Kiran | 80000  | IT         |

Explanation

For each employee:
- Calculate department average
- Compare employee salary with that average

6. Subquery in SELECT Clause

Used to display additional calculated information.

```
SELECT Name,
       Salary,
       (
           SELECT AVG(Salary)
           FROM Employees
       ) AS CompanyAverage
FROM Employees;
```
Output:
| Name  | Salary | CompanyAverage |
| ----- | ------ | -------------- |
| Ravi  | 50000  | 65000          |
| Priya | 70000  | 65000          |
| Arun  | 60000  | 65000          |
| Kiran | 80000  | 65000          |

7. Subquery in FROM Clause

Acts like a temporary table.

```
SELECT *
FROM
(
    SELECT Department,
           AVG(Salary) AS AvgSalary
    FROM Employees
    GROUP BY Department
) DeptSalary;
```
Output:
| Department | AvgSalary |
| ---------- | --------- |
| HR         | 60000     |
| IT         | 70000     |

Subquery vs JOIN

Find Employee Department

Using Subquery:
```
SELECT Name
FROM Employees
WHERE DepartmentID =
(
    SELECT DepartmentID
    FROM Departments
    WHERE DepartmentName = 'HR'
);
```

Using JOIN:
```
SELECT E.Name
FROM Employees E
INNER JOIN Departments D
ON E.DepartmentID = D.DepartmentID
WHERE D.DepartmentName = 'HR';
```

Comparison:
| Subquery                   | JOIN                             |
| -------------------------- | -------------------------------- |
| Easier for simple logic    | Better for complex relationships |
| Can be nested              | Usually faster for large data    |
| Readable for small queries | More flexible                    |
| May be slower              | Often optimized better           |

Execution Order
```
SELECT *
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);
```
Actual Execution:

1. Execute Subquery
2. Get AVG(Salary)
3. Execute Outer Query
4. Return Result

### Quick Revision Table
| Type                  | Description             |
| --------------------- | ----------------------- |
| Single Row Subquery   | Returns one value       |
| Multiple Row Subquery | Returns many rows       |
| IN                    | Checks multiple values  |
| EXISTS                | Checks row existence    |
| Correlated Subquery   | Depends on outer query  |
| SELECT Subquery       | Used in column list     |
| FROM Subquery         | Acts as temporary table |
| ------------------- | ---------------------------- |
| Subquery            | Query inside another query   |
| Nested Query        | Another name for Subquery    |
| IN                  | Works with multiple rows     |
| EXISTS              | Checks row existence         |
| Correlated Subquery | Executes for every outer row |
| FROM Subquery       | Temporary result set         |
| SELECT Subquery     | Returns calculated values    |
| JOIN Alternative    | Sometimes replaces joins     |

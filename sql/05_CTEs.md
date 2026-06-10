## Common Table Expressions (CTEs) in SQL

- A CTE (Common Table Expression) is a temporary named result set that exists only during the execution of a query.
- It makes complex queries easier to read, write, and maintain.

Why Use CTEs?

Without a CTE:
```
SELECT *
FROM (
    SELECT City,
           COUNT(*) AS TotalStudents
    FROM Students
    GROUP BY City
) AS StudentCount
WHERE TotalStudents > 1;
```
With a CTE:
```
WITH StudentCount AS
(
    SELECT City,
           COUNT(*) AS TotalStudents
    FROM Students
    GROUP BY City
)
SELECT *
FROM StudentCount
WHERE TotalStudents > 1;
```
The CTE version is more readable.

Basic Syntax
```
WITH CTE_Name AS
(
    SELECT column1,
           column2
    FROM TableName
)
SELECT *
FROM CTE_Name;
```

Example 1: Simple CTE

students:
| StudentID | Name  | Age |
| --------- | ----- | --- |
| 1         | Ravi  | 20  |
| 2         | Priya | 21  |
| 3         | Arun  | 19  |

Find students older than 20

```
WITH StudentData AS
(
    SELECT *
    FROM Students
)
SELECT *
FROM StudentData
WHERE Age > 20;
```

Output:
| StudentID | Name  | Age |
| --------- | ----- | --- |
| 2         | Priya | 21  |

Example 2: CTE with Aggregation

Find cities having more than one student.
```
WITH CityCount AS
(
    SELECT City,
           COUNT(*) AS TotalStudents
    FROM Students
    GROUP BY City
)
SELECT *
FROM CityCount
WHERE TotalStudents > 1;
```

Example 3: Multiple CTEs

You can define multiple CTEs separated by commas.

```
WITH StudentCount AS
(
    SELECT City,
           COUNT(*) AS TotalStudents
    FROM Students
    GROUP BY City
),
AverageAge AS
(
    SELECT City,
           AVG(Age) AS AvgAge
    FROM Students
    GROUP BY City
)
SELECT S.City,
       S.TotalStudents,
       A.AvgAge
FROM StudentCount S
JOIN AverageAge A
ON S.City = A.City;
```
Output:
| City    | TotalStudents | AvgAge |
| ------- | ------------- | ------ |
| Chennai | 2             | 19.5   |
| Mumbai  | 2             | 20.5   |

Example 4: CTE with JOIN

Students:
| StudentID | Name  |
| --------- | ----- |
| 1         | Ravi  |
| 2         | Priya |

Marks:
| StudentID | Marks |
| --------- | ----- |
| 1         | 85    |
| 2         | 90    |

```
WITH StudentMarks AS
(
    SELECT S.Name,
           M.Marks
    FROM Students S
    INNER JOIN Marks M
    ON S.StudentID = M.StudentID
)
SELECT *
FROM StudentMarks
WHERE Marks > 85;
```

Output:
| Name  | Marks |
| ----- | ----- |
| Priya | 90    |

Recursive CTE

- A Recursive CTE references itself.

Used for:
- Hierarchical data
- Employee-manager relationships
- Organization charts
- Tree structures
- Generating sequences

Recursive CTE Syntax
```
WITH RECURSIVE CTE_Name AS
(
    -- Anchor Query

    SELECT ...

    UNION ALL

    -- Recursive Query

    SELECT ...
    FROM CTE_Name
)
SELECT *
FROM CTE_Name;
```
Parts
1. Anchor Query
- Starting point.
- Executes once.
2. Recursive Query
- References the CTE itself.
- Repeats until no rows are returned.

Example 5: Generate Numbers 1 to 5
```
WITH RECURSIVE Numbers AS
(
    SELECT 1 AS Num

    UNION ALL

    SELECT Num + 1
    FROM Numbers
    WHERE Num < 5
)
SELECT *
FROM Numbers;
```
Output:
| Num |
| --- |
| 1   |
| 2   |
| 3   |
| 4   |
| 5   |

Example 6: Employee Hierarchy
| EmpID | Name  | ManagerID |
| ----- | ----- | --------- |
| 1     | John  | NULL      |
| 2     | Sam   | 1         |
| 3     | David | 1         |
| 4     | Alex  | 2         |

```
WITH RECURSIVE EmployeeTree AS
(
    SELECT EmpID,
           Name,
           ManagerID,
           1 AS Level
    FROM Employees
    WHERE ManagerID IS NULL

    UNION ALL

    SELECT E.EmpID,
           E.Name,
           E.ManagerID,
           ET.Level + 1
    FROM Employees E
    JOIN EmployeeTree ET
      ON E.ManagerID = ET.EmpID
)
SELECT *
FROM EmployeeTree;
```
Output:
| EmpID | Name  | Level |
| ----- | ----- | ----- |
| 1     | John  | 1     |
| 2     | Sam   | 2     |
| 3     | David | 2     |
| 4     | Alex  | 3     |

### CTE vs Subquery
Subquery
```
SELECT *
FROM (
    SELECT City,
           COUNT(*) AS TotalStudents
    FROM Students
    GROUP BY City
) X;
```
CTE
```
WITH CityCount AS
(
    SELECT City,
           COUNT(*) AS TotalStudents
    FROM Students
    GROUP BY City
)
SELECT *
FROM CityCount;
```

| CTE                      | Subquery                   |
| ------------------------ | -------------------------- |
| More readable            | Less readable              |
| Can be reused            | Cannot be reused easily    |
| Supports recursion       | Does not support recursion |
| Easier for complex logic | Harder to maintain         |

CTE vs Temporary Table
| CTE                  | Temporary Table                  |
| -------------------- | -------------------------------- |
| Exists for one query | Exists for session/transaction   |
| No physical storage  | Stored temporarily in database   |
| Good for readability | Good for large intermediate data |
| Supports recursion   | No recursion                     |


### Quick Revision Table
| Concept         | Description                         |
| --------------- | ----------------------------------- |
| CTE             | Temporary named result set          |
| WITH            | Keyword used to create a CTE        |
| Recursive CTE   | CTE that references itself          |
| Anchor Query    | Starting query in recursion         |
| Recursive Query | Repeated query in recursion         |
| UNION ALL       | Combines anchor and recursive parts |
| Scope           | Only for the next query             |


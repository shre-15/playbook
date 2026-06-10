## Sorting and Grouping

Sorting and Grouping are used to organize and summarize data effectively.

students:
| StudentID | Name  | Age | City    |
| --------- | ----- | --- | ------- |
| 1         | Ravi  | 20  | Chennai |
| 2         | Priya | 21  | Mumbai  |
| 3         | Arun  | 19  | Chennai |
| 4         | Kiran | 21  | Delhi   |
| 5         | Meena | 20  | Mumbai  |

1. ORDER BY (Sorting Data)

- The ORDER BY clause is used to sort records in ascending or descending order.

Sort by Age (Ascending)
```
SELECT *
FROM Students
ORDER BY Age ASC;
```

Output:
| Name  | Age |
| ----- | --- |
| Arun  | 19  |
| Ravi  | 20  |
| Meena | 20  |
| Priya | 21  |
| Kiran | 21  |

Sort by Age (Descending)
```
SELECT *
FROM Students
ORDER BY Age DESC;
```

Output:
| Name  | Age |
| ----- | --- |
| Priya | 21  |
| Kiran | 21  |
| Ravi  | 20  |
| Meena | 20  |
| Arun  | 19  |

Sort by Multiple Columns

First sorts by City, then by Name.

```
SELECT *
FROM Students
ORDER BY City ASC, Name ASC;
```

Output:
| Name  | City    |
| ----- | ------- |
| Arun  | Chennai |
| Ravi  | Chennai |
| Kiran | Delhi   |
| Meena | Mumbai  |
| Priya | Mumbai  |

Sort Using Column Position

```
SELECT Name, Age, City
FROM Students
ORDER BY 2 DESC;
```

Explanation:
- Column 1 → Name
- Column 2 → Age
- Column 3 → City
- Sorts by Age descending.

Sort with WHERE Clause

```
SELECT *
FROM Students
WHERE City = 'Mumbai'
ORDER BY Age DESC;
```

Output:
| Name  | Age | City   |
| ----- | --- | ------ |
| Priya | 21  | Mumbai |
| Meena | 20  | Mumbai |

2. GROUP BY (Grouping Data)

`GROUP BY` combines rows having the same value into groups.
 
Usually used with aggregate functions such as:
- COUNT()
- SUM()
- AVG()
- MAX()
- MIN()

Count Students in Each City
```
SELECT City,
       COUNT(*) AS TotalStudents
FROM Students
GROUP BY City;
```

Output:
| City    | TotalStudents |
| ------- | ------------- |
| Chennai | 2             |
| Mumbai  | 2             |
| Delhi   | 1             |

Average Age by City

```
SELECT City,
       AVG(Age) AS AverageAge
FROM Students
GROUP BY City;
```

Output:
| City    | AverageAge |
| ------- | ---------- |
| Chennai | 19.5       |
| Mumbai  | 20.5       |
| Delhi   | 21         |

Maximum Age by City

```
SELECT City,
       MAX(Age) AS OldestStudent
FROM Students
GROUP BY City;
```

Output:
| City    | OldestStudent |
| ------- | ------------- |
| Chennai | 20            |
| Mumbai  | 21            |
| Delhi   | 21            |

Sum of Ages by City

```
SELECT City,
       SUM(Age) AS TotalAge
FROM Students
GROUP BY City;
```

Output:
| City    | TotalAge |
| ------- | -------- |
| Chennai | 39       |
| Mumbai  | 41       |
| Delhi   | 21       |

3. HAVING Clause

`HAVING` filters grouped results.

Difference between `WHERE` and `HAVING` ?
| WHERE                                   | HAVING                        |
| --------------------------------------- | ----------------------------- |
| Filters rows before grouping            | Filters groups after grouping |
| Cannot use aggregate functions directly | Can use aggregate functions   |

Find Cities Having More Than 1 Student
```
SELECT City,
       COUNT(*) AS TotalStudents
FROM Students
GROUP BY City
HAVING COUNT(*) > 1;
```

Output:
| City    | TotalStudents |
| ------- | ------------- |
| Chennai | 2             |
| Mumbai  | 2             |

Find Cities with Average Age Greater Than 20
```
SELECT City,
       AVG(Age) AS AverageAge
FROM Students
GROUP BY City
HAVING AVG(Age) > 20;
```

Output:
| City   | AverageAge |
| ------ | ---------- |
| Mumbai | 20.5       |
| Delhi  | 21         |

4. WHERE + GROUP BY + HAVING + ORDER BY Together

A common interview pattern.
```
SELECT City,
       COUNT(*) AS TotalStudents
FROM Students
WHERE Age >= 20
GROUP BY City
HAVING COUNT(*) > 0
ORDER BY TotalStudents DESC;
```

Execution Order:
- WHERE
- GROUP BY
- HAVING
- SELECT
- ORDER BY

Example with Sales Table

sales:
| SaleID | Product | Amount |
| ------ | ------- | ------ |
| 1      | Laptop  | 50000  |
| 2      | Mobile  | 20000  |
| 3      | Laptop  | 60000  |
| 4      | Mobile  | 15000  |
| 5      | Tablet  | 10000  |

Total Sales per Product:

```
SELECT Product,
       SUM(Amount) AS TotalSales
FROM Sales
GROUP BY Product;
```

Output:
| Product | TotalSales |
| ------- | ---------- |
| Laptop  | 110000     |
| Mobile  | 35000      |
| Tablet  | 10000      |

Products with Sales Greater Than 30000

```
SELECT Product,
       SUM(Amount) AS TotalSales
FROM Sales
GROUP BY Product
HAVING SUM(Amount) > 30000;
```
Output:
| Product | TotalSales |
| ------- | ---------- |
| Laptop  | 110000     |
| Mobile  | 35000      |

### Quick Revision Table
| Clause   | Purpose                     |
| -------- | --------------------------- |
| ORDER BY | Sort records                |
| ASC      | Ascending order             |
| DESC     | Descending order            |
| GROUP BY | Group similar values        |
| COUNT()  | Count rows                  |
| SUM()    | Add values                  |
| AVG()    | Average value               |
| MAX()    | Highest value               |
| MIN()    | Lowest value                |
| HAVING   | Filter grouped results      |
| WHERE    | Filter rows before grouping |

### Execution Order of a SELECT Query
```
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT;
```

### Actual SQL execution order:
```
FROM
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
LIMIT;
```

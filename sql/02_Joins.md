## SQL JOINS

A JOIN combines rows from two or more tables based on a related column.

Why Use Joins?
Suppose you have two tables:

students:
| StudentID | Name  |
| --------- | ----- |
| 1         | Ravi  |
| 2         | Priya |
| 3         | Arun  |

marks:
| StudentID | Marks |
| --------- | ----- |
| 1         | 85    |
| 2         | 90    |
| 4         | 75    |


1. INNER JOIN

Returns only matching records from both tables.

```
SELECT S.StudentID,
       S.Name,
       M.Marks
FROM Students S
INNER JOIN Marks M
ON S.StudentID = M.StudentID;
```

Output:

| StudentID | Name  | Marks |
| --------- | ----- | ----- |
| 1         | Ravi  | 85    |
| 2         | Priya | 90    |

Explanation:
- StudentID 1 and 2 exist in both tables.
- StudentID 3 and 4 are excluded.

2. LEFT JOIN (LEFT OUTER JOIN)

Returns:
- All records from the left table
- Matching records from the right table
- NULL if no match exists

```
SELECT S.StudentID,
       S.Name,
       M.Marks
FROM Students S
LEFT JOIN Marks M
ON S.StudentID = M.StudentID;
```

Output:
| StudentID | Name  | Marks |
| --------- | ----- | ----- |
| 1         | Ravi  | 85    |
| 2         | Priya | 90    |
| 3         | Arun  | NULL  |

Explanation:
- All students are shown.
- Arun has no marks record, so Marks = NULL.

3. RIGHT JOIN (RIGHT OUTER JOIN)

Returns:
- All records from the right table
- Matching records from the left table
- NULL if no match exists

```
SELECT S.StudentID,
       S.Name,
       M.Marks
FROM Students S
RIGHT JOIN Marks M
ON S.StudentID = M.StudentID;
```

Output:
| StudentID | Name  | Marks |
| --------- | ----- | ----- |
| 1         | Ravi  | 85    |
| 2         | Priya | 90    |
| NULL      | NULL  | 75    |

Explanation:
- StudentID 4 exists only in Marks.
- Student details become NULL.

4. FULL OUTER JOIN

Returns:
- All records from both tables
- Matching rows where possible
- NULL where no match exists

```
SELECT S.StudentID,
       S.Name,
       M.Marks
FROM Students S
FULL OUTER JOIN Marks M
ON S.StudentID = M.StudentID;
```

Output:
| StudentID | Name  | Marks |
| --------- | ----- | ----- |
| 1         | Ravi  | 85    |
| 2         | Priya | 90    |
| 3         | Arun  | NULL  |
| NULL      | NULL  | 75    |

5. CROSS JOIN

Returns every combination of rows.

students:
| Name  |
| ----- |
| Ravi  |
| Priya |

courses:
| Course |
| ------ |
| SQL    |
| Python |

```
SELECT S.Name,
       C.Course
FROM Students S
CROSS JOIN Courses C;
```

Output:
| Name  | Course |
| ----- | ------ |
| Ravi  | SQL    |
| Ravi  | Python |
| Priya | SQL    |
| Priya | Python |

formula: Rows = Table1 Rows × Table2 Rows

6. SELF JOIN

A table joins itself.

employees:
| EmpID | Name  | ManagerID |
| ----- | ----- | --------- |
| 1     | John  | NULL      |
| 2     | Sam   | 1         |
| 3     | David | 1         |

```
SELECT E.Name AS Employee,
       M.Name AS Manager
FROM Employees E
LEFT JOIN Employees M
ON E.ManagerID = M.EmpID;
```

Output:
| Employee | Manager |
| -------- | ------- |
| John     | NULL    |
| Sam      | John    |
| David    | John    |


7. Multiple Table Join Example

students:
| StudentID | Name |
| --------- | ---- |
| 1         | Ravi |

marks:
| StudentID | SubjectID | Marks |
| --------- | --------- | ----- |
| 1         | 101       | 85    |

subjects:
| SubjectID | SubjectName |
| --------- | ----------- |
| 101       | SQL         |


```
SELECT S.Name,
       Sub.SubjectName,
       M.Marks
FROM Students S
INNER JOIN Marks M
ON S.StudentID = M.StudentID
INNER JOIN Subjects Sub
ON M.SubjectID = Sub.SubjectID;
```

Output:
| Name | SubjectName | Marks |
| ---- | ----------- | ----- |
| Ravi | SQL         | 85    |


### Quick Revision Table

| Join Type  | Returns                   |
| ---------- | ------------------------- |
| INNER JOIN | Matching rows only        |
| LEFT JOIN  | All left + matching right |
| RIGHT JOIN | All right + matching left |
| FULL JOIN  | All rows from both tables |
| CROSS JOIN | Every combination         |
| SELF JOIN  | Table joined with itself  |


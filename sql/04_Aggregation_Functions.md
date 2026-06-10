## Aggregation Functions in SQL

- Aggregation functions perform calculations on multiple rows and return a single result.
- They are commonly used with GROUP BY to summarize data.

students:
| StudentID | Name  | Age | City    |
| --------- | ----- | --- | ------- |
| 1         | Ravi  | 20  | Chennai |
| 2         | Priya | 21  | Mumbai  |
| 3         | Arun  | 19  | Chennai |
| 4         | Kiran | 21  | Delhi   |
| 5         | Meena | 20  | Mumbai  |

What is Aggregation?
- Aggregation means combining multiple values into a single value.

Example:

Ages = 20, 21, 19, 21, 20

- SUM → 101
- AVG → 20.2
- MAX → 21
- MIN → 19
- COUNT → 5

Common Aggregate Functions:
| Function | Purpose       |
| -------- | ------------- |
| COUNT()  | Count rows    |
| SUM()    | Add values    |
| AVG()    | Average value |
| MAX()    | Highest value |
| MIN()    | Lowest value  |

### Quick Revision Table
| Function               | Description           |
| ---------------------- | --------------------- |
| COUNT(*)               | Count all rows        |
| COUNT(column)          | Count non-NULL values |
| COUNT(DISTINCT column) | Count unique values   |
| SUM()                  | Total of values       |
| AVG()                  | Average value         |
| MAX()                  | Largest value         |
| MIN()                  | Smallest value        |


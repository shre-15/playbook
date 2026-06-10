## Advanced String Functions and Regular Expressions (Regex) in SQL

String functions are used to manipulate, format, search, and analyze text data stored in database columns.

They are commonly used for:

1. Data cleaning
2. Data validation
3. Text formatting
4. Searching patterns
5. Reporting
6. Data transformation

Employees:
| EmpID | Name         | Email                                         | City    |
| ----- | ------------ | --------------------------------------------- | ------- |
| 1     | Ravi Kumar   | [ravi@gmail.com](mailto:ravi@gmail.com)       | Chennai |
| 2     | Priya Sharma | [priya@yahoo.com](mailto:priya@yahoo.com)     | Mumbai  |
| 3     | Arun Raj     | [arun@gmail.com](mailto:arun@gmail.com)       | Chennai |
| 4     | Kiran Das    | [kiran@outlook.com](mailto:kiran@outlook.com) | Delhi   |

Common String Functions

1. UPPER()

Converts text to uppercase.
```
SELECT Name,
       UPPER(Name) AS UpperName
FROM Employees;
```
Output:
| Name         | UpperName    |
| ------------ | ------------ |
| Ravi Kumar   | RAVI KUMAR   |
| Priya Sharma | PRIYA SHARMA |

2. LOWER()

Converts text to lowercase.

```
SELECT Name,
       LOWER(Name) AS LowerName
FROM Employees;
```
Output:
| Name         | LowerName    |
| ------------ | ------------ |
| Ravi Kumar   | ravi kumar   |
| Priya Sharma | priya sharma |

3. LENGTH() / LEN()

Returns number of characters.

MySQL/PostgreSQL:
```
SELECT LENGTH(Name)
FROM Employees;
```
SQL Server:
```
SELECT LEN(Name)
FROM Employees;
```
Output:
| Name         | Length |
| ------------ | ------ |
| Ravi Kumar   | 10     |
| Priya Sharma | 13     |

4. CONCAT()

Combines multiple strings.
```
SELECT CONCAT(Name,' - ',City) AS EmployeeInfo
FROM Employees;
```
Output:
| EmployeeInfo          |
| --------------------- |
| Ravi Kumar - Chennai  |
| Priya Sharma - Mumbai |

5. SUBSTRING()

Extracts part of a string.

```
SELECT Name,
       SUBSTRING(Name,1,4)
FROM Employees;
```
Output:
| Name         | Result |
| ------------ | ------ |
| Ravi Kumar   | Ravi   |
| Priya Sharma | Priy   |

6. LEFT()

Returns characters from left side.

```
SELECT LEFT(Name,3)
FROM Employees;
```
Output:
| Result |
| ------ |
| Rav    |
| Pri    |

7. RIGHT()

Returns characters from right side.

```
SELECT RIGHT(Name,5)
FROM Employees;
```
Output:
| Result |
| ------ |
| Kumar  |
| harma  |

8. TRIM()

Removes spaces from both sides.

```
SELECT TRIM('   Ravi   ');
```
Output:

Ravi

9. LTRIM()

Removes left spaces.

```
SELECT LTRIM('   Ravi');
```

Output:

Ravi

10. RTRIM()

Removes right spaces.
```
SELECT RTRIM('Ravi   ');
```
Output:

Ravi

11. REPLACE()

Replaces text.
```
SELECT REPLACE(Name,'Ravi','Ravikumar')
FROM Employees;
```
Output:

Ravikumar Kumar

12. REVERSE()

Reverses string.
```
SELECT REVERSE(Name)
FROM Employees;
```
Output:

ramuK ivaR

13. POSITION() / CHARINDEX()

Finds location of a string.

PostgreSQL:
```
SELECT POSITION('@' IN Email)
FROM Employees;
```
SQL Server:
```
SELECT CHARINDEX('@',Email)
FROM Employees;
```
Output:
| Email                                   | Position |
| --------------------------------------- | -------- |
| [ravi@gmail.com](mailto:ravi@gmail.com) | 5        |


LIKE Clause

Used for pattern matching.

```
SELECT *
FROM Employees
WHERE column_name LIKE pattern;
```
Wildcards
| Symbol | Meaning                  |
| ------ | ------------------------ |
| %      | Any number of characters |
| _      | Exactly one character    |


Regular Expressions (REGEXP / RLIKE)

Regex provides advanced pattern matching beyond LIKE.

Why Regex?

LIKE can only do simple matching.

Regex can:

- Validate email
- Validate phone numbers
- Extract patterns
- Find special characters
- Match exact formats

MySQL:
```
SELECT *
FROM Employees
WHERE Name REGEXP 'pattern';
```
PostgreSQL:
```
SELECT *
FROM Employees
WHERE Name ~ 'pattern';
```
Regex Meta Characters
| Symbol | Meaning              |
| ------ | -------------------- |
| ^      | Start of string      |
| $      | End of string        |
| .      | Any single character |
| *      | Zero or more         |
| +      | One or more          |
| ?      | Optional             |
| []     | Character range      |
| |      | OR                   |
| ()     | Grouping             |

Execution Order
```
SELECT *
FROM Employees
WHERE Email REGEXP '@gmail\.com$';
```
Actual Execution:

1. FROM Employees
2. Apply REGEXP Filter
3. Return Matching Rows

### Quick Revision Table
| Function         | Purpose                   |
| ---------------- | ------------------------- |
| UPPER()          | Convert to uppercase      |
| LOWER()          | Convert to lowercase      |
| LENGTH()         | Count characters          |
| CONCAT()         | Join strings              |
| SUBSTRING()      | Extract text              |
| LEFT()           | Left characters           |
| RIGHT()          | Right characters          |
| TRIM()           | Remove spaces             |
| REPLACE()        | Replace text              |
| REVERSE()        | Reverse string            |
| LIKE             | Simple pattern matching   |
| REGEXP           | Advanced pattern matching |
| REGEXP_REPLACE() | Replace using regex       |
| REGEXP_SUBSTR()  | Extract pattern           |
| REGEXP_COUNT()   | Count matches             |

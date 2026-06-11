# Control Flow

## Conditional Statements

### if

```python
age = 20

if age >= 18:
    print("Eligible")
```

---

### if else

```python
if age >= 18:
    print("Eligible")
else:
    print("Not Eligible")
```

---

### if elif else

```python
marks = 85

if marks >= 90:
    print("A")
elif marks >= 80:
    print("B")
else:
    print("C")
```

---

# Loops

## for Loop

```python
for i in range(5):
    print(i)
```

Output:

```python
0
1
2
3
4
```

---

## while Loop

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

---

## break

```python
for i in range(10):
    if i == 5:
        break
```

---

## continue

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

---

# Interview Questions

## Q1: Difference between break and continue?

break:

Stops loop completely.

continue:

Skips current iteration.

---

## Q2: What is pass?

Placeholder statement.

```python
if True:
    pass
```
# Functions

Function is a reusable block of code.

## Creating Function

```python
def greet():
    print("Hello")
```

Calling:

```python
greet()
```

---

# Parameters

```python
def greet(name):
    print(name)
```

---

# Return Statement

```python
def add(a,b):
    return a+b
```

---

# Default Arguments

```python
def greet(name="Guest"):
    print(name)
```

---

# *args

```python
def total(*numbers):
    return sum(numbers)
```

---

# **kwargs

```python
def info(**data):
    print(data)
```

---

# Lambda Function

Anonymous function.

```python
square = lambda x: x*x

print(square(5))
```

Output:

```python
25
```

---

# Interview Questions

## Q1: Difference between parameter and argument?

Parameter:

```python
def add(a,b)
```

Argument:

```python
add(10,20)
```

---

## Q2: What is recursion?

Function calling itself.

```python
def factorial(n):
    if n==1:
        return 1
    return n * factorial(n-1)
```
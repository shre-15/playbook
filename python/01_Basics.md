# Python Basics

## What is Python?

Python is a high-level, interpreted, object-oriented programming language.

Features:

- Easy to learn
- Platform independent
- Open source
- Huge library ecosystem
- Supports OOP

---

# Variables

A variable stores data.

```python
name = "John"
age = 25
salary = 50000
```

Rules:

- Cannot start with a number
- Case-sensitive
- Use meaningful names

Valid:

```python
student_name = "Alex"
```

Invalid:

```python
2name = "Alex"
```

---

# Data Types

## Integer

```python
x = 10
```

## Float

```python
price = 99.99
```

## String

```python
name = "Python"
```

## Boolean

```python
is_active = True
```

## Complex

```python
x = 3 + 4j
```

---

# Type Checking

```python
x = 10

print(type(x))
```

Output:

```python
<class 'int'>
```

---

# Operators

## Arithmetic Operators

```python
+
-
*
/
%
**
//
```

Example:

```python
a = 10
b = 3

print(a+b)
print(a-b)
print(a*b)
print(a/b)
print(a%b)
print(a**b)
```

---

# Comparison Operators

```python
==
!=
>
<
>=
<=
```

Example:

```python
print(10 > 5)
```

---

# Logical Operators

```python
and
or
not
```

Example:

```python
age = 20

print(age > 18 and age < 60)
```

---

# Interview Questions

## Q1: Difference between == and is?

Answer:

== compares values.

```python
a = [1,2]
b = [1,2]

print(a == b)
```

Output:

```python
True
```

is compares memory location.

```python
print(a is b)
```

Output:

```python
False
```

---

## Q2: What is dynamically typed language?

Python determines variable type during runtime.

```python
x = 10
x = "Hello"
```

No explicit declaration required.

---

## Q3: Mutable vs Immutable?

Mutable:

- List
- Dictionary
- Set

Immutable:

- String
- Tuple
- Integer
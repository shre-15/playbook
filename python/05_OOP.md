# Object-Oriented Programming

## Class

Blueprint for objects.

```python
class Employee:
    pass
```

---

## Object

```python
emp = Employee()
```

---

## Constructor

```python
class Employee:

    def __init__(self,name):
        self.name = name
```

---

# Encapsulation

```python
class Employee:

    def __init__(self):
        self.__salary = 1000
```

---

# Inheritance

```python
class Animal:
    pass

class Dog(Animal):
    pass
```

---

# Polymorphism

```python
class Dog:
    def sound(self):
        print("Bark")

class Cat:
    def sound(self):
        print("Meow")
```

---

# Abstraction

```python
from abc import ABC, abstractmethod
```

---

# Interview Questions

## Four Pillars of OOP

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

---

## Method Overloading in Python?

Not supported directly.

Use default arguments.

---

## Method Overriding?

Child class redefines parent method.
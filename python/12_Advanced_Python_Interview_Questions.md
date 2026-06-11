# Advanced Python Interview Questions (3–5 YOE)

## 1. What is Python?

### Answer

Python is a high-level, interpreted, object-oriented, and dynamically typed programming language known for its simplicity and readability.

### Features

* Easy to learn
* Platform independent
* Huge standard library
* Automatic memory management
* Supports OOP and Functional Programming

---

## 2. What is Dynamic Typing?

### Answer

Python determines variable types during runtime.

```python
x = 10
print(type(x))

x = "Hello"
print(type(x))
```

### Output

```python
<class 'int'>
<class 'str'>
```

### Interview Follow-up

Unlike Java or C++, Python does not require explicit type declarations.

---

## 3. Difference Between is and ==

### Answer

`==` compares values.

```python
a = [1, 2]
b = [1, 2]

print(a == b)
```

Output:

```python
True
```

`is` compares memory locations.

```python
print(a is b)
```

Output:

```python
False
```

### Interview Tip

Use:

```python
if value is None:
    pass
```

instead of

```python
if value == None:
    pass
```

---

## 4. Mutable vs Immutable Objects

### Mutable Types

* list
* dict
* set

```python
numbers = [1, 2]
numbers.append(3)
```

### Immutable Types

* int
* float
* str
* tuple

```python
name = "Python"
```

### Frequently Asked

Why are tuples hashable but lists are not?

Because tuples are immutable.

---

## 5. List vs Tuple

| List        | Tuple       |
| ----------- | ----------- |
| Mutable     | Immutable   |
| []          | ()          |
| Slower      | Faster      |
| More Memory | Less Memory |

### Example

```python
my_list = [1, 2, 3]
my_tuple = (1, 2, 3)
```

### When to Use Tuple?

Use tuples for constant data that should not change.

---

## 6. Dictionary Internals

### Answer

Python dictionaries use Hash Tables internally.

Operations:

```text
Insert -> O(1)
Search -> O(1)
Delete -> O(1)
```

### Example

```python
employee = {
    "name": "John",
    "age": 30
}
```

### Interview Question

Why are dictionary lookups fast?

Because of hashing.

---

## 7. Deep Copy vs Shallow Copy

### Shallow Copy

Copies references.

```python
import copy

a = [[1, 2]]
b = copy.copy(a)

a[0].append(3)

print(b)
```

Output:

```python
[[1, 2, 3]]
```

### Deep Copy

Creates completely independent copies.

```python
import copy

a = [[1, 2]]
b = copy.deepcopy(a)

a[0].append(3)

print(b)
```

Output:

```python
[[1, 2]]
```

---

## 8. What are *args and **kwargs?

### *args

Variable positional arguments.

```python
def add(*args):
    return sum(args)

print(add(1, 2, 3))
```

Output:

```python
6
```

### **kwargs

Variable keyword arguments.

```python
def details(**kwargs):
    print(kwargs)

details(name="John", age=25)
```

Output:

```python
{'name': 'John', 'age': 25}
```

---

## 9. What is a Lambda Function?

### Answer

Anonymous function.

```python
square = lambda x: x * x

print(square(5))
```

Output:

```python
25
```

Equivalent:

```python
def square(x):
    return x * x
```

---

## 10. What is a Closure?

### Answer

A function that remembers variables from its enclosing scope.

```python
def outer(msg):

    def inner():
        print(msg)

    return inner

greet = outer("Hello")
greet()
```

Output:

```python
Hello
```

---

## 11. What is a Decorator?

### Answer

A decorator modifies function behavior without changing its source code.

```python
def logger(func):

    def wrapper():
        print("Before Execution")
        func()
        print("After Execution")

    return wrapper
```

Usage:

```python
@logger
def greet():
    print("Hello")

greet()
```

Output:

```python
Before Execution
Hello
After Execution
```

### Real-world Use Cases

* Logging
* Authentication
* Authorization
* Caching

---

## 12. What is an Iterator?

### Answer

An object implementing:

```python
__iter__()
__next__()
```

Example:

```python
nums = iter([1, 2, 3])

print(next(nums))
```

Output:

```python
1
```

---

## 13. What is a Generator?

### Answer

A function that uses `yield`.

```python
def count():

    yield 1
    yield 2
    yield 3

for num in count():
    print(num)
```

### Advantages

* Lazy evaluation
* Memory efficient
* Faster for large datasets

---

## 14. yield vs return

### return

Terminates function.

```python
def test():
    return 1
```

### yield

Pauses execution.

```python
def test():
    yield 1
```

---

## 15. What is OOP?

### Answer

Object-Oriented Programming organizes software using classes and objects.

### Four Pillars

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

---

## 16. What is Encapsulation?

### Answer

Restricting direct access to internal data.

```python
class Employee:

    def __init__(self):
        self.__salary = 5000
```

Private variable:

```python
__salary
```

---

## 17. What is Inheritance?

### Answer

A child class acquires properties of a parent class.

```python
class Animal:

    def speak(self):
        print("Animal Sound")


class Dog(Animal):
    pass


dog = Dog()
dog.speak()
```

Output:

```python
Animal Sound
```

---

## 18. What is Polymorphism?

### Answer

Same method name behaves differently.

```python
class Dog:

    def sound(self):
        print("Bark")


class Cat:

    def sound(self):
        print("Meow")
```

---

## 19. What is Method Overriding?

### Answer

Child class redefines parent method.

```python
class Parent:

    def show(self):
        print("Parent")


class Child(Parent):

    def show(self):
        print("Child")
```

---

## 20. What is MRO?

### Answer

Method Resolution Order determines the order Python searches for methods in multiple inheritance.

```python
class A:
    pass

class B(A):
    pass

class C(A):
    pass

class D(B, C):
    pass

print(D.mro())
```

Python uses:

```text
C3 Linearization
```

---

## 21. What is Exception Handling?

### Answer

Mechanism for handling runtime errors.

```python
try:
    x = 10 / 0

except ZeroDivisionError:
    print("Cannot divide by zero")
```

---

## 22. Difference Between Exception and Error

### Exception

Can be handled.

Examples:

```python
ValueError
TypeError
KeyError
```

### Error

More severe.

Examples:

```python
MemoryError
SystemError
```

---

## 23. What is a Context Manager?

### Answer

Used for resource management.

```python
with open("data.txt") as file:
    content = file.read()
```

Benefits:

* Automatically closes files
* Cleaner code
* Prevents resource leaks

---

## 24. What is GIL?

### Answer

Global Interpreter Lock allows only one thread to execute Python bytecode at a time.

### Impact

Multithreading does not improve CPU-bound tasks.

### Solution

Use multiprocessing.

---

## 25. Thread vs Process

| Thread          | Process         |
| --------------- | --------------- |
| Shared Memory   | Separate Memory |
| Lightweight     | Heavyweight     |
| Faster Creation | Slower Creation |
| Affected by GIL | Not Affected    |

### Use Threading

* API calls
* File I/O
* Database I/O

### Use Multiprocessing

* Data Processing
* Machine Learning
* Image Processing

---

## 26. What is Garbage Collection?

### Answer

Python automatically frees unused memory.

Uses:

* Reference Counting
* Garbage Collector

Example:

```python
a = [1, 2, 3]

del a
```

Memory becomes eligible for cleanup.

---

## 27. What is Monkey Patching?

### Answer

Modifying classes or methods during runtime.

```python
class Employee:
    pass

def greet(self):
    print("Hello")

Employee.greet = greet

emp = Employee()
emp.greet()
```

Output:

```python
Hello
```

---

## 28. What is Duck Typing?

### Answer

"If it walks like a duck and quacks like a duck, it is a duck."

Python checks behavior, not type.

```python
class Dog:
    def sound(self):
        print("Bark")

class Cat:
    def sound(self):
        print("Meow")

def make_sound(animal):
    animal.sound()
```

---

## 29. What are Magic Methods?

### Answer

Special methods that begin and end with double underscores.

Examples:

```python
__init__
__str__
__repr__
__len__
__add__
```

Example:

```python
class Employee:

    def __str__(self):
        return "Employee Object"
```

---

## 30. Most Frequently Asked Python Questions

1. Mutable vs Immutable
2. List vs Tuple
3. is vs ==
4. Deep Copy vs Shallow Copy
5. Decorators
6. Generators vs Iterators
7. GIL
8. Thread vs Process
9. MRO
10. Context Managers
11. Closures
12. Lambda Functions
13. Dictionary Internals
14. Garbage Collection
15. Method Overriding
16. Encapsulation
17. Polymorphism
18. Duck Typing
19. Monkey Patching
20. Python Memory Management

---

# Interview Preparation Tips

### Must Master

* OOP Concepts
* Collections
* Generators
* Decorators
* Exception Handling
* Multithreading
* Multiprocessing
* Async Programming
* SQL Basics
* REST APIs

### For 3–5 YOE

Interviewers focus more on:

* Real-world use cases
* Optimization
* Design decisions
* Performance improvements
* Code quality
* Scalability

Understanding the "why" behind Python concepts is often more important than memorizing definitions.

# Decorators

Decorator modifies behavior of function.

## Example

```python
def logger(func):

    def wrapper():
        print("Before")
        func()
        print("After")

    return wrapper
```

Usage:

```python
@logger
def greet():
    print("Hello")
```

---

# Interview Questions

## Why decorators?

Code reusability.

Examples:

- Logging
- Authentication
- Caching

---

## Built-in decorators

```python
@staticmethod
@classmethod
@property
```
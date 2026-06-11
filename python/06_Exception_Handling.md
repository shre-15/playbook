# Exception Handling

## Try Except

```python
try:
    x = 10/0
except ZeroDivisionError:
    print("Cannot divide by zero")
```

---

## Multiple Exceptions

```python
try:
    pass
except ValueError:
    pass
except TypeError:
    pass
```

---

## Finally

```python
finally:
    print("Always executes")
```

---

## Raise

```python
raise ValueError("Invalid")
```

---

# Interview Questions

## Difference between Error and Exception?

Error:

System-level issue.

Exception:

Can be handled.

---

## Why use finally?

Resource cleanup.
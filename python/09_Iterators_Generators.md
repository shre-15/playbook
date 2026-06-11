# Iterators and Generators

## Iterator

Object implementing:

```python
__iter__()
__next__()
```

Example:

```python
nums = iter([1,2,3])

print(next(nums))
```

---

## Generator

Uses yield.

```python
def counter():
    yield 1
    yield 2
    yield 3
```

---

Advantages:

- Memory efficient
- Lazy evaluation

---

# Interview Questions

## yield vs return

return:

Terminates function.

yield:

Pauses execution.

---

## Why generators?

Large datasets processing.
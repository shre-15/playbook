# File Handling

## Open File

```python
file = open("data.txt","r")
```

Modes:

```python
r
w
a
rb
wb
```

---

## Read

```python
file.read()
```

---

## Write

```python
file.write("Hello")
```

---

## Context Manager

```python
with open("data.txt","r") as file:
    print(file.read())
```

---

# Interview Questions

## Why use with?

Automatically closes file.

---

## Difference between write and append?

write() overwrites.

append() adds content.
# Multithreading and Multiprocessing

## Multithreading

```python
import threading
```

Best for:

- I/O bound tasks

Example:

```python
thread = threading.Thread(target=my_function)
thread.start()
```

---

## Multiprocessing

```python
from multiprocessing import Process
```

Best for:

- CPU intensive tasks

Example:

```python
p = Process(target=my_function)
p.start()
```

---

# GIL

Global Interpreter Lock.

Only one thread executes Python bytecode at a time.

---

# Interview Questions

## Thread vs Process

| Thread | Process |
|----------|----------|
| Shared Memory | Separate Memory |
| Lightweight | Heavyweight |
| Faster | Slower |

---

## Why multiprocessing over threading?

Avoids GIL.
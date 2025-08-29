# Day 003 — Functions

---

## 🕐 Tier 1 (1h) — Core

Focus: defining functions, arguments, and return values.

- In `notebooks/week1_basics.ipynb`, add a new section **Functions**.
- Write simple functions with positional args, keyword args, and return values.

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

def add(a: int, b: int = 0) -> int:
    return a + b

print(greet("Ada"))
print(add(3, 4), add(5))
```

- Practice recursion and iteration with basic examples.

```python
# Factorial recursion
def factorial(n: int) -> int:
    if n == 0:
        return 1
    return n * factorial(n-1)

print(factorial(5))

# Fibonacci iteration
def fibonacci(n: int) -> list[int]:
    seq = [0, 1]
    for _ in range(2, n):
        seq.append(seq[-1] + seq[-2])
    return seq[:n]

print(fibonacci(10))
```

---

## ⏱️ Tier 2 (2h) — Extend

- Add functions with multiple return values and default/keyword arguments.

```python
def min_max_avg(numbers: list[float]) -> tuple[float, float, float]:
    return min(numbers), max(numbers), sum(numbers) / len(numbers)

print(min_max_avg([1, 2, 3, 4, 5]))
```

- Add **docstrings** and demonstrate `help()`.

```python
def is_prime(n: int) -> bool:
    """Return True if n is prime, else False."""
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

help(is_prime)
```

- Demonstrate *args and **kwargs.

```python
def print_all(*args, **kwargs):
    print("Positional:", args)
    print("Keywords:", kwargs)

print_all(1, 2, 3, name="Ada", age=27)
```

---

## ⏳ Tier 3 (3h) — Advance

- Move functions to `utils/func_utils.py` with type hints and docstrings.

```python
"""Function utilities for AI Journey."""

def gcd(a: int, b: int) -> int:
    """Greatest common divisor using Euclidean algorithm."""
    while b:
        a, b = b, a % b
    return a

def lcm(a: int, b: int) -> int:
    """Least common multiple."""
    return abs(a * b) // gcd(a, b)

def reverse_string(s: str) -> str:
    return s[::-1]
```

- In your notebook, import and test:

```python
from utils.func_utils import gcd, lcm, reverse_string
print(gcd(48, 18), lcm(4, 5), reverse_string("Python"))
```

---

## 🔥 Tier 4 (4h) — Polish

- Write tests in `tests/test_func_utils.py`.

```python
from utils.func_utils import gcd, lcm, reverse_string

def test_gcd():
    assert gcd(48, 18) == 6
    assert gcd(7, 3) == 1

def test_lcm():
    assert lcm(4, 5) == 20
    assert lcm(7, 3) == 21

def test_reverse_string():
    assert reverse_string("abc") == "cba"
    assert reverse_string("") == ""
```

- Run tests:

```bash
pytest -q
```

- Update README.md or notebook with examples.

---

## ✅ Deliverable
- Notebook updated with **functions section**
- `utils/func_utils.py` created with reusable functions
- Tests written in `tests/test_func_utils.py` (Tier 4)
- All changes committed & pushed

---

## 📚 Choose Your Adventure (Optional References)
- Book: [*Python Crash Course* — Functions](https://nostarch.com/pythoncrashcourse2e)  
- Book: [*Automate the Boring Stuff with Python* — Functions](https://automatetheboringstuff.com/)  
- Video: [Corey Schafer — Python Functions](https://www.youtube.com/watch?v=9Os0o3wzS_I)  
- Blog: [Real Python — Defining Your Own Python Function](https://realpython.com/defining-your-own-python-function/)  

---

🔗 *Navigation:* [⬅️ Back to Week 01 Overview](./README.md) | [🌍 RoadMapUltimate](../../RoadMapUltimate.md)

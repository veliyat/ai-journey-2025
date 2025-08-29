# Day 002 — Python Basics

---

## 🕐 Tier 1 (1h) — Core

Focus: variables, data types, operators, and loops.

- Open `notebooks/week1_basics.ipynb` and add a new section **Python Basics**.
- Practice variables & types, arithmetic/comparison/logical operators.
- Write a few loop exercises (`for`, `while`).

```python
# Variables & types
name = "Ada"
age = 27
height_m = 1.65
is_student = True
print(type(name), type(age), type(height_m), type(is_student))

# Operators
a, b = 7, 3
print(a + b, a - b, a * b, a / b, a // b, a % b, a ** b)
print(a > b, a == b, (a > 5) and (b < 5))

# Loops
for i in range(5):
    print("for:", i)

j = 0
while j < 3:
    print("while:", j)
    j += 1
```

**Mini exercise:** FizzBuzz (1..20)

```python
for n in range(1, 21):
    if n % 15 == 0:
        print("FizzBuzz")
    elif n % 3 == 0:
        print("Fizz")
    elif n % 5 == 0:
        print("Buzz")
    else:
        print(n)
```

---

## ⏱️ Tier 2 (2h) — Extend

Add two small programs and basic error handling.

1) **Calculator (CLI)** — add to notebook cell:
```python
def calculator():
    try:
        x = float(input("Enter first number: "))
        op = input("Operator (+ - * /): ").strip()
        y = float(input("Enter second number: "))
        if op == "+":
            print(x + y)
        elif op == "-":
            print(x - y)
        elif op == "*":
            print(x * y)
        elif op == "/":
            print(x / y if y != 0 else "Error: divide by zero")
        else:
            print("Unknown operator")
    except ValueError:
        print("Please enter valid numbers.")

# calculator()   # uncomment to run interactively
```

2) **Temperature converter** (C↔F):
```python
def c_to_f(c: float) -> float:
    return (c * 9/5) + 32

def f_to_c(f: float) -> float:
    return (f - 32) * 5/9

print(c_to_f(0), c_to_f(100))  # 32, 212
print(round(f_to_c(32), 2), round(f_to_c(212), 2))  # 0.0, 100.0
```

---

## ⏳ Tier 3 (3h) — Advance

Refactor repeatable code into a `utils/` module with docstrings & type hints.

- Create `utils/` folder and add `utils/basic_utils.py`:

```python
"""Basic utility functions for the AI Journey."""
from typing import Iterable, List

def factorial(n: int) -> int:
    """Return n! for n >= 0."""
    if n < 0:
        raise ValueError("n must be >= 0")
    out = 1
    for i in range(2, n + 1):
        out *= i
    return out

def fibonacci(n: int) -> List[int]:
    """Return first n Fibonacci numbers (n >= 0)."""
    a, b = 0, 1
    seq: List[int] = []
    for _ in range(n):
        seq.append(a)
        a, b = b, a + b
    return seq

def is_palindrome(s: str) -> bool:
    t = ''.join(ch.lower() for ch in s if ch.isalnum())
    return t == t[::-1]

def running_sum(xs: Iterable[float]) -> float:
    total = 0.0
    for x in xs:
        total += float(x)
    return total
```

- In your notebook, import and test:

```python
from utils.basic_utils import factorial, fibonacci, is_palindrome, running_sum
print(factorial(5), fibonacci(6), is_palindrome("Madam"), running_sum([1,2,3.5]))
```

---

## 🔥 Tier 4 (4h) — Polish

Add unit tests with **pytest** and (optional) formatting hooks.

- Create `tests/test_basic_utils.py`:

```python
from utils.basic_utils import factorial, fibonacci, is_palindrome, running_sum
import pytest

def test_factorial():
    assert factorial(0) == 1
    assert factorial(5) == 120
    with pytest.raises(ValueError):
        factorial(-1)

def test_fibonacci():
    assert fibonacci(0) == []
    assert fibonacci(5) == [0, 1, 1, 2, 3]

def test_is_palindrome():
    assert is_palindrome("Madam")
    assert is_palindrome("A man, a plan, a canal: Panama")
    assert not is_palindrome("Hello")

def test_running_sum():
    assert running_sum([1, 2, 3.5]) == 6.5
```

- (Optional) Add **pre-commit** config for formatting (if you use it later).

```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/psf/black
    rev: 24.4.2
    hooks:
      - id: black
  - repo: https://github.com/charliermarsh/ruff-pre-commit
    rev: v0.6.2
    hooks:
      - id: ruff
```

Run tests:
```bash
pytest -q
```

---

## ✅ Deliverable
- Updated notebook with **Python basics + mini programs**
- `utils/basic_utils.py` module created & imported
- Tests added in `tests/test_basic_utils.py` (Tier 4)
- All changes committed & pushed

---

## 📚 Choose Your Adventure (Optional References)
- Book: [*Automate the Boring Stuff with Python* — basics](https://automatetheboringstuff.com/)  
- Video: [Corey Schafer — Python Basics](https://www.youtube.com/playlist?list=PL-osiE80TeTsqhIuOqKhwlXsIBIdSeYtc)  
- Video: [FreeCodeCamp — Python for Beginners (4h)](https://www.youtube.com/watch?v=rfscVS0vtbw)  
- Blog: [Real Python — If/Else, Loops, and Exceptions](https://realpython.com/)  

---

🔗 *Navigation:* [⬅️ Back to Week 01 Overview](./README.md) | [🌍 RoadMapUltimate](../../RoadMapUltimate.md)

# Day 004 — Lists

---

## 🕐 Tier 1 (1h) — Core

Focus: creating lists, indexing, slicing, mutation, and iteration.

- In `notebooks/week1_basics.ipynb`, add a new section **Lists**.
- Practice creation, indexing, slicing, append/extend/insert/remove/pop, and iteration.

```python
nums = [3, 1, 4, 1, 5, 9]
print(nums[0], nums[-1])     # indexing
print(nums[1:4])             # slicing
nums.append(2)
nums.extend([6, 5])
nums.insert(1, 7)
removed = nums.pop()         # removes last
nums.remove(1)               # removes first occurrence of 1
for x in nums:
    print(x, end=" ")
```

**Mini exercises**
1) Given `nums`, print **unique** values (preserve order).  
2) Reverse a list **in-place** and via slicing.  
3) Compute **max, min, sum, average**.

```python
# 1) Unique (preserve order)
seen, unique = set(), []
for x in nums:
    if x not in seen:
        seen.add(x)
        unique.append(x)
print("unique:", unique)

# 2) Reverse
nums_rev_slice = nums[::-1]
nums.reverse()  # in-place

# 3) Aggregates
print(max(nums), min(nums), sum(nums), sum(nums)/len(nums))
```

---

## ⏱️ Tier 2 (2h) — Extend

Learn **list comprehensions** and simple filtering/mapping.

```python
# Squares of even numbers 0..9
squares_even = [n*n for n in range(10) if n % 2 == 0]

# Normalize strings (strip + lower) and filter out empty
raw = ["  Ada ", "  ", "Python ", " ", "ML"]
clean = [s.strip().lower() for s in raw if s.strip()]

# Cartesian pairs (small demo)
pairs = [(i, j) for i in range(3) for j in range(2)]
squares_even, clean, pairs
```

**Mini project (Tier 2):** Given a list of dictionaries `students`, compute:  
- all names,  
- average score,  
- names of students with score >= 80.

```python
students = [
    {"name": "Ada", "score": 91},
    {"name": "Alan", "score": 78},
    {"name": "Grace", "score": 88},
]

names = [s["name"] for s in students]
avg_score = sum(s["score"] for s in students) / len(students)
top_names = [s["name"] for s in students if s["score"] >= 80]
names, avg_score, top_names
```

---

## ⏳ Tier 3 (3h) — Advance

Create reusable helpers in `utils/list_utils.py` with type hints and docstrings.

```python
"""List utilities for AI Journey."""
from __future__ import annotations
from typing import Iterable, Callable, TypeVar, List

T = TypeVar("T")
U = TypeVar("U")

def unique_preserve_order(xs: Iterable[T]) -> List[T]:
    """Return a list of unique elements preserving first-seen order."""
    seen, out = set(), []
    for x in xs:
        if x not in seen:
            seen.add(x)
            out.append(x)
    return out

def chunk(xs: List[T], size: int) -> List[List[T]]:
    """Split list into chunks of given size (size > 0)."""
    if size <= 0:
        raise ValueError("size must be > 0")
    return [xs[i:i+size] for i in range(0, len(xs), size)]

def flatten(nested: Iterable[Iterable[T]]) -> List[T]:
    """Flatten one level of nesting."""
    out: List[T] = []
    for it in nested:
        out.extend(it)
    return out

def map_filter(xs: Iterable[T], f: Callable[[T], U] | None = None,
               pred: Callable[[U], bool] | None = None) -> List[U]:
    """Optionally map then filter in one pass. If f is None, identity is used."""
    out: List[U] = []
    if f is None:
        f = lambda x: x  # type: ignore
    for x in xs:
        y = f(x)
        if pred is None or pred(y):
            out.append(y)
    return out
```

- Import and test in your notebook:

```python
from utils.list_utils import unique_preserve_order, chunk, flatten, map_filter
print(unique_preserve_order([1,2,1,3,2,4]))
print(chunk([1,2,3,4,5], 2))
print(flatten([[1,2],[3,4,5]]))
print(map_filter([1,2,3,4], f=lambda x: x*x, pred=lambda y: y%2==0))
```

---

## 🔥 Tier 4 (4h) — Polish

Write tests in `tests/test_list_utils.py` and consider performance nuances.

```python
from utils.list_utils import unique_preserve_order, chunk, flatten, map_filter
import pytest

def test_unique_preserve_order():
    assert unique_preserve_order([1,2,1,3,2,4]) == [1,2,3,4]

def test_chunk():
    assert chunk([1,2,3,4,5], 2) == [[1,2],[3,4],[5]]
    with pytest.raises(ValueError):
        chunk([1,2,3], 0)

def test_flatten():
    assert flatten([[1,2],[3,4,5]]) == [1,2,3,4,5]

def test_map_filter():
    res = map_filter([1,2,3,4], f=lambda x: x*x, pred=lambda y: y%2==0)
    assert res == [4,16]
```

**Performance tip:** when membership tests dominate, consider `set`/`dict` for O(1) average lookups; for small data, a simple list can be faster due to lower overhead.

Run tests:
```bash
pytest -q
```

---

## ✅ Deliverable
- Notebook updated with **list operations + comprehensions**
- `utils/list_utils.py` created with reusable helpers
- Tests in `tests/test_list_utils.py` (Tier 4)
- All changes committed & pushed

---

## 📚 Choose Your Adventure (Optional References)
- Book: [*Automate the Boring Stuff with Python* — Lists](https://automatetheboringstuff.com/)
- Video: [Corey Schafer — Lists and Tuples](https://www.youtube.com/results?search_query=Corey+Schafer+python+lists)
- Video: [FreeCodeCamp — Python Lists](https://www.youtube.com/results?search_query=freecodecamp+python+lists)
- Blog: [Real Python — Python Lists](https://realpython.com/python-lists-tuples/)

---

🔗 *Navigation:* [⬅️ Back to Week 01 Overview](./README.md) | [🌍 RoadMapUltimate](../../RoadMapUltimate.md)

# Day 005 — Dictionaries

---

## 🕐 Tier 1 (1h) — Core

Focus: dictionary creation, key-value access, adding/updating/removing entries, and iteration.

- In `notebooks/week1_basics.ipynb`, add a new section **Dictionaries**.
- Practice dictionary basics.

```python
person = {"name": "Ada", "age": 27, "city": "London"}
print(person["name"], person.get("age"))
person["age"] = 28          # update
person["country"] = "UK"    # add
del person["city"]          # delete

for key, value in person.items():
    print(key, ":", value)

print("keys:", list(person.keys()))
print("values:", list(person.values()))
```

**Mini exercise:** Count word frequencies in a sentence.

```python
sentence = "to be or not to be"
freq = {}
for word in sentence.split():
    freq[word] = freq.get(word, 0) + 1
print(freq)
```

---

## ⏱️ Tier 2 (2h) — Extend

Work with **dictionary comprehensions** and nested dictionaries.

```python
# Squares in a dict
squares = {n: n*n for n in range(6)}
print(squares)

# Swap keys/values
swap = {v: k for k, v in squares.items()}
print(swap)

# Nested dictionaries
students = {
    "Ada": {"math": 91, "cs": 95},
    "Alan": {"math": 78, "cs": 88},
}
for name, scores in students.items():
    avg = sum(scores.values()) / len(scores)
    print(name, "avg:", avg)
```

**Mini project (Tier 2):** Build a frequency counter as a function.

```python
def word_count(text: str) -> dict[str, int]:
    counts = {}
    for word in text.lower().split():
        counts[word] = counts.get(word, 0) + 1
    return counts

print(word_count("The cat and the hat and the bat"))
```

---

## ⏳ Tier 3 (3h) — Advance

Create reusable helpers in `utils/dict_utils.py` with type hints.

```python
"""Dictionary utilities for AI Journey."""
from collections import Counter
from typing import Dict, Any

def merge_dicts(a: Dict[Any, Any], b: Dict[Any, Any]) -> Dict[Any, Any]:
    """Merge two dictionaries, b overrides a."""
    out = a.copy()
    out.update(b)
    return out

def invert_dict(d: Dict[Any, Any]) -> Dict[Any, Any]:
    """Invert dict (keys become values). Assumes values are hashable & unique."""
    return {v: k for k, v in d.items()}

def top_n_frequencies(text: str, n: int = 3) -> Dict[str, int]:
    """Return the top n word frequencies from a text."""
    return dict(Counter(text.lower().split()).most_common(n))
```

- Test in your notebook:

```python
from utils.dict_utils import merge_dicts, invert_dict, top_n_frequencies
print(merge_dicts({"a":1}, {"b":2, "a":3}))
print(invert_dict({"x": 1, "y": 2}))
print(top_n_frequencies("cat bat cat hat bat cat", 2))
```

---

## 🔥 Tier 4 (4h) — Polish

Add tests in `tests/test_dict_utils.py`.

```python
from utils.dict_utils import merge_dicts, invert_dict, top_n_frequencies

def test_merge_dicts():
    assert merge_dicts({"a":1}, {"b":2}) == {"a":1, "b":2}
    assert merge_dicts({"a":1}, {"a":3}) == {"a":3}

def test_invert_dict():
    assert invert_dict({"x": 1, "y": 2}) == {1: "x", 2: "y"}

def test_top_n_frequencies():
    text = "cat bat cat hat bat cat"
    result = top_n_frequencies(text, 2)
    assert result == {"cat": 3, "bat": 2}
```

Run tests:
```bash
pytest -q
```

---

## ✅ Deliverable
- Notebook updated with **dictionary exercises + word counter**
- `utils/dict_utils.py` created with reusable helpers
- Tests in `tests/test_dict_utils.py` (Tier 4)
- All changes committed & pushed

---

## 📚 Choose Your Adventure (Optional References)
- Book: [*Automate the Boring Stuff with Python* — Dictionaries](https://automatetheboringstuff.com/)
- Video: [Corey Schafer — Python Dictionaries](https://www.youtube.com/watch?v=daefaLgNkw0)
- Video: [FreeCodeCamp — Python Dictionaries](https://www.youtube.com/results?search_query=freecodecamp+python+dictionaries)
- Blog: [Real Python — Dictionaries 101](https://realpython.com/python-dicts/)

---

🔗 *Navigation:* [⬅️ Back to Week 01 Overview](./README.md) | [🌍 RoadMapUltimate](../../RoadMapUltimate.md)

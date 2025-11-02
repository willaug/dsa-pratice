# 🗂️ Hash Map

A **hash map** stores data as **key → value** pairs with (amortized) **O(1)** `get/set/delete`. In Python, the built-ins are **`dict`** (map) and **`set`** (keys only).

### 📌 Characteristics of Hash Maps

1. **Time**: Average **O(1)** for lookups/inserts/deletes (worst-case O(n) with heavy collisions).
2. **Unordered**: Python 3.7+ preserves **insertion order**, but it’s not sorted order.
3. **Hash & equality**: Keys must be **hashable** and use stable equality.
4. **Collisions**: Resolved internally (open addressing); you don’t manage buckets directly.

### 💚 Best choice

* Use when you need **constant-time membership** or **keyed counts**.
* Great for **frequency maps**, **Two Sum (unsorted)**, **anagram checks**, **dedup**, **caching**.
* Avoid if you need **sorted/range queries** → use `bisect` + sorted list, or `heapq`, or a tree structure (third-party).

### 💛 In Python

* Prefer `dict` for maps, `set` for membership, and `collections.Counter` / `defaultdict(int)` for counting.

```python
# Basic dict usage
m = {}
m["apple"] = 3
m["banana"] = 1
m["apple"] += 1
print(m.get("apple"))   # 4
print("banana" in m)    # True
m.pop("banana", None)
```

```python
# Frequency counter (string → counts)
from collections import Counter

def char_freq(s: str) -> Counter:
    return Counter(s)

# Example: char_freq("ababa") -> Counter({'a': 3, 'b': 2})
```

```python
# Two Sum (UNSORTED) using a dict
# Time: O(n) | Space: O(n)
from typing import List, Tuple

def two_sum_unsorted(nums: List[int], target: int) -> Tuple[int, int]:
    seen = {}  # value -> index
    for i, x in enumerate(nums):
        need = target - x
        if need in seen:
            return (seen[need], i)
        seen[x] = i
    return (-1, -1)
```

```python
# Anagram check using counts
# Time: O(n) | Space: O(k), k = distinct chars
from collections import Counter

def is_anagram(a: str, b: str) -> bool:
    if len(a) != len(b):
        return False
    return Counter(a) == Counter(b)
```

```python
# defaultdict for counting (alternative to Counter)
from collections import defaultdict

def word_freq(words):
    freq = defaultdict(int)
    for w in words:
        freq[w] += 1
    return freq
```

---

## 🔍 Step-by-step walkthrough (passes)

### Example — `two_sum_unsorted([2, 7, 11, 15], 9)`

Track the dict **after each pass**:

* **Pass 0 (i=0)**: `x=2`, `need=7`.
  `7 in seen`? **No** → store `seen[2] = 0`.
  **seen**: `{2: 0}`

* **Pass 1 (i=1)**: `x=7`, `need=2`.
  `2 in seen`? **Yes → index 0** → return **(0, 1)**.
  (Done.)

> If no pair exists, loop ends and we return `(-1, -1)`.

---

## 🧠 Quick tips

* **Membership only?** Use **`set`**: `seen = set(); if x in seen: ...; seen.add(x)`.
* **Counting pattern** without `defaultdict`:

  ```python
  m[k] = m.get(k, 0) + 1
  ```
* **Hashable keys**: numbers, strings, tuples (of hashables). Lists/dicts aren’t hashable.
* **Space vs speed**: dicts/sets are fast but memory-heavy—mind huge datasets.

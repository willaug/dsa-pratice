# 🚀 Exponential Search

Exponential search is great for finding a value in a **sorted** array when the size may be large/unknown **or** when the target might be **near the beginning**. It works in two phases:

1. **Exponential bounding** (1, 2, 4, 8, …) to bracket the target.
2. **Binary search** inside that bracket.

### 📌 Characteristics of Exponential Search

1. **Two phases**: fast bounding → precise binary search.
2. **Time**: **O(log pos)** where `pos` is the target’s index (and **O(1)** extra space).
3. **Sorted prerequisite**: ascending by default (flip comparisons for descending).
4. **Good fits**: very large arrays, unknown length (“infinite array” APIs), or targets near the front.

### 💚 Best choice

* Use on **sorted** data when:

  * Getting the **length** is expensive/unknown, or
  * The target is likely **early** in the array.
* Prefer arrays / random access (not ideal for linked lists).

### 💛 In JavaScript (Node 20+)

* Grow `bound` while `arr[bound] < target`, then binary-search `[bound/2 … min(bound, n-1)]`.

```js
// Exponential Search on a sorted ascending array.
// Returns the index of target or -1.
// Time: O(log pos) | Space: O(1)
function exponentialSearch(arr, target) {
  const n = arr.length;
  if (n === 0) return -1;
  if (arr[0] === target) return 0;

  // 1) Exponential bound: find high where arr[bound] >= target (or reach n)
  let bound = 1;
  while (bound < n && arr[bound] < target) bound *= 2;

  // 2) Binary search in [bound/2, min(bound, n-1)]
  let left = bound >> 1;
  let right = Math.min(bound, n - 1);

  while (left <= right) {
    const mid = left + ((right - left) >> 1);
    if (arr[mid] === target) return mid;
    if (arr[mid] < target) left = mid + 1;
    else right = mid - 1;
  }
  return -1;
}
```

---

## 🔍 Step-by-step Walkthroughs (showing the “passes”)

### Example A — target **exists**

`arr = [1, 3, 5, 7, 9, 12, 15, 18, 21]`, `target = 15`

**Phase 1 — Bounding (doubling):**

* **Pass 0**: index 0 already checked (1 ≠ 15).
* **Pass 1**: `bound=1` → `arr[1]=3 < 15` → `bound=2`.
* **Pass 2**: `bound=2` → `arr[2]=5 < 15` → `bound=4`.
* **Pass 3**: `bound=4` → `arr[4]=9 < 15` → `bound=8`.
* **Pass 4**: `bound=8` → `arr[8]=21 ≥ 15` → stop.
  Bracket for binary search: **[4, 8]**.

**Phase 2 — Binary Search in [4, 8]:**

* **Pass 1**: `left=4`, `right=8` → `mid=6` → `arr[6]=15` → **found**.
  **Answer**: index **6**.

---

### Example B — target **does not exist**

`arr = [1, 4, 6, 8, 10, 13, 17, 25]`, `target = 9`

**Phase 1 — Bounding:**

* **Pass 0**: index 0 checked (1 ≠ 9).
* **Pass 1**: `bound=1` → `arr[1]=4 < 9` → `bound=2`.
* **Pass 2**: `bound=2` → `arr[2]=6 < 9` → `bound=4`.
* **Pass 3**: `bound=4` → `arr[4]=10 ≥ 9` → stop.
  Bracket: **[2, 4]**.

**Phase 2 — Binary Search in [2, 4]:**

* **Pass 1**: `left=2`, `right=4` → `mid=3` → `arr[3]=8 < 9` → `left=4`.
* **Pass 2**: `left=4`, `right=4` → `mid=4` → `arr[4]=10 > 9` → `right=3`.
* End: `left(4) > right(3)` → **not found** → **-1**.

---

### Example C — target at the **start**

`arr = [2, 5, 9, 14, 20]`, `target = 2`

* Initial check: `arr[0] === 2` → return **0** immediately.

---

## 🧠 Quick tips

* With **duplicates**, this returns *a* valid index. Need the **first**? Run a `lowerBound` **inside the final bracket**.
* For **descending** arrays, flip the comparison signs in both phases.
* With truly **unknown length** (e.g., “infinite array” API), keep doubling until you hit an index error or a value ≥ target, then binary-search the last valid bracket.

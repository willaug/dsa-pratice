## 🧬 Merge Sort

### 🧠 Definition  
A **divide and conquer** algorithm that splits the array into halves, sorts each half, and merges them back together in order.

---

### ⚙️ How It Works  
1. Divide the array into two halves.  
2. Recursively apply merge sort to each half.  
3. Merge the two sorted halves into one sorted array.  
4. Continue until the entire array is sorted.

---

### 💻 Code (JavaScript)
```js
function mergeSort(arr) {
  if (arr.length <= 1) return arr; // base case

  const mid = Math.floor(arr.length / 2);
  const left = mergeSort(arr.slice(0, mid));
  const right = mergeSort(arr.slice(mid));

  return merge(left, right);
}

function merge(left, right) {
  const result = [];
  let i = 0, j = 0;

  while (i < left.length && j < right.length) {
    if (left[i] < right[j]) {
      result.push(left[i]);
      i++;
    } else {
      result.push(right[j]);
      j++;
    }
  }

  return [...result, ...left.slice(i), ...right.slice(j)];
}

console.log(mergeSort([5, 3, 8, 1, 2]));
```

---

### 🔍 Example Walkthrough

Input: `[5, 3, 8, 1, 2]`

| Step | Action                                           | Result             |
| ---- | ------------------------------------------------ | ------------------ |
| 1    | Split `[5, 3, 8, 1, 2]` → `[5, 3]` + `[8, 1, 2]` | —                  |
| 2    | Split `[5, 3]` → `[5]` + `[3]`                   | —                  |
| 3    | Merge `[5]` + `[3]` → `[3, 5]`                   | `[3, 5]`           |
| 4    | Split `[8, 1, 2]` → `[8]` + `[1, 2]`             | —                  |
| 5    | Merge `[1, 2]` → `[1, 2]`                        | —                  |
| 6    | Merge `[8]` + `[1, 2]` → `[1, 2, 8]`             | `[1, 2, 8]`        |
| ✅    | Merge `[3, 5]` + `[1, 2, 8]` → `[1, 2, 3, 5, 8]` | Final sorted array |

---

### ⏱️ Complexity

| Case  | Time       | Space |
| ----- | ---------- | ----- |
| Best  | O(n log n) | O(n)  |
| Avg   | O(n log n) | O(n)  |
| Worst | O(n log n) | O(n)  |

---

### 🧩 Notes

* **Stable** (preserves order of duplicates).
* **Not in-place** (needs extra space).
* Great for **large datasets** and **linked lists**.
* Often used as a base for optimized hybrid sorts.

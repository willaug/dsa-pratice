## ⚡ Quick Sort

### 🧠 Definition  
Uses **divide and conquer**: picks a pivot, partitions the array into smaller and larger elements, then recursively sorts each side.

---

### ⚙️ How It Works  
1. Choose a **pivot** (usually middle or last element).  
2. Split array into:
   - `left`: values < pivot  
   - `right`: values > pivot  
3. Recursively sort both sides.  
4. Combine: `[...sortedLeft, pivot, ...sortedRight]`

---

### 💻 Code (JavaScript)
```js
function quickSort(arr) {
  if (arr.length <= 1) return arr; // base case

  const pivot = arr[arr.length - 1];
  const left = [];
  const right = [];

  for (let i = 0; i < arr.length - 1; i++) {
    if (arr[i] < pivot) left.push(arr[i]);
    else right.push(arr[i]);
  }

  return [...quickSort(left), pivot, ...quickSort(right)];
}

console.log(quickSort([5, 3, 8, 1, 2]));
```

---

### 🔍 Example Walkthrough

Input: `[5, 3, 8, 1, 2]`
Pivot = 2

| Step | Left           | Pivot | Right       | Combined                 |
| ---- | -------------- | ----- | ----------- | ------------------------ |
| 1    | `[1]`          | 2     | `[5, 3, 8]` | `[1, 2, 5, 3, 8]`        |
| 2    | —              | —     | Pivot = 8   | `[5, 3] < 8 → [5, 3, 8]` |
| 3    | `[3,5]` sorted | —     | —           | ✅ `[1, 2, 3, 5, 8]`      |

---

### ⏱️ Complexity

| Case  | Time       | Space    |
| ----- | ---------- | -------- |
| Best  | O(n log n) | O(log n) |
| Avg   | O(n log n) | O(log n) |
| Worst | O(n²)      | O(log n) |

---

### 🧩 Notes

* **In-place version** exists (using pointers).
* **Unstable** (order of duplicates not preserved).
* Pivot choice affects performance.
* Extremely efficient for large datasets.

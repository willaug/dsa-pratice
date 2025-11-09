# 🫧 Bubble Sort
Compares **adjacent elements** and swaps them if they’re in the wrong order. Repeats the process until the array is sorted.

---

### ⚙️ How It Works  
1. Loop through the array multiple times.  
2. On each pass, compare pairs `(arr[i], arr[i+1])`.  
3. Swap if `arr[i] > arr[i+1]`.  
4. After each pass, the largest element "bubbles" to the end.  
5. Stop when no swaps happen in a full pass.

---

### 💻 Code (JavaScript)
```js
function bubbleSort(arr) {
  let n = arr.length;
  let swapped;

  do {
    swapped = false;
    for (let i = 0; i < n - 1; i++) {
      if (arr[i] > arr[i + 1]) {
        [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]];
        swapped = true;
      }
    }
    n--; // optimization: last element already sorted
  } while (swapped);

  return arr;
}

console.log(bubbleSort([5, 3, 8, 1, 2]));
```

---

### 🔍 Example Walkthrough

Input: `[5, 3, 8, 1]`

| Pass | Comparisons / Swaps                | Result         |
| ---- | ---------------------------------- | -------------- |
| 1    | 5>3 → swap / 5<8 → ok / 8>1 → swap | `[3, 5, 1, 8]` |
| 2    | 3<5 → ok / 5>1 → swap              | `[3, 1, 5, 8]` |
| 3    | 3>1 → swap                         | `[1, 3, 5, 8]` |
| ✅    | Sorted                             | `[1, 3, 5, 8]` |

---

### ⏱️ Complexity

| Case  | Time  | Space |
| ----- | ----- | ----- |
| Best  | O(n)  | O(1)  |
| Avg   | O(n²) | O(1)  |
| Worst | O(n²) | O(1)  |

---

### 🧩 Notes

* Simple but inefficient for large arrays.
* Stable and in-place.
* Good for teaching sorting basics.

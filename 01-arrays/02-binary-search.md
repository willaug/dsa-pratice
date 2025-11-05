# 🔎 Binary Search

Binary search is a highly efficient algorithm for finding an item from a sorted list of items. It works by repeatedly dividing the search interval in half. If the value of the search key is less than the item in the middle of the interval, the search continues in the lower half, or if it's greater, in the upper half. This process repeats until the value is found or the interval is empty.

### 📌 Characteristics of Binary Search
1. **Efficiency**: Reduces the time complexity from O(n) to O(log n).
2. **Sorted Data**: Requires the data to be sorted beforehand.
3. **Divide and Conquer**: Utilizes the divide and conquer strategy.

### 💚 Best choice
- Use binary search when you have a sorted dataset and need to find an element quickly.
- Consider the trade-offs between the simplicity of linear search and the efficiency of binary search.

### 💛 In JavaScript
- The binary search algorithm can be implemented using a simple loop or recursion.

```js
// Iterative Binary Search - O(log n) time, O(1) space
function binarySearch(arr, target) {
  let left = 0;
  let right = arr.length - 1;
  while (left <= right) {
    const mid = Math.floor((left + right) / 2);
    if (arr[mid] === target) {
      return mid; // Target found
    } else if (arr[mid] < target) {
      left = mid + 1; // Search in the right half
    } else {
      right = mid - 1; // Search in the left half
    }
  }
  return -1; // Target not found
}
// Example:
//  mid = 2, arr[mid] = 3 < 4 → left = mid + 1 = 3
//  mid = 4, arr[mid] = 5 > 4 → right = mid - 1 = 3
//  mid = 3, arr[mid] = 4 === 4 → return mid = 3
console.log(binarySearch([1, 2, 3, 4, 5, 6], 4)); // Output: 3
```

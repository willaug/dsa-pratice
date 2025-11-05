# 🚦 Two Pointers

The two pointers technique involves using two indices to traverse an array or a string, often from opposite ends or at different speeds. This approach is particularly useful for problems involving sorted arrays, searching for pairs, or removing duplicates.

### 📌 Characteristics of Two Pointers
1. **Efficiency**: Reduces the time complexity from O(n^2) to O(n) in many cases.
2. **Space Complexity**: Often uses O(1) extra space, making it memory efficient.
3. **Sorted Data**: Works best with sorted arrays or linked lists.
4. **Pair Finding**: Ideal for problems that require finding pairs or triplets in a dataset.

### 💚 Best choice
- Use queues when you need to process elements in the order they arrive.
- Consider the trade-offs between memory usage and access speed when choosing between stacks and queues.
- Use the two pointers technique when dealing with sorted arrays or when you need to find pairs in a dataset.
- Be mindful of edge cases, such as empty arrays or arrays with only one element.

### 💛 In JavaScript
- The two pointers technique can be implemented using simple loops and index variables.

```js
// O(n) time, O(1) extra space
function twoSumSorted(nums, target) {
  let i = 0, j = nums.length - 1;
  while (i < j) {
    const sum = nums[i] + nums[j];
    if (sum === target) return [i, j];
    if (sum < target) i++;       // need bigger sum → move left pointer right
    else j--;                    // sum too big → move right pointer left
  }
  return [-1, -1];
}

// Example:
console.log(twoSumSorted([1,2,4,6,10], 8)); // [1,3] → 2 + 60

// reverse a string using two pointers
function reverseString(s) {
  let left = 0;
  let right = s.length - 1;
  while (left < right) {
    [s[left], s[right]] = [s[right], s[left]];
    left++;
    right--;
  }
  return s;
}

// Example:
console.log(reverseString(['h','e','l','l','o'])); // ['o','l','l','e','h']
```

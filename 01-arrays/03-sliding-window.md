# 🪟 Sliding Window

The sliding window technique uses **two indices**—`start` and `end`—to track a **current interval** over an array or string. You **expand** the window with `end`; if a rule is violated, you **shrink** it from `start` until it’s valid again. Most problems solve in **O(n)** time with **O(1)** or **O(k)** extra space.

### 📌 Characteristics of Sliding Window

1. **Efficiency**: Single pass (or near it), typically **O(n)**.
2. **Local State**: Maintain counts/sum/frequency for the active window.
3. **Rule-Driven**: Grow until you **break** a constraint; then shrink to **restore** it.
4. **Versatility**: Great for “**longest/shortest subarray/substring that satisfies X**.”

### 💚 Best choice

* Use when the task asks for **max/min length** or **count** of subarrays/substrings under a constraint.
* With **positive integers**, windows for `sum ≤ K` are straightforward.
* For **strings**, a `Map` for character frequencies is your go-to.
* Watch edge cases: empty input, `k = 0`, duplicates, Unicode/UTF-16 pitfalls.

### 💛 In JavaScript

* Implement with a loop for `end`, a `while` to adjust `start`, and a small state (sum or `Map`).

```js
// Longest substring without repeating characters
// Time: O(n) | Space: O(min(n, alphabet))
function lengthOfLongestUnique(s) {
  const freq = new Map();
  let start = 0, best = 0;

  for (let end = 0; end < s.length; end++) {
    const c = s[end];
    freq.set(c, (freq.get(c) || 0) + 1);

    // Rule: no char count > 1
    while (freq.get(c) > 1) {
      const d = s[start++];
      freq.set(d, freq.get(d) - 1);
    }
    best = Math.max(best, end - start + 1);
  }
  return best;
}

// Example:
// console.log(lengthOfLongestUnique("abcabcbb")); // 3 ("abc")
```

```js
// Max sum of a subarray with FIXED size k
// Time: O(n) | Space: O(1)
function maxSumFixed(nums, k) {
  if (k <= 0 || k > nums.length) return 0;
  let sum = 0;

  // first window
  for (let i = 0; i < k; i++) sum += nums[i];
  let best = sum;

  // slide one step at a time
  for (let end = k; end < nums.length; end++) {
    sum += nums[end];          // add right
    sum -= nums[end - k];      // remove left
    if (sum > best) best = sum;
  }
  return best;
}

// Example:
// console.log(maxSumFixed([2, 1, 5, 1, 3, 2], 3)); // 9 (5+1+3)
```

```js
// Longest substring with at most K distinct characters
// Time: O(n) | Space: O(k)
function longestAtMostKDistinct(s, k) {
  const freq = new Map();
  let start = 0, distinct = 0, best = 0;

  for (let end = 0; end < s.length; end++) {
    const c = s[end];
    freq.set(c, (freq.get(c) || 0) + 1);
    if (freq.get(c) === 1) distinct++;

    // shrink until valid: distinct <= k
    while (distinct > k) {
      const d = s[start++];
      freq.set(d, freq.get(d) - 1);
      if (freq.get(d) === 0) distinct--;
    }
    best = Math.max(best, end - start + 1);
  }
  return best;
}

// Example:
// console.log(longestAtMostKDistinct("eceba", 2)); // 3 ("ece")
```

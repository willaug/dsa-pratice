[README > Data Structure > Big O Notation](../README.md)

## ⭕ Big O Notation

Big O is a mathematical notation used to describe the performance or complexity of an algorithm. Specifically, it characterizes algorithms in terms of **time complexity** and **space complexity**.

- **time complexity**: runtime of an algorithm increases with size of the input.
- **space complexity**: memory consumption of an algorithm increases with size of the input.

### 📰 Classification of Algorithms
- **O(1)**: Constant time complexity. The runtime does not change with the size of the input.
- **O(n)**: Linear time complexity. The runtime increases linearly with the size of the input.
- **O(n^2)**: Quadratic time complexity. The runtime is proportional to the square of the input size.
- **O(log n)**: Logarithmic time complexity. The runtime increases logarithmically as the input size increases.
- **O(n log n)**: Linearithmic time complexity. Common in efficient sorting algorithms.

---

 **Constant => O(1)**
- The algorithm takes a constant amount of time to complete, regardless of the size of the input data set.
- Example: Accessing a specific element in an array by its index.

```js
const arr = [1, 2, 3, 4, 5];
const element = arr[2];
```

**Linear => O(n)**
- The algorithm's runtime increases linearly with the size of the input data set.
- Example: Finding a specific element in an unsorted array.

```js
const arr = [1, 2, 3, 4, 5];
const element = 3;
const index = arr.indexOf(element);
```

**Quadratic => O(n^2)**
- The algorithm's runtime is proportional to the square of the size of the input data set.
- Example: A nested loop that iterates over the input data set.

```js
const arr = [1, 2, 3, 4, 5];
for (let i = 0; i < arr.length; i++) {
  for (let j = 0; j < arr.length; j++) {
    console.log(arr[i], arr[j]);
  }
}
```

**Logarithmic => O(log n)**
- The algorithm's runtime increases logarithmically as the input size increases.
- Example: Binary search in a sorted array.

```js
const arr = [1, 2, 3, 4, 5];
const target = 3;
let left = 0;
let right = arr.length - 1;
while (left <= right) {
  const mid = Math.floor((left + right) / 2);
  if (arr[mid] === target) {
    console.log(`Found ${target} at index ${mid}`);
    break;
  } else if (arr[mid] < target) {
    left = mid + 1;
  } else {
    right = mid - 1;
  }
}
```

**Linearithmic => O(n log n)**
- The algorithm's runtime increases in proportion to n log n as the input size increases.
- Example: Efficient sorting algorithms like mergesort and heapsort.

```js
function mergeSort(arr) {
  if (arr.length <= 1) return arr;
  const mid = Math.floor(arr.length / 2);
  const left = mergeSort(arr.slice(0, mid));
  const right = mergeSort(arr.slice(mid));
  return merge(left, right);
}

function merge(left, right) {
  const merged = [];
  let i = 0;
  let j = 0;
  while (i < left.length && j < right.length) {
    if (left[i] < right[j]) {
      merged.push(left[i]);
      i++;
    } else {
      merged.push(right[j]);
      j++;
    }
  }
  return merged.concat(left.slice(i)).concat(right.slice(j));
}
```

---

**Resources**
- [What is Big O Notation Explained: Space and Time Complexity](https://www.freecodecamp.org/news/big-o-notation-why-it-matters-and-why-it-doesnt-1674cfa8a23c/)
- [O que é Big O Notation](https://medium.com/linkapi-solutions/o-que-%C3%A9-big-o-notation-32f171e4a045)


<br>
<br>


---

by @willaug ❤️

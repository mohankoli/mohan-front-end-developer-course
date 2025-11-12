# 🧩 Merge Two Sorted Arrays into One Sorted Array

---

### ✅ Method 1: Without Using `sort()` (Two Pointer Technique)

```js
const a = [1, 3, 5, 7];
const b = [2, 4, 6, 8];

function mergeSortedArrays(arr1, arr2) {
  let res = [], i = 0, j = 0;

  while (i < arr1.length || j < arr2.length) {
    if (j >= arr2.length || arr1[i] < arr2[j]) {
      res.push(arr1[i]);
      i++;
    } else {
      res.push(arr2[j]);
      j++;
    }
  }

  return res;
}

console.log(mergeSortedArrays(a, b));


const a = [1, 3, 5, 7];
const b = [2, 4, 6, 8];

function mergeSortedArrays(arr1, arr2) {
  return arr1.concat(arr2).sort((x, y) => x - y);
}

console.log(mergeSortedArrays(a, b));
// Output: [1, 2, 3, 4, 5, 6, 7, 8]

// Output: [1, 2, 3, 4, 5, 6, 7, 8]

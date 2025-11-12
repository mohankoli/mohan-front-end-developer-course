# 🧩 Remove Duplicates from Array (Preserve Order)

### ✅ Using `Set` (Short & Clean)
```js
let input = [1, 2, 3, 2, 4, 5, 1, 5, 7];

let removeDuplicate = (arr) => {
  return [...new Set(arr)];
};

console.log(removeDuplicate(input));
// Output: [1, 2, 3, 4, 5, 7]

let input = [1, 2, 3, 2, 4, 5, 1, 5, 7];

let removeDuplicate = (arr) => {
  let res = [];
  for (let i = 0; i <= arr.length - 1; i++) {
    if (!res.includes(arr[i])) {
      res.push(arr[i]);
    }
  }
  return res;
};

console.log(removeDuplicate(input));
// Output: [1, 2, 3, 4, 5, 7]

# Binary Search in JavaScript

Binary Search is an efficient algorithm used to find an element in a **sorted array**.

---

## 🔹 How Binary Search Works
1. Start with two pointers: `left` and `right`
2. Find the middle element
3. Compare the middle element with the target
4. Eliminate half of the array based on comparison
5. Repeat until found or search space becomes empty

---

## ✅ Correct JavaScript Implementation

```js
let binarySearch = (arr, target) => {
    let left = 0;
    let right = arr.length - 1;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        if (arr[mid] === target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;

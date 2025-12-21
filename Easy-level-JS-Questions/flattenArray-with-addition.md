# Flatten Nested Array and Calculate Sum (JavaScript)

## Problem
Flatten a nested array and calculate the total sum of all numbers.

---

## Input
```js
let sampleData = [1, 2, [3, 4, [5]], 6, 7, [8]];
let flatten = (arr) => {
    let res = [];
    arr.forEach((item) => {
        if (Array.isArray(item)) {
            res.push(...flatten(item));
        } else {
            res.push(item);
        }
    });
    return res;
};

let total = () => {
    let arr = flatten(sampleData);
    let count = arr.reduce((total, item) => total + item, 0);
    return count;
};

console.log(total()); // 36



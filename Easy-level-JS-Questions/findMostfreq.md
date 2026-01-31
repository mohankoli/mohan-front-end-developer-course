# 38. Find the Most Frequent Element in an Array (Mode)  
**[Coding] [Easy] [JavaScript]**

## Problem
Given an array, find the **most frequent element** (also known as the **mode**).

---

## Program

```js
const arr = [1, 3, 2, 1, 4, 1, 3, 3, 3];

let findMostfreq = (arr) => {
  let freq = {};
  let max = 0;
  let output;

  for (let i = 0; i < arr.length; i++) {
    let val = arr[i];
    freq[val] = (freq[val] || 0) + 1;

    if (freq[val] > max) {
      max = freq[val];
      output = val;
    }
  }

  return output;
};

console.log(findMostfreq(arr)); // 3

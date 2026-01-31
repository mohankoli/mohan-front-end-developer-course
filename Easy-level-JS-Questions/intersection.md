# Intersection of Two Arrays (Unique Values)

## Problem
Find the **intersection** of two arrays such that:
- Only **common elements** are returned
- **Duplicates are not allowed**
- Use `indexOf`

---

## Solution (Using `indexOf`)

```js
let intersection = (arr1, arr2) => {
    let result = [];

    for (let i = 0; i < arr1.length; i++) {
        if (
            arr2.indexOf(arr1[i]) !== -1 &&   // exists in arr2
            result.indexOf(arr1[i]) === -1   // not already in result
        ) {
            result.push(arr1[i]);
        }
    }

    return result;
};


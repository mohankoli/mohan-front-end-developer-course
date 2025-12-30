
---

## Approach Using `indexOf` (Simple)

1. Loop from `0` to `n`
2. Use `indexOf` to check if the number is present
3. If not present, return that number

---

## JavaScript Code

```js
function findMissing(nums) {
    for (let i = 0; i <= nums.length; i++) {
        if (nums.indexOf(i) === -1) {
            return i;
        }
    }
}

// Example
console.log(findMissing([3, 0, 1])); // Output: 2

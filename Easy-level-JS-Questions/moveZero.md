# Move Zeroes to End (JavaScript)

## Problem Statement
Given an array of integers, move all `0`s to the end of the array while maintaining the relative order of the non-zero elements.

---

## Version 1: Using Extra Space (Simple & Readable)

### Approach
- Traverse the array
- Push non-zero elements into a new array
- Count the number of zeroes
- Append zeroes at the end

### Code
```js
function moveZeroes(arr) {
    let output = [];
    let countZero = 0;

    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== 0) {
            output.push(arr[i]);
        } else {
            countZero++;
        }
    }

    for (let j = 0; j < countZero; j++) {
        output.push(0);
    }

    return output;
}

// Example
console.log(moveZeroes([0,1,0,3,12]));
// Output: [1,3,12,0,0]

function moveZeroes(nums) {
    let index = 0;

    for (let i = 0; i < nums.length; i++) {
        if (nums[i] !== 0) {
            nums[index++] = nums[i];
        }
    }

    while (index < nums.length) {
        nums[index++] = 0;
    }

    return nums;
}

// Example
console.log(moveZeroes([0,1,0,3,12]));
// Output: [1,3,12,0,0]


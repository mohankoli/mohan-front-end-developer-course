# Two Sum Problem in JavaScript

[Watch explanation on YouTube](https://www.youtube.com/watch?v=vWNYCIj5Dm0)

```javascript
// Fixed Two Sum Implementation
let nums = [2, 7, 11, 15]; 
let target = 13;

let twoSum = (nums, target) => {
    let mp = new Map();
    for (let i = 0; i < nums.length; i++) {
        let rem = target - nums[i];
        if (mp.has(rem)) {
            return [mp.get(rem), i]; // corrected get method
        } else {
            mp.set(nums[i], i);
        }
    }
    return []; // if no pair found
}

console.log(twoSum(nums, target)); // Output: [0, 2] because 2 + 11 = 13


function twoSum(nums, target) {
  for (let i = 0; i < nums.length; i++) {
    const j = nums.indexOf(target - nums[i],i+1);
    if (j !== -1) return [i, j];
  }
}

console.log(twoSum([1,2,3,4,5,0,6,20], 26));

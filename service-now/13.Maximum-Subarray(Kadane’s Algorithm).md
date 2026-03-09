# Maximum Subarray (Kadane’s Algorithm)

## Problem
Given an integer array `nums`, find the **contiguous subarray** with the largest sum and return that sum.

---

## Example

Input

```
[-2,1,-3,4,-1,2,1,-5,4]
```

Output

```
6
```

Explanation

```
Subarray: [4,-1,2,1]
Sum = 4 + (-1) + 2 + 1 = 6
```

---

# Optimized Approach (Kadane’s Algorithm)

Instead of checking all subarrays (O(n²)), we track a **running sum**.

Idea:

```
1. Keep adding numbers to currentSum.
2. If currentSum becomes negative, reset it.
3. Track the maximum sum seen so far.
```

---

# JavaScript Solution

```javascript
function maxSubArray(nums){

    let sum = 0
    let max = -Infinity

    for(let num of nums){

        sum += num
        max = Math.max(max, sum)

        if(sum < 0){
            sum = 0
        }

    }

    return max
}

console.log(maxSubArray([-2,1,-3,4,-1,2,1,-5,4]))
```

---

# How It Works

Example

```
[4,-1,2,1]
```

Steps

```
4 → sum = 4
4 + (-1) = 3
3 + 2 = 5
5 + 1 = 6
```

Maximum sum

```
6
```

---

# Time Complexity

```
O(n)
```

The array is traversed once.

---

# Space Complexity

```
O(1)
```

No extra memory used.

---

# Key Idea

```
If running sum becomes negative → restart subarray
```

This ensures we always keep the **best possible sum**.

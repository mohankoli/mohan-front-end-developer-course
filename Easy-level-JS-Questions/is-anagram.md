# Sliding Window Technique

## What is Sliding Window?

Sliding Window is a technique used to **reduce nested loops into a single loop** when working with **subarrays or substrings**.

Instead of recalculating values repeatedly, we **expand and shrink a window** over the array/string.

---

# When to Use Sliding Window

Use sliding window when the problem involves:

- Subarrays
- Substrings
- Contiguous elements
- Maximum / minimum length
- Fixed size window
- Dynamic size window

---

# Types of Sliding Window

## 1️⃣ Fixed Window Size

Window size is constant.

Example problem:

```
Find maximum sum of subarray of size k
```

Example:

```
arr = [2,1,5,1,3,2]
k = 3
```

### Solution

```javascript
function maxSumSubarray(arr,k){

    let windowSum = 0
    let maxSum = 0

    for(let i=0;i<k;i++){
        windowSum += arr[i]
    }

    maxSum = windowSum

    for(let i=k;i<arr.length;i++){

        windowSum += arr[i]
        windowSum -= arr[i-k]

        maxSum = Math.max(maxSum,windowSum)
    }

    return maxSum
}

console.log(maxSumSubarray([2,1,5,1,3,2],3))
```

Output

```
9
```

---

## 2️⃣ Dynamic Window Size

Window expands and shrinks depending on condition.

Example problem:

```
Longest substring without repeating characters
```

Example:

```
s = "abcabcbb"
```

Output

```
3
```

### Solution

```javascript
function longestSubstring(s){

    let set = new Set()
    let left = 0
    let maxLength = 0

    for(let right = 0; right < s.length; right++){

        while(set.has(s[right])){
            set.delete(s[left])
            left++
        }

        set.add(s[right])

        maxLength = Math.max(maxLength, right-left+1)
    }

    return maxLength
}

console.log(longestSubstring("abcabcbb"))
```

---

# Sliding Window Pattern

General template:

```javascript
let left = 0

for(let right = 0; right < arr.length; right++){

    // expand window

    while(condition not satisfied){
        // shrink window
        left++
    }

    // update result
}
```

---

# Time Complexity

```
O(N)
```

Because each element is processed at most **twice**.

---

# Common Sliding Window Problems

1. Longest Substring Without Repeating Characters
2. Maximum Sum Subarray of Size K
3. Minimum Window Substring
4. Longest Repeating Character Replacement
5. Permutation in String

---

# Key Idea

```
Expand → Check condition → Shrink → Update result
```

---

# Interview Explanation

You can say:

```
Sliding window avoids recomputing subarrays repeatedly.
Instead of nested loops, we move a window across the array
and adjust its size dynamically.
```

---

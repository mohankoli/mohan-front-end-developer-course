# Maximum Subarray (Kadane’s Algorithm)

---

## 🧠 Problem

Given an integer array `nums`, find the **contiguous subarray** with the largest sum and return its sum.

---

## 🚀 Approach (Kadane’s Algorithm)

### 💡 Key Idea

* Maintain a running sum (`total`)
* If the sum becomes negative → reset it to `0`
* Track the maximum sum seen so far

---

## ✅ Python Code

```python id="k3d9x2"
def maxSubArray(nums):
    n = len(nums)
    maxi = float("-inf")
    total = 0

    for i in range(n):
        total = total + nums[i]
        maxi = max(maxi, total)

        if total < 0:
            total = 0

    return maxi
```

---

## 🔍 Example

```python id="b92xka"
nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
print(maxSubArray(nums))  # Output: 6
```

**Explanation:**

* Subarray: `[4, -1, 2, 1]`
* Sum = **6**

---

## ⏱ Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)

---

## 🎯 Interview Tips

* Say:

  > “I’ll use Kadane’s Algorithm for O(n) time.”
* Key trick:

  > Reset sum when it becomes negative

---

## ⚠️ Important Clarification

This solution does **NOT** solve:

❌ Subarray Sum Equals K
✔ Only solves Maximum Subarray

---

## 🏁 Summary

* Efficient O(n) solution
* Widely asked in interviews
* Important to distinguish from prefix sum problems

---

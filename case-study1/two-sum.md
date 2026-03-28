# Two Sum Problem (Hashmap Approach)

## 🧩 Problem

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to the target.

---

## ✅ Solution (Python)

```python
def two_sum(nums, target):
    hashmap = {}
    n = len(nums)

    for i in range(0, n):
        remaining = target - nums[i]

        if remaining in hashmap:
            return [hashmap[remaining], i]

        hashmap[nums[i]] = i

    return None


nums = [4, 8, 12, 8, 5, 10]
target = 15

print(two_sum(nums, target))
```

---

## 🧠 Explanation

* Use a hashmap to store numbers and their indices.
* For each element:

  * Calculate `remaining = target - current number`
  * Check if `remaining` exists in hashmap
  * If yes → return indices
  * Otherwise → store current number in hashmap

---

## 📌 Example

**Input:**

```
nums = [4, 8, 12, 8, 5, 10]
target = 15
```

**Output:**

```
[4, 5]
```

**Explanation:**

```
nums[4] + nums[5] = 5 + 10 = 15
```

---

## ⚡ Complexity

* Time Complexity: **O(n)**
* Space Complexity: **O(n)**

---

## 🔥 Optimized Version

```python
def two_sum(nums, target):
    hashmap = {}

    for i, num in enumerate(nums):
        remaining = target - num

        if remaining in hashmap:
            return [hashmap[remaining], i]

        hashmap[num] = i

    return None
```

---

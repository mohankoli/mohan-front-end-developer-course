# Longest Consecutive Sequence (Optimal Solution)

## 🧠 Problem

Given an unsorted array of integers `nums`, return the length of the longest consecutive elements sequence.

* Must run in **O(n)** time.

---

## 🚀 Approach (Using Set)

### 💡 Key Idea

* Use a **set** for O(1) lookup.
* Only start counting when the number is the **start of a sequence**:

  * `num - 1` is NOT present in the set.
* Expand the sequence using a `while` loop.

---

## ✅ Python Code

```python
def longestConsecutive(nums):
    num_set = set(nums)
    longest = 0

    for num in num_set:
        if num - 1 not in num_set:  # start of sequence
            current = num
            count = 1

            while current + 1 in num_set:
                current += 1
                count += 1

            longest = max(longest, count)

    return longest
```

---

## 🔍 Example

```python
nums = [100, 4, 200, 1, 3, 2]
print(longestConsecutive(nums))  # Output: 4
```

**Explanation:**

* Longest sequence is `[1, 2, 3, 4]`
* Length = **4**

---

## ⏱ Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(n)

---

## 🎯 Interview Tips

* Always mention:

  > “Using a set for O(1) lookup.”
* Key optimization:

  > Only start from numbers where `num - 1` is not present.
* Avoid duplicate work by iterating over the set.

---

## ⚠️ Common Mistake

❌ Iterating over the original list instead of the set:

```python
for num in nums:  # Not optimal
```

✔ Correct:

```python
for num in num_set:
```

---

## 🏁 Summary

* Optimal solution using **HashSet**
* Avoids redundant computation
* Industry-standard approach for interviews (FAANG/Karat)

---
